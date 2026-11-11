# Electromechanical Arcade

A mobile-first, playable collection inspired by mechanical and electromechanical games from before and around the dawn of video arcades. **Version 0.3** features **six games**, in one self-contained, offline-compatible `index.html`.

**[Open the playable collection](index.html)** (when using GitHub Pages, visit the Pages website for this repository).

## The games

| Game | Inspiration | How to play |
| --- | --- | --- |
| **Mini Drive** | Kasco Mini Drive (1959) | Steer a toy car over a moving roadway. Keep it on the road to score. |
| **Ball Walk** | Cointronics Ball Walk (1960s) | Five balls. Spread and close twin hinged rails, using gravity and inertia to coax the ball toward the chime. |
| **Shoot the Moon** | Classic wooden tabletop game (1940s onward) | Five attempts. Roll a steel ball along hinged rails, then drop it in a scoring planet pocket. |
| **Marble Mechanica** | Mechanical button-operated obstacle toys, notably TOMY's Screwball Scramble (1979) | Clear four original stations: spring launcher, teetering bridge, timed stepping pads, and rotary gate. |
| **Tilt Labyrinth** | BRIO's wooden tilt labyrinth (1946) | Roll a ball through an original maze by changing two tilt axes. Avoid holes. |
| **Shoot the Bear** | Seeburg Shoot the Bear (1949) | Aim a moving light-rifle crosshair and fire 20 shots. |

These games are **original playable interpretations** and **not licensed or exact historical reproductions**. We did not reuse original commercial game artwork, sounds, board layouts, source code, or brand trade dress.

## Controls

### Mini Drive
- **Touch:** horizontal steering slider, tap/drag on the road, or hold left/right buttons.
- **Keyboard:** Left/Right arrows or A/D.

### Ball Walk and Shoot the Moon
- **Touch:** press **LIFT BALL** or tap the playfield to start the next ball. Move the **RAIL SPREAD** slider or hold **CLOSE/OPEN**.
- **Keyboard:** Left/Right or A/D to change spread, Space to lift.
- Spread the rails to reshape the slope and accelerate the ball. Narrow the rails before they open too wide beneath the ball. Watch the **BALL SPEED** readout. The ball can roll backward, carry inertia forward, or drop between the rods. There is no hidden “open = automatic progress” scoring shortcut.

### Marble Mechanica
This is deliberately **not** a single joystick game. The two on-screen buttons become the appropriate mechanical controls at each station, with the enlarged active mechanism pictured on the left:

1. **Spring launcher:** Hold `HOLD SPRING` to build pressure; release (or tap `RELEASE`) in the gold power zone.
2. **Teetering bridge:** Hold `LEFT` or `RIGHT` briefly to control a tip-able bridge. Give the marble a gentle slope, but don't overtilt.
3. **Stepping pads:** Tap the alternating `LEFT PAD` and `RIGHT PAD` controls when the timing marker is in the gold window. Complete six jumps.
4. **Rotary gate:** Hold `CRANK` to turn the gate; tap `DROP BALL` when it lines up with the target arrow.

A mistake restarts the current station and costs points, not the whole course. The buttons also respond to **J/K** or **Left/Right** keys. This is an original four-mechanism proof of concept inspired by the feel of manually operating plastic toy mechanisms, not a duplicate of a Screwball Scramble product.

### Tilt Labyrinth
- **Touch:** drag *from anywhere on the playfield* to tilt the board relative to your initial finger position; release to let the tilt level out. Or use the independent X and Y sliders in the control panel.
- **Keyboard:** Arrow keys or WASD.
- Ball motion has acceleration, momentum, damping, and collision with wooden walls. Rolling into one of the dark holes returns you to the beginning; the goal is the brass G cup.

### Shoot the Bear
- Drag to aim; release to fire, or press the FIRE button. Keyboard arrows/WASD to aim and Space to shoot.

All games have **Reset**, sound toggle, fullscreen attempt, and local best scores. Sounds are synthesized with Web Audio. No external assets, accounts, server calls, or downloads are required after you save the HTML.

## Technical approach

- Pure **HTML + CSS + Canvas + JavaScript**, no external libraries or image assets.
- One portable file, designed to fit both portrait and landscape phone screens.
- The *Ball Walk* and *Shoot the Moon* games now share an approximate **rod/ball geometry-and-gravity integrator** with changing ball height, projected gravitational force, rolling inertia, and friction. See [docs/physics.md](docs/physics.md).
- *Tilt Labyrinth* has 2D acceleration/inertia and rounded ball-versus-wall collision resolution. Its maze is independently generated with a fixed seed; holes are placed in dead ends off the guaranteed path.
- *Marble Mechanica* uses four deterministic interactive stations; bridge motion has acceleration and inertia, while other station mechanisms are rule-based minigames.
- No claim of exact restoration of actual electromechanical schematics or original physical forces.

## Run / deploy

1. Download or clone the repository.
2. Open `index.html` in a browser, or serve it with any static server.
3. To publish from GitHub: **Settings → Pages → Deploy from a branch → `main` → `/ (root)`**.

## References and further reading

- [Ball Walk, International Arcade Museum](https://www.arcade-museum.com/Trade-Stim/ball-walk)
- [Shoot the Moon wooden game construction and play, Woodcraft](https://www.woodcraft.com/blogs/small-projects/shoot-the-moon)
- [Peng Xu, *Dynamics and Control of the Shoot-the-Moon Tabletop Game*, Clemson thesis (2011)](https://open.clemson.edu/all_theses/1209/)
- [Stanford CHARM Lab, Shoot the Moon haptic simulation](https://charm.stanford.edu/ME327/Group9)
- [TAKARA TOMY Screwball Scramble news release (2022)](https://www.takaratomy.co.jp/english/product_release/pdf/p220201_en.pdf)
- [BRIO Labyrinth, official manufacturer page](https://www.ravensburger.us/en-US/brio/products/games/labyrinth-game-63400000)

## Roadmap

- Tuning the rail physics with real-world reference footage and measured rail geometry.
- Improve rolling sound and tactile feedback.
- Add more original mechanical obstacle modules and alternate labyrinth layouts.
- Optional touchscreen/gamepad presets and better accessibility options.