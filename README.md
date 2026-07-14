# Falling-Ball Lab 🎾📄

An interactive physics simulation that races a **tennis ball** against a **crumpled paper ball**
dropped from the same (configurable) height — the classic demonstration of why air resistance,
not mass, decides who lands first.

It is a single, dependency-free `index.html`: plain HTML + CSS + canvas + vanilla JavaScript,
so it renders anywhere GitHub Pages can serve a static file.

## Features

- **Animated drop scene** with a height ruler, strobe-style motion trails, and bounces.
- **Live charts**: height vs. time and speed vs. time for both balls, with terminal-velocity
  guide lines and hover tooltips.
- **Everything is configurable**: drop height, gravity, air density, playback speed, and for
  each ball its mass, diameter, drag coefficient, and restitution (bounciness). Air resistance
  and bouncing can be toggled entirely.
- **Presets**: Earth defaults, vacuum (Apollo 15 mode — they land together), the Moon, and a
  55 m Tower-of-Pisa drop.
- **Predictions and results table**: terminal velocities, predicted vs. measured fall times,
  impact speeds, bounce counts.

## The physics

Each ball is modeled as a sphere with quadratic aerodynamic drag and buoyancy
(downward positive):

```
a = g·(1 − ρV/m) − (ρ·Cd·A / 2m) · v·|v|
```

integrated with a fixed-step 4th-order Runge–Kutta scheme at 480 steps per simulated second.
Landings are located by interpolating within the step; bounces reflect the velocity scaled by
the restitution coefficient.

## Running it

- **GitHub Pages**: Settings → Pages → *Deploy from a branch*, pick the branch and `/ (root)`.
  The page is `index.html`, so the site root just works. (A `.nojekyll` file is included so
  Pages skips Jekyll processing.)
- **Locally**: open `index.html` in a browser, or `python3 -m http.server` and visit
  `http://localhost:8000`.
