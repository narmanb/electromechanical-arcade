# Electromechanical Arcade

A mobile-first, playable collection inspired by mechanical and electromechanical games from before and around the dawn of video arcades. **Version 0.5** features **nine games**, in one self-contained, offline-compatible `index.html`.

**[Open the playable collection](index.html)** (when using GitHub Pages, visit the Pages website for this repository).

## The games

| Game | Inspiration | How to play |
| --- | --- | --- |
| **Mini Drive** | Kasco Mini Drive (1959) | Steer a toy car over a moving roadway. Keep it on the road to score. |
| **Ball Walk** | Cointronics Ball Walk (1960s) | Five balls. Spread and close twin hinged rails, using gravity and inertia to coax the ball toward the chime. |
| **Shoot the Moon** | Classic wooden tabletop game (1940s onward) | Five attempts on a **vertical wooden board**. Roll a steel ball upward and drop it into a planet pocket. |
| **Marble Mechanica** | Mechanical button-operated obstacle toys, notably TOMY's Screwball Scramble (1979) | Clear four original stations: spring launcher, teetering bridge, timed stepping pads, and rotary gate. |
| **Tilt Labyrinth** | BRIO's wooden tilt labyrinth (1946) | Roll a ball through an original maze by changing two tilt axes. Avoid holes. |
| **Shoot the Bear** | Seeburg Shoot the Bear (1949) | Aim a moving light-rifle crosshair and fire 20 shots. |
| **Electric Crane** | International Mutoscope Electric Traveling Crane (c. 1933) and early digger machines | Move a winch and boom, track moving prizes, and time five descending claw grabs. |
| **Ten Strike** | Williams Ten Strike (introduced late 1957; commonly cataloged 1958) | Aim a miniature bowler, wind a spring by holding a button, and release toward ten pins. Five scored frames with strikes/spares. |
| **Relay Switchyard** | Entirely original mechanical-style parcel sorter | Route 12 stamped parcels with three relay levers; sort correctly before the sensor, conserve three fuses, build combos. |

These games are **original playable interpretations** and **not licensed or exact historical reproductions**. We did not reuse original commercial game artwork, sounds, board layouts, source code, or brand trade dress.

## Controls

### Mini Drive
- **Touch:** horizontal steering slider, tap/drag on the road, or hold left/right buttons.
- **Keyboard:** Left/Right arrows or A/D.

### Ball Walk and Shoot the Moon
- **Touch:** press **LIFT BALL** or tap the playfield to start the next ball. Move the **RAIL SPREAD** slider or hold **CLOSE/OPEN**.
- **Keyboard:** Left/Right or A/D to change spread, Space to lift.
- Start with approximately **30–40% spread**. As the ball climbs, narrow the rods to keep the steel ball supported. The gap you can safely hold depends on the ball’s position. The ball can roll backward, accelerate, or fall; **holding a single slider percentage cannot reach the jackpot**. The two games share the historical rod mechanism, but Shoot the Moon has a different vertical presentation and higher-risk scoring cups.

### Marble Mechanica
This is deliberately **not** a single joystick game. The two on-screen buttons become the appropriate mechanical controls at each station, with the enlarged active mechanism pictured on the left:

1. **Spring launcher:** Hold `HOLD SPRING` to build pressure; release (or tap `RELEASE`) in the gold power zone.
2. **Teetering bridge:** **Balance the ball inside the gold center zone for two seconds**. LEFT and RIGHT apply torque to the teetering bridge; the marble itself makes the bridge tip. Falling off or over-tilting restarts the station.
3. **Stepping pads:** Complete six alternating LEFT and RIGHT jumps, each in the gold moving-timing window. **Every wrong press, early/late press, or completed marker sweep costs one of four lives.** Timing windows shrink and marker speed increases after every successful jump. Four lost lives reset the station.
4. **Rotary gate:** Hold `CRANK` to turn the gate; tap `DROP BALL` when it lines up with the target arrow.

A mistake restarts the current station and costs points, not the whole course. The buttons also respond to **J/K** or **Left/Right** keys. This is an original four-mechanism proof of concept inspired by the feel of manually operating plastic toy mechanisms, not a duplicate of a Screwball Scramble product.

### Tilt Labyrinth
- **Touch:** drag *from anywhere on the playfield* to tilt the board relative to your initial finger position; release to let the tilt level out. Or use the independent X and Y sliders in the control panel.
- **Keyboard:** Arrow keys or WASD.
- The **entire board visibly tilts** with perspective-like shear, rotation and a moving shadow, plus a separate bubble-level indicator. Ball motion has acceleration, momentum, damping, and collision with wooden walls. Rolling into one of the dark holes returns you to the beginning; the goal is the brass G cup.

