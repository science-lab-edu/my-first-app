# Repository instructions

## Build, test, and lint

- There is no package manifest, build step, test runner, or linter configured.
- Run the game by opening `index.html` directly in a browser; no dependencies or compilation are required.
- No single-test command is available because this repository does not currently define tests.

## Architecture

- This is a standalone browser game with no framework or module system. Currently, `index.html` contains the page structure, responsive styles, Canvas renderer, input handling, and game logic.
- The game is a side-scrolling platformer. Its JavaScript IIFE owns the player and enemy state, collision/physics updates, camera position, HUD, and start/retry/win flow.
- The world uses a fixed 2800-by-540 coordinate space. `update()` advances simulation state and `draw()` renders the visible camera window to the canvas on each `requestAnimationFrame` tick.
- Platforms and enemy starting positions are level data near the top of the script. The HTML overlay and HUD expose game state and controls; keep their element IDs aligned with the selectors used by the script.

## Repository conventions

- Keep HTML, CSS, and JavaScript in three separate files: `index.html`, `styles.css`, and `game.js`. Preserve the dependency-free browser setup; do not add a bundler or framework without a deliberate project decision.
- Player movement and collisions use world coordinates; rendering applies canvas scaling and camera translation. Keep level geometry, camera bounds, and the goal position consistent with the world dimensions.
- Keyboard and touch controls share the `keys` set. Touch buttons are identified by `data-key` and use pointer events; update the visible instructions and both input paths together when changing controls.
- The visible game copy and README are in Japanese. Preserve Japanese for player-facing text and keep the README's controls and gameplay description consistent with the implementation.
- Display user-facing explanations and instructions in Japanese.
