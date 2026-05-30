# 🛠️ The Setup Journey — Engineering Documentation with Claude MCP & Obsidian

## 🎯 Overview

This document covers how this engineering notebook was built — specifically how I connected **Claude AI** to my **Obsidian vault** using the **Model Context Protocol (MCP)**, enabling Claude to read and write files in my vault directly from the Claude Desktop app. The goal was to use Claude as an intelligent documentation assistant that could edit project files, rename documents, push to GitHub, and help me maintain my engineering portfolio hands-free.

---

## 🧱 System Architecture

The final working setup consists of three components working together:

| Component | Role |
| :--- | :--- |
| **Obsidian** | Local vault storing all markdown documentation |
| **Obsidian Local REST API plugin** | Exposes the vault over a local HTTP/HTTPS server on port `27124` |
| **Claude Desktop + MCP** | Connects to the REST API via `mcp-remote`, allowing Claude to call vault tools |

Claude communicates with Obsidian through the MCP (Model Context Protocol) layer, using `mcp-remote` as a bridge between Claude Desktop's STDIO interface and Obsidian's local REST API.

---

## ⚙️ Configuration

The Claude Desktop MCP config (`claude_desktop_config.json`) was set up to launch `mcp-remote` via `npx`, pointed at the Obsidian REST API endpoint with a Bearer token for authentication:

```json
{
  "mcpServers": {
    "obsidian": {
      "command": "C:\\Users\\Shreyas-PC\\AppData\\Roaming\\npm\\npx.cmd",
      "args": [
        "mcp-remote@latest",
        "https://127.0.0.1:27124/mcp/",
        "--header",
        "Authorization: Bearer <token>"
      ]
    }
  }
}
```

---

## 🐛 Troubleshooting — Issues Encountered During Setup

Getting this working was not straightforward. Several distinct errors had to be debugged in sequence.

### Issue 1: Wrong `npx` Path — "not recognized as an internal or external command"

The first attempt used the system-wide Node.js path (`C:\Program Files\nodejs\npx.cmd`). Because the path contains a space, Windows cmd failed to parse it correctly and threw:

```
'C:\Program' is not recognized as an internal or external command
```

**Fix:** Switched to the npm user directory path, which has no spaces:
```
C:\Users\Shreyas-PC\AppData\Roaming\npm\npx.cmd
```

---

### Issue 2: Self-Signed Certificate Error (`DEPTH_ZERO_SELF_SIGNED_CERT`)

Once the correct `npx` path was used, the next error was a TLS failure. The Obsidian Local REST API uses a self-signed certificate for its HTTPS server, and Node.js rejected it by default:

```
Error: self-signed certificate; if the root CA is installed locally,
try running Node.js with --use-system-ca
  code: 'DEPTH_ZERO_SELF_SIGNED_CERT'
```

Several flags were attempted to work around this — `--allow-http`, `--ignore-ssl` — but none resolved it at the `mcp-remote` level. The fix that ultimately worked was setting the `NODE_TLS_REJECT_UNAUTHORIZED=0` environment variable, which disables TLS verification entirely. While this produces a security warning, it is acceptable for a localhost-only connection.

---

### Issue 3: HTTP vs HTTPS — "other side closed" (`UND_ERR_SOCKET`)

Switching to plain `http://` instead of `https://` caused a different error — the connection was immediately dropped:

```
SocketError: other side closed
  code: 'UND_ERR_SOCKET'
```

This happened because the Obsidian REST API plugin only serves over HTTPS by default, even locally. Attempting to connect over plain HTTP resulted in the server immediately closing the socket. The endpoint had to remain `https://`.

---

### Issue 4: Session Drops and "Session not found" (404)

Even after a successful connection was established, subsequent tool calls would fail with:

```
StreamableHTTPError: Streamable HTTP error: Error POSTing to endpoint:
  {"error": "Session not found"}
  code: 404
```

This occurred because the SSE (Server-Sent Events) stream that `mcp-remote` uses to maintain the session would disconnect — often due to Obsidian briefly going idle or the REST API plugin resetting its session state. When Claude then tried to make a follow-up tool call, the session ID was no longer valid.

The SSE disconnection error looked like:
```
Error: SSE stream disconnected: TypeError: terminated
```

**Workaround:** Reloading the Claude Desktop MCP connection (restarting the server in settings) re-established a fresh session. The connection is stable as long as Obsidian remains active and the REST API plugin stays running.

---

### Issue 5: Race Condition on Startup — Duplicate Process Assertion Failure

During one restart cycle, two `mcp-remote` processes were spawned simultaneously. One would connect and immediately shut down, triggering a low-level Windows assertion failure:

```
Assertion failed: !(handle->flags & UV_HANDLE_CLOSING),
file src\win\async.c, line 76
```

This was a Windows-specific Node.js race condition caused by rapid MCP server restarts in Claude Desktop. It resolved itself after a clean restart with only one server instance running.

---

## ✅ What's Working Now

Once the correct configuration was in place, the full workflow became:

1. **Claude reads vault files** — searching, reading markdown content, navigating the file tree
2. **Claude writes and edits files** — rewriting project docs, renaming files, updating frontmatter
3. **Claude pushes to GitHub** — via Desktop Commander MCP running terminal commands in the quartz repo
4. **Persistent documentation** — changes made through Claude survive session restarts and are tracked in git

This setup effectively makes Claude a hands-free documentation assistant for the entire engineering notebook. Voice or text instructions in Claude Desktop translate directly into vault edits and GitHub commits.

---

## 🔧 Technical Specifications

**Tools & Technologies:**
- Obsidian (local markdown vault)
- Obsidian Local REST API plugin (community plugin)
- Claude Desktop (MCP client)
- `mcp-remote` via `npx` (MCP bridge)
- Desktop Commander MCP (terminal access for git operations)
- Git / GitHub (version control and publishing via Quartz)

**Key Config Details:**
- MCP endpoint: `https://127.0.0.1:27124/mcp/`
- Auth: Bearer token from Obsidian REST API plugin settings
- TLS: Self-signed cert accepted via `NODE_TLS_REJECT_UNAUTHORIZED=0`
- npx path: `C:\Users\Shreyas-PC\AppData\Roaming\npm\npx.cmd`
