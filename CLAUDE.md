# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Single-file static web app — no build step, no dependencies, no package manager.

## Running

Open `tictactoe.html` directly in a browser:

```powershell
start tictactoe.html
```

## Architecture

Everything lives in `tictactoe.html` as one self-contained file:

- **HTML** — board grid (`#board`), status line, score display, two control buttons
- **CSS** — dark theme, grid layout, per-player colors (X = pink `#ff6b9d`, O = cyan `#00d4ff`), win pulse animation
- **JS** — plain ES6, no libraries
  - `init()` resets board state and re-renders
  - `place(i, player)` is the single write path for both human and CPU moves
  - `checkResult()` tests all 8 win combos after each move
  - `cpuMove()` uses a simple heuristic: win > block > prefer center/corners/edges
  - CPU moves are delayed 350 ms via `setTimeout` for feel
