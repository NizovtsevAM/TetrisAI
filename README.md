# Tetris — Demo/Player

A single‑file HTML Tetris implementation with a step‑by‑step AI demo, player mode, dark/light themes, and configurable demo speed.

## How to Play

### Option 1: Via GitHub Pages (recommended)
The game is available online at: [https://nizovtsevam.github.io/TetrisAI/](https://nizovtsevam.github.io/TetrisAI/)

### Option 2: Locally
To start the game locally, open the `index.html` file in any modern browser:

- **Direct link**: [index.html](index.html)

You can also:
- Double-click the `index.html` file in your file explorer
- Drag the file into your browser window
- Use the "Open File" command in your browser's menu

## Features

- **Demo Mode**: Watch an AI play using a simple heuristic (maximize lines, avoid new holes, keep board healthy). The AI shows each move step‑by‑step.
- **Player Mode**: Classic keyboard controls (← → ↑ ↓, Space, P, R).
- **Themes**: Light and dark themes with persistent preference.
- **Demo Speed Slider**: Adjust the AI step interval from 60 ms (fast) to 400 ms (slow).
- **Scoring**: Standard line‑clear scores, T‑Spin bonuses, and Perfect Clear bonuses (including the 3200 special case).
- **Levels**: Up to level 100 with gravity scaling.
- **Preview**: Centered “Next” piece preview.
- **Controls**: Pause (P), Restart (R), and mode toggle.

## Controls

- **Move**: ← / →
- **Rotate**: ↑
- **Soft Drop**: ↓
- **Hard Drop**: Space
- **Pause**: P
- **Restart**: R
- **Mode Toggle**: Click “🤖 Demo” / “🕹️ Player”
- **Theme Toggle**: Click “🌙 Dark” / “☀️ Light”
- **Demo Speed**: Use the slider (60 ms – 400 ms)

## AI Strategy (Demo Mode)

The AI evaluates reachable landing positions using a breadth‑first search and scores them with a weighted heuristic:

- Aggregate height
- Lines cleared
- Holes
- Bumpiness
- Maximum height
- Survival factor for high stacks

It prefers moves that clear the most lines without creating new holes, and falls back to board‑health considerations when lines are equal.

## Scoring Details

- **Line clears**: 0, 100, 300, 500, 800 points for 0–4 lines.
- **T‑Spin**: 100 (no lines), 200 (single), 1200 (double), 1600 (triple).
- **Perfect Clear**: 800–2000 points; 3200 points if the previous clear was a 4‑line clear.

## Levels & Gravity

- Levels advance every 10 lines cleared, up to level 100.
- Gravity interval scales from 1000 ms (level 1) to 100 ms (level 100).

## Theme Persistence

Your theme choice is saved in `localStorage` and restored on reload.

## Demo Speed Persistence

The demo speed slider value is saved in `localStorage` and restored on reload.

## Technical Notes

- Canvas rendering with grid overlay.
- 7‑bag randomizer for piece generation.
- SRS‑like wall kicks for rotations.
- No external dependencies; pure HTML/CSS/JavaScript.