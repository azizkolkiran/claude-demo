# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Running the Games

No build tools or dependencies. Open any HTML file directly in a browser:

```
open memory-game.html
open pacman.html
```

## Architecture

Two standalone single-file games — each file contains all HTML, CSS, and JavaScript inline. No frameworks, no external assets, no module system.

**memory-game.html** — Hafıza Kartı (Memory Card Game)
- 4x4 grid, 8 emoji pairs, Fisher-Yates shuffle
- CSS 3D card flip via `rotateY(180deg)` + `backface-visibility: hidden`
- Global state: `flipped[]`, `matched`, `moves`, `locked` (blocks clicks during animation), `started`
- Match/mismatch feedback via `pulse` / `shake` CSS keyframe animations
- Timer starts on first card click

**pacman.html** — Pac-Man
- Canvas 2D rendering, `requestAnimationFrame` game loop
- Tile-based 21×21 maze encoded as a 2D binary array (1=wall, 0=path)
- Timestamp throttling: Pac-Man moves every 175ms, ghosts every 430ms
- Ghost AI: BFS pathfinding to Pac-Man with 22% random move chance to avoid determinism
- Three game states: `'playing'` / `'win'` / `'dead'`

## Language

All UI text is Turkish (Türkçe). Keep labels, messages, and button text in Turkish when modifying existing games.

## Repository Notes

- `test.txt` and `README.md` are stubs with no functional content.
- `.gitignore` excludes `.claude/` (Claude Code internal files).
