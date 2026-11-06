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
- Game state is a string state machine: `playing` | `dead` | `gameover` (see `update()`); level completion is triggered when no non-`ShootingStar` asteroid remains.
- Frame delta is capped at `0.05s` in `loop()`; keep physics in units per second (`dt`-based), not per frame.
- UI text is in Spanish (`NIVEL`, `PUNTAJE`, etc.); identifiers and comments follow the repo convention: English code, Spanish comments when they add value.

## Special entities

- Power-ups share the `PowerUp` base class (with `apply(ship)`) and spawn on a timer; only one is active at a time, picked from `POWER_UP_TYPES`. `SpeedPowerUp` grants `ship.speedBoost` for 5s (doubles thrust only, not current velocity). `ShieldPowerUp` grants `ship.shield` for 6s. `TripleShotPowerUp` grants `ship.tripleShot` for 5s, making `tryShoot()` fire three parallel bullets.
- `ship.shield` only blocks `EnemyBullet` impacts; asteroids still destroy the ship. The shield ring is drawn in `Ship.drawShield()`.
- `Enemy` is an OVNI that drifts, wraps around the world, and fires `EnemyBullet`s aimed at the ship via the shortest toroidal path.
- `SHIP_SKINS` + `skinIndex` define the ship appearances; `C` cycles them and `traceHull()` draws the active hull.
- `ShootingStar` extends `Asteroid` with a short `ttl`. It lives in the same `asteroids` array, but level completion ignores it, so it never blocks `nextLevel()`.
