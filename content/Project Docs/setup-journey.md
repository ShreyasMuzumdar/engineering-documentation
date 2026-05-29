---
title: The Setup Journey
---

# 🚀 Setting Up the Engineering Notebook

This page documents the evolution of my digital documentation system, from a collection of static files to a fully functional, web-published engineering notebook.

## The Goal
The objective was to create a centralized, searchable, and professional-looking repository for all my engineering work that could be easily updated and shared.

## The Evolution

### 1. The Obsidian Foundation
I started by utilizing **Obsidian** to manage my notes. The local-first, markdown-based approach allowed me to link ideas and build a "second brain" for my technical research. I organized my vault into dedicated sections for Robot Docs and Project Docs to keep the structure scalable.

### 2. The Transition to Markdown
A significant challenge was converting existing documentation—some of which existed as HTML files—into clean Markdown. This required a process of:
- Stripping out HTML boilerplate.
- Normalizing indentation.
- Converting web-based formatting into standard markdown syntax to ensure compatibility across different viewers.

### 3. Web Publishing with Quartz
To make the notebook public, I implemented **Quartz**, a framework that transforms Obsidian vaults into fast, searchable websites. This involved:
- Configuring the `v5` branch for stable deployment.
- Setting up a GitHub repository to act as the source of truth.
- Managing the sync process between my local machine and the remote server.

### 4. Refinement and Version Control
The process wasn't without hurdles. I encountered several "sync anomalies" where files were unexpectedly deleted or incorrectly formatted during the push process. This reinforced the importance of:
- Using standard `git` commands (`add`, `commit`, `push`) for critical updates.
- Maintaining a strict branch strategy to separate experimental changes from the live site.

## Current Stack
- **Knowledge Base:** Obsidian
- **Publishing:** Quartz
- **Version Control:** Git / GitHub
- **Hosting:** GitHub Pages/Vercel
