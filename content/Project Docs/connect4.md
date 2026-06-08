# 🎮 Connect 4 AI

## Overview

Connect 4 AI is a web-based implementation of the classic Connect 4 game with an AI opponent powered by the minimax algorithm. The player competes against the AI through a browser interface, with the AI evaluating every possible move to play optimally.

## How It Works

The minimax algorithm builds a decision tree of all possible game states from the current board position. At each level of the tree, it alternates between maximizing the AI score and minimizing the player score, simulating both players playing optimally. Alpha-beta pruning is applied to cut off branches that cannot affect the final decision, significantly reducing computation time.

The web interface is built in HTML, CSS, and JavaScript, with the game logic and AI running in Python on the backend.

## Skills Applied

- Algorithm design and implementation
- Recursive tree search
- Game theory fundamentals
- Web interface development
- Python backend logic

The algorithm thinking developed here, particularly around state evaluation and decision trees, is conceptually related to the intent-routing logic in [[Project Docs/hermes-assistant|Hermes]], where the system evaluates possible actions given a natural language input and selects the best one.

## Technical Specifications

**Software and Tools:**
- Python (minimax algorithm and backend)
- HTML, CSS, JavaScript (web interface)
- Alpha-beta pruning optimization

**Skills Applied:**
- Algorithm design
- Game state representation
- Web development
- Recursive programming

## Related Projects

- [[Project Docs/python-automations|Python Automations]], shared Python scripting foundation
- [[Project Docs/hermes-assistant|Hermes Assistant]], decision-making logic shares conceptual roots with minimax evaluation
