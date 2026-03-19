# black-hole-simulation
# Black Hole Simulation — Einstein's General Relativity in Python

A fully animated, physics-based black hole simulator built in Python and Google Colab.
Simulates real astrophysical phenomena derived from Einstein's field equations:
accretion disk dynamics, relativistic jets, gravitational lensing, and time dilation.

---

## What it looks like

Particles spiral into the black hole following real orbital mechanics. The disk glows
white-hot near the event horizon and deep red at the outer edges, matching the actual
temperature profile of accretion disks observed by X-ray telescopes. Background stars
are displaced by gravitational lensing. Plasma jets shoot from the poles at near-light speed.

---

## Physics implemented

**Schwarzschild radius** — the event horizon, derived from Einstein's field equations:

```
r_s = 2GM/c²
```

In natural units (G = c = 1), this simplifies to r_s = 2M. Nothing that crosses this
boundary can return — including light.

**ISCO (Innermost Stable Circular Orbit)** — the last stable orbit around the black hole.
For a non-spinning black hole: r_isco = 6M. For a spinning (Kerr) black hole, the spin
parameter `a` warps spacetime inward, shrinking the ISCO and allowing matter to orbit
closer. This is why spinning black holes are more efficient at capturing matter.

**Kepler's third law** — orbital angular velocity:

```
omega = sqrt(GM / r³)
```

Particles closer to the black hole orbit faster. The speed differential between inner
and outer orbits creates friction, heating the disk to millions of Kelvin.

**Gravitational lensing** — light deflection near mass, approximated as:

```
deflection ≈ 4GM / (c² × impact_parameter)
```

This is the same formula Arthur Eddington measured during the 1919 solar eclipse,
the first observational confirmation of General Relativity.

**Gravitational time dilation** — from the Schwarzschild metric:

```
dt_proper = dt_far × sqrt(1 - r_s/r)
```

At the event horizon, time stops completely from a distant observer's perspective.
At the ISCO, clocks run measurably slower — this effect is real and is corrected
for in GPS satellite systems every day.

**Relativistic jets** — powered by the Blandford-Znajek mechanism (1977). A spinning
black hole drags spacetime into rotation (frame-dragging), winding up magnetic field
lines that thread the accretion disk and launching plasma at near-light speed from
both poles. Jet power scales as spin²: set spin to 0 and jets disappear entirely.

**Disk temperature profile** — based on the Novikov-Thorne thin disk model (1973):

```
T(r) ∝ M^(1/4) × r^(-3/4)
```

Temperature drops as r^(-3/4) outside the ISCO. Inner regions exceed 10–100 million
Kelvin, emitting in X-rays. This is how astronomers detect black holes — by finding
unexplained X-ray sources in the sky.

---

## Project structure

```
black_hole_simulation.ipynb   ← main notebook, all 10 cells
README.md                     ← this file
black_hole.gif                ← exported animation (optional)
```



## Libraries used

- `numpy` — fast array math, moves all particles simultaneously
- `matplotlib` — drawing and animation engine
- `matplotlib.animation.FuncAnimation` — the frame loop driver
- `ipywidgets` — interactive sliders inside Colab
- `scipy` — not required for the base simulation

---

## Things you can tweak

Open Cell 10 and change these values at the top:

```python
M      = 2.0    # black hole mass — scales all radii
SPIN   = 0.75   # 0 = Schwarzschild (no spin), 0.99 = near-maximum Kerr
N_DISK = 140    # number of accretion disk particles
N_JET  = 100    # number of jet particles
TRAIL  = 22     # trail length per particle (frames)
```

Try `SPIN = 0.0` to remove jets entirely. Try `M = 10.0` to see a more massive black hole
with a wider event horizon and larger ISCO.

---

## Background

This project was built as a learning exercise to understand how Einstein's General
Relativity translates into real, observable phenomena. The simulation uses natural units
(G = c = 1) standard in theoretical physics, and implements equations from:

- Schwarzschild (1916) — static black hole solution
- Kerr (1963) — rotating black hole solution
- Novikov & Thorne (1973) — thin accretion disk temperature model
- Blandford & Znajek (1977) — relativistic jet mechanism

---

## License

MIT 
