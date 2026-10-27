# Pavilion Hoops

A real-time pixel-art isometric diorama of a 3×3 basketball cup day, played on the
half-court of an old brick-and-steel pavilion. One HTML file, three.js r160 from a CDN,
no build step.

Play: <https://germanpadua.github.io/pavilion-hoops/>

## The day

Four original clubs — Riverside Owls, Forge Ferros, Gable Magpies, Static Volts — are
drawn into two semi-finals and a final. Games follow FIBA 3×3 half-court rules: first to
11 or the leader at 4:00, 1 point inside the arc and 2 beyond it, a 12-second shot clock,
a clearance after defensive rebounds and steals, check balls at the top after a dead ball,
and overtime to a two-point lead. Between games the polisher crosses the parquet and the
scorer updates the flip cards. The final ends with a trophy, confetti, the day's top scorer
on the honours board, and a fresh draw.

Idle clubs sit on the bleachers. Teams enter from the stage door. The AI runs on-ball and
help defence, spacing and cuts, drives, lay-ups, dunks, contested jumpers, blocks, strips
and rebounds; the on-ball chaser is chosen by intercept time.

## Controls

- **Click** the ball handler to shoot, a teammate to pass, an empty floor spot to drive.
- **Drag** to turn the camera; it snaps to 90° isometric steps. **Wheel / pinch** to zoom.
- **Shoot / Pass / Pause / New cup** buttons; `Space`, `P`, `Esc`, `N`.
- Time / weather segmented controls, palette, pixel size, dither, outlines, raw 3D and
  camera turn controls live in the HUD. Light/dark theme and “How it’s drawn” are top right.
- On phones the HUD stacks; the cup bracket opens from the top bar.

## Drawing

The pavilion is lit 3D geometry rendered to a small offscreen target with no anti-aliasing.
A full-screen pass quantises linear light into a fixed 54-colour OKLab palette, adds an
optional 4×4 Bayer dither, and inks silhouettes from the depth buffer. A flag buffer skips
outline and dither work on translucent panes and nets. The browser performs the integer
nearest-neighbour upscale. The orthographic camera is snapped to the low-res pixel lattice.
“Raw 3D” bypasses the palette/outline pass.

Everything is drawn procedurally: parquet and herringbone border, paint and worn floor
lettering, brick, banners, flip cards, honours board, skyline, emblems, rain and reflections.
The parquet also carries live canvas layers for squeak marks and the polisher's shine.

## Determinism

The simulation runs on a fixed 60 Hz step with a seeded generator. The seed is printed in
the console and can be replayed with `?seed=20261027`. The same seed and the same input
tend to produce the same cup; opening the console exposes `PAVILION.seed`,
`PAVILION.state`, and a small `PAVILION.debug` harness (`ff(seconds)`, `reset(seed)`,
`probe()`, `ascii()`, `pump(seconds)`).

## Files

- `index.html` — the entire game, styles and JavaScript inline.
- `.github/workflows/deploy.yml` — GitHub Pages deployment on every push to `main`.
- `README.md`.

## Credits

Original club names, characters, emblems and geometry. No real brands or likenesses.
Built from scratch with three.js r160.