### Shoot the Bear
- Drag to aim; release to fire, or press the FIRE button. Keyboard arrows/WASD to aim and Space to shoot.

### Electric Crane
- **Touch:** drag the on-glass targeting ring over the carousel or use LEFT/RIGHT/FRONT/BACK hold-buttons. Tap **DROP CLAW** when ready.
- **Keyboard:** arrow keys to move, Space to drop.
- The miniature platform rotates continuously. A successful grip requires the prize to be under the claw **when it arrives**, not when you start the descent. Five drops per round; picked-up prizes disappear from the carousel.

### Ten Strike
- **Touch:** adjust **AIM** slider, hold **HOLD TO WIND / RELEASE** to charge, release it inside the gold spring band. Tap/drag the wooden lane to aim, too.
- **Keyboard:** Left/Right adjusts the aim via the playfield (touch preferred), Space to hold/release the spring.
- Five frames, each with up to two balls. A strike scores 30; a spare scores 20; an open frame scores the total pins knocked down (an intentional simplified homage to the original backglass scoring, not standard ten-pin rules). The off-center strike pocket requires aim and appropriate power.

### Relay Switchyard
- **Touch:** use the three colored buttons or the switches on the glass, and press **START BELT**. Press START again to pause if needed.
- **Keyboard:** 1/2/3 to throw the red/gold/blue relay switches.
- Every parcel carries a stamp. Select its matching colored chute before it crosses the sensor. Relays take a fraction of a second to latch, so very late changes fail. Twelve parcels per shift, three fuses, escalating conveyor speed and combo bonuses.



All games have **Reset**, sound toggle, fullscreen attempt, and local best scores. Sounds are synthesized with Web Audio. No external assets, accounts, server calls, or downloads are required after you save the HTML.

## Technical approach

- Pure **HTML + CSS + Canvas + JavaScript**, no external libraries or image assets.
- One portable file, designed to fit both portrait and landscape phone screens.
- The *Ball Walk* and *Shoot the Moon* games share a retuned **rod/ball geometry-and-gravity integrator** with changing ball height, projected gravitational force, inertia, and friction. It was tested across static spread values to prevent the single-setting jackpot exploit. See [docs/physics.md](docs/physics.md).
- *Tilt Labyrinth* has 2D acceleration/inertia, rounded ball-versus-wall collision resolution, and a tilting rendering transform for the whole board. Its maze is independently generated with a fixed seed; holes are placed in dead ends off the guaranteed path.
- *Electric Crane* has a rotating eight-prize platform, independently movable targeting boom, descending/retracting claw, deterministic proximity-based catches, and a five-drop limit.
- *Ten Strike* has a wind-up oscillator with a gold power window, angular aim, animated miniature pins, pin-count knockdown resolution, and five simplified bowling frames.
- *Relay Switchyard* has a continuously moving belt, color-coded packets, timed relay latching, twelve deliveries, three fuses, progressive belt speed, and combo scoring.
- *Marble Mechanica* has four mechanical stations. The teetering bridge has player torque, marble-driven tipping and a two-second center balance requirement; timed platforms now use shrinking hit windows, four lives and missed-cycle penalties. The launcher and rotary gate remain rule-based.
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
- [The Henry Ford, *Electric Traveling Crane* (circa 1933)](https://www.thehenryford.org/collections/explore/artifact/255525)
- [*Billboard*, December 30, 1957: Williams Ten Strike machine and controls](https://www.worldradiohistory.com/Archive-All-Music/Billboard/50s/1957/Billboard%201957-12-30.pdf)
- [Museum of the Game: Williams Ten Strike](https://www.arcade-museum.com/Arcade/ten-strike--williams--1958--5995)

## Roadmap

- Further tuning rail physics with physical measurements and real-world footage; the current model is an approximation, not a full multibody solution.
- Add gradual physical bridge movement and optional adjustable game difficulty.
- Improve rolling sound and tactile feedback.
- Tune prize crane grip timing and improve visual depth of the winch.
- Give the miniature bowler more detailed individual pin interactions and optional regulation scoring.
- Expand relay sorter's mechanical switch visual feedback, add difficulty settings.
- Add more original mechanical obstacle modules and alternate labyrinth layouts.
- Optional touchscreen/gamepad presets and better accessibility options.