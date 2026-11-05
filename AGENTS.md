# AGENTS.md

Static HTML5 canvas game. No build, bundler, package manager, tests, linter, or CI — do not add dependencies or npm scripts unless asked.

## Run

Open `index.html` directly, or serve it locally:

```bash
npx serve .
```

`npx` is only used for serving; the project itself has zero dependencies.

## Layout / wiring

- `index.html` — canvas element, inline CSS, loads `game.js` at end of `<body>`.
- `game.js` — entire game: entities, state machine, update/draw, rAF loop.
- No modules/imports; `game.js` relies on globals and `'use strict'`.

## Things that are easy to get wrong

- Canvas size is hardcoded twice: `width`/`height` in `index.html` and `W`/`H` in `game.js`. Change both together.
- World is toroidal: movement must use `wrap()` from `game.js` so entities reappear on the opposite edge.
- Game state is a string state machine: `playing` | `dead` | `gameover` (see `update()`); level completion is triggered when `asteroids.length === 0`.
- Frame delta is capped at `0.05s` in `loop()`; keep physics in units per second (`dt`-based), not per frame.
- UI text is in Spanish (`NIVEL`, `PUNTAJE`, etc.); identifiers and comments follow the repo convention: English code, Spanish comments when they add value.

## README is partially aspirational

`README.md` claims power-ups and special asteroid types (e.g. "estrella fugaz"), but `game.js` implements none of them. Trust `game.js` over the README for actual behavior.
