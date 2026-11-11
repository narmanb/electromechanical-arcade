# Rail physics and accuracy notes (v0.4)

This document explains **what is actually simulated** in Shoot the Moon and Ball Walk. The model is *physically motivated*, not a complete reconstruction of the historical machines or a full nonholonomic rigid-body solution.

## Core geometry

The game is a steel sphere supported by two cylindrical rods. The rods have a **fixed narrow hinge** at the start and **moving handles** at the far end, so the distance between them increases along the direction of travel when opened.

Our approximation uses:

- `u`: normalized ball distance along the rods, 0 near hinge, 1 at the handles.
- `L`: rail length (model 0.42 m).
- `R`: steel ball radius (model 0.019 m).
- `d(u) = d_hinge + d_handle * spread * u`: local rod separation.
- `d_handle`: adjustable rod separation at the handle (0.11 m at full spread, a gameplay approximation).
- `rise`: simulated height gained from the rods' physical incline (0.006 m).

The sphere's vertical center above the rod centerline is approximately

`height(u) = rise*u + sqrt(R*R - (d(u)/2)^2)`.

The effective slope is its derivative:

`dh/du = rise - d(u) * (d_handle*spread) / (4*sqrt(R*R - (d(u)/2)^2))`.

The game steps a one-dimensional acceleration proportional to `-g * dh/du`, divided by `L²` and a rolling-inertia factor, and integrates velocity and position. There is also velocity damping (friction) and a small motion-coupling term when the user moves the rods. A ball falls if the local rod separation approaches its diameter. Reaching the far end scores the top pocket.

In v0.4 the rod separation and rise have been retuned. Static-spread browser tests: 20–30% remains stationary or rolls backward; 35–90% starts but drops short of the jackpot. A position-dependent, gradually narrowing control policy can reach the top. These tests describe the game's numerical model, not measurements of a historical machine.

This captures the main surprise of the real game: **opening the rods can make the ball roll uphill along their visible incline because it lowers the ball between them and creates an effective downhill slope.** Ball momentum persists after you narrow the rods. The ball can also roll back toward the hinge.

## What it does not simulate

- Full rigid-body torque and angular momentum, no-slip rolling constraints, rod compliance, and continuous contact forces.
- Material-specific coefficients for steel-on-steel contact.
- Real dimensions, sloping angles, and timing measured from either specific physical machine.
- Ball bouncing and a detailed transition into individual cup geometry after falling.

There are published engineering models that go much further. See Peng Xu's [2011 Clemson thesis](https://open.clemson.edu/all_theses/1209/) and the [Stanford CHARM Lab's simplified haptic rendition](https://charm.stanford.edu/ME327/Group9). This prototype's formulas were informed by their explanations but do not reimplement those projects' code.

## Tilt Labyrinth physics

The tilt maze integrates a 2D velocity vector accelerated by two independent virtual board tilts, with exponential velocity damping. The entire maze and ball now render with a moving tilt transform (skew, rotation and foreshortening) plus a fixed bubble-level indicator. The visual transform is illustrative 2.5D, not a separate 3D board simulation. Each wooden divider is a line segment with thickness. The ball is approximated as a disk, contacts are resolved as a circle-vs-rounded-segment intersection, and the normal component of incoming velocity is suppressed. Black dead-end pockets cause a fall/reset. The maze layout is original and generated from a deterministic depth-first spanning tree, with a guaranteed route between S and G.

## Obstacle course physics

Marble Mechanica is a multi-station mechanical-control *interpretation* of the toy genre. The teetering bridge now includes ball-driven bridge torque, player-applied left/right torque, angular damping, and a two-second center-balance requirement with position, velocity and angle thresholds. The stepping pads have four lives, progressively smaller hit windows and faster sweeps, and automatically deduct a life if a sweep completes without a press. The spring launcher and rotary gate remain rule-based rather than full rigid-body models. We intentionally retain direct mechanical buttons for those stations rather than mapping everything to a virtual joystick.