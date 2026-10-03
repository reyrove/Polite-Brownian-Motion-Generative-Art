# Polite Brownian Motion — Generative Art

> A seed-based generative system for bounded walk compositions.  
> A reproducible catalogue of computational walk studies.

---

## What is this?

**Polite Brownian Motion** is a generative design system built on the classical random walk — bounded. Instead of letting each path wander freely, every step is constrained inside a margin, so the walkers drift but never escape. Each palette runs its own set of walks across the field, layered at different rotations, until the composition becomes a luminous mesh of overlapping trajectories.

Every artwork in this catalogue is defined by a single numeric seed. The same seed always produces the identical composition — making each piece **traceable, reproducible, and licensable** across textile, print, and apparel applications.

Named for the philosophical tension between *Brownian motion* (a random walk with no memory) and *politeness* (a walk that respects its bounds), **Polite Brownian Motion** reframes bounded drift as a textile.

---

## Live

🌐 **[View the catalogue →](https://reyrove.github.io/Polite-Brownian-Motion/)**

---

## The System

The generator combines two layers:

| Layer | Description |
|-------|-------------|
| **Walkers** | Each palette contributes a walker that moves in one of four directions per step, rotated by that palette's phase. |
| **Margin** | Every step is clamped inside a bounded margin — so the walk drifts, but never escapes the field. |

Both layers are driven by the same seed, ensuring deterministic output.

### Parameters

- **Step count per palette** — 202 to 700 max steps
- **Palettes** — 2 to 8 colours per palette, drawn from 45 curated sets
- **Backgrounds** — 27 curated dark tones
- **Rotation rings** — `floor(2π / max(θ)) + 1`
- **Margin fraction** — 30 to 100 subdivisions of the canvas
- **Shadow glow** — `w / (2 × xsteps)` per walker
- **Step shape** — four-direction L-shaped moves, bounded to the canvas

---

## Structure

```
Polite-Brownian-Motion/
├── index.html                    ← Full catalogue (single-file)
├── images/
│   ├── fav.svg
│   ├── brownian-tote.png
│   ├── brownian-cushion.png
│   └── ...
├── Polite-Brownian-Motion.jpg    ← Apparel mockup
└── README.md
```

The entire project is contained in a single `index.html` — no build step, no dependencies, no framework. Open it in any modern browser.

---

## Features

- **Seed-based generation** — every composition is deterministic and reproducible
- **Live catalogue** — cover, statement, plate, surfaces, process, archive, commission sections
- **Multiple surfaces** — print, scarf, textile, wallpaper — all rendered from the same seed
- **Archive of 8 seeds** — click any plate to load it into the main view
- **PNG export** — download any composition directly from the browser
- **Keyboard shortcuts** — `R` for new seed, `S` to save
- **Legal modal** — licensing, terms, and credits built in
- **Responsive** — works on desktop, tablet, and mobile
- **Mobile-first navbar** — horizontally scrollable with fade hint
- **Fast load** — master offscreen rendering + batched path strokes

---

## Usage

### Generate a new composition

Click **New Seed** or press `R`.

### Download the current composition

Click **Download** or press `S`.

### Load a seed from the archive

Click any plate in the **Archive** section.

---

## Color System

Every composition is drawn from two curated palettes:

**Background — 27 dark tones**

Blacks, deep blues, teals, muted reds, charcoals, deep purples, and a handful of warm accents.

**Foreground — 45 curated palettes**

Each palette contains between 2 and 8 colours chosen for contrast and coherence — neon duos, triad harmonies, quartet contrasts, and larger rainbow sets.

Each walker draws its colour from the current palette's colour list. Because both the walk and the palette are seeded, no two compositions share the same rhythm of line and hue.

---

## Technical Notes

- Pure vanilla JavaScript — no libraries
- Canvas 2D rendering
- Custom xorshift random generator for deterministic seeds
- Device-pixel-ratio aware rendering
- Fully static rendering — one seed produces one composition, no animation loops
- **Master offscreen rendering** — the plate is rendered once at 1024² into a master canvas; cover, framed print, and all four surfaces blit from it via `drawImage()`
- **Batched path strokes** — walker segments are grouped into chunks of 50 with a single `beginPath()` / `stroke()` per chunk, cutting canvas state changes by ~50×
- **Reduced archive budget** — thumbnails render at 320² with 500 steps per palette (vs 20,000 for the master), which is visually indistinguishable at that size
- `prefers-reduced-motion` respected

---

## About

**Polite Brownian Motion** is a project by [Reyhaneh Daneshdoost](https://reyrove.github.io/) — an Iranian-born artist working at the intersection of classical textile logic and generative systems.

The work begins with a simple observation: the woven surface — repetitive, mathematically structured, infinitely variable — has always been a form of computation, long before computers.

**Polite Brownian Motion** is an attempt to render that logic visible.

> *A walk that never crosses its own path is not truly random — it is polite.*

---

## Licensing

All compositions are seed-documented and available for licensing across textile, surface, and apparel applications.

For commercial use, custom editions, or exclusive rights:

📧 **reyhanehdaneshdoost@gmail.com**

See the **Licensing** section in the live catalogue for details.

---

## Links

- 🌐 [Website](https://reyrove.github.io/)
- 📷 [Instagram](https://www.instagram.com/rey._.rove/)
- 💼 [LinkedIn](https://www.linkedin.com/in/reyhaneh-daneshdoost-730481160/)
- 🐦 [X](https://x.com/reyrove)

---

## Credits

**Design & Generative System**  
Reyhaneh Daneshdoost

**Typefaces**  
Cormorant Garamond · DM Mono

**Edition**  
Polite Brownian Motion — Autumn 2026

---

<p align="center">
  <em>Generative Bounded Walk</em><br />
  <sub>© Reyrove Studio · All compositions reproducible by seed</sub>
</p>