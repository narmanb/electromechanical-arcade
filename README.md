# Electromechanical Arcade

A playable, browser-based collection inspired by historical mechanical and electromechanical arcade machines. **Prototype v0.1.** Works on phones, tablets, and desktop browsers. No frameworks, external assets, internet connection or build step required.

## Play

Open `index.html` in a browser, or visit a static hosting deployment of this repository. For GitHub Pages: Settings → Pages → Deploy from branch → `main` / root.

### Mini Drive (Kasco, 1959)

Steer the toy car left and right to stay on the scrolling road and earn points. Drive for 75 seconds and collect checkpoint bonuses. Use left/right buttons, the steering slider, touch anywhere inside the playfield, or arrow keys/A-D.

### Ball Walk (Cointronics, 1960s)

Tap **LIFT BALL**. Gently **open** the two rods to walk the steel ball toward the far end; **close** them to reset your stroke, then repeat. If you open them too wide (above ~85%) the ball falls into a scoring pocket. You receive five balls. Reaching the jackpot earns 500 points and doubles the final total. Use the touch buttons, the spread slider, drag across the playfield, or arrow keys/A-D. Press Space to lift the next ball.

## Other controls

- `R`: restart current machine.
- `FULLSCREEN`: maximize the cabinet if the browser permits it.
- `SOUND`: toggle synthesized clicks, bell and buzzer.
- Scores are stored in the local browser using localStorage where available.

## Scope and authenticity

These are **original, unlicensed approximations**, *not* exact historical restorations. The mechanisms, dimensions, scoring, cabinet artwork, and gameplay have been simplified for a mobile proof of concept. Notably, **Ball Walk was entirely mechanical**, even though it could have optional electric lights, bell, and buzzer.

No third-party pictures, sounds, fonts or code dependencies are bundled. UI illustrations and playfields are drawn using CSS and HTML Canvas. No generated images used.

### Historical references

- Mini Drive gameplay footage: https://www.youtube.com/watch?v=svQzx8OI8PQ
- Mini Drive overview: https://ameblo.jp/dorikin86/entry-12477043796.html
- Ball Walk description: https://www.arcade-museum.com/Trade-Stim/ball-walk
- Ball Walk original restoration: https://forums.arcade-museum.com/threads/my-restoration-of-a-ball-walk-1960s-game-cointroinics.333857/
- Ball Walk reference: https://www.pinrepair.com/arcade/ballwalk.htm

## Roadmap

1. Playtest on touchscreens and tune steering and twin-rail response.
2. Improve mechanical simulation, playfield depth, shadows, and authentic cabinet presentation.
3. Validate original scoring, dimensions and variants from manuals or surviving machines.
4. Split into maintainable modules as the collection grows, then add another machine.
5. Optionally wrap the web version as an Android APK.

© No claim of ownership of the names or original machine designs of Kasco or Cointronics. Historical names are used for identification; this prototype is unaffiliated with the manufacturers.