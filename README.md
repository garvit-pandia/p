# Garvit Pandia — The Material Index

A curated collection of **fourteen completely independent portfolio websites**, each a
different design concept built around the same fictional-but-believable career data.
The repo root `index.html` is the **Material Index** — a museum-style chooser that
showcases all fourteen variants with live preview cards.

> **🌐 Main website (deployed):** <https://garvit-pandia.github.io/p/> — this is the
> root `index.html` (the chooser / Material Index), live on GitHub Pages.
> Open the source directly: [`index.html`](./index.html)

Each variant is self-contained in its own subfolder — zero shared code, zero
cross-contamination. Each one is a production-ready portfolio; pick any and it can
stand alone.

## The fourteen portfolios

| Folder | Theme | Brief description |
|--------|-------|-------------------|
| `v1-light/` | Light · Archival | **Sunlit Archive** — warm paper, ink and sunlight. Editorial archive of a careful keeper: developing-photo hero, rubber-stamp headers, handwritten marginalia, pin-able notes, solar-dial scroll progress. |
| `v2-dark/` | Dark · Celestial | **Midnight Index** — a star chart of a career. 3D starfield with orbiting rings, comet cursor trail, self-typing terminal, star-chart scroll rail, nebula glow, star-drift parallax. |
| `v3-wild/` | Wild · Dreamlike | **Dream Loom** — silk threads and aurora. Raw WebGL2 aurora shader, kinetic type, silk-thread cursor trail, woven scroll thread with eyelets, living-palette sections, thread tension on scroll velocity. |
| `v4-brutalist/` | Brutalist · Industrial | **MONO_FACTORY** — the portfolio as an industrial machine. Neo-brutalism with hard shadows and Anton type, typed terminal, receipt-print spec sheets, CLI block cursor, interactive factory console, command flicker. |
| `v5-glass/` | Glass · Elegant | **Glass Horizon** — light through glass. Premium glassmorphism, drifting orbs, Three.js glass prisms (cursor-reactive with glint), sunbeam scroll ray, 3D tilt glass cards. |
| `v6-scrollstory/` | Scrollytelling · Organic | **The Field Journal** — a botanist's field log. Pinned parallax scenes, horizontal snap gallery, self-drawing timeline, sketch underlines, field-margin rail, press-able specimens with a collection tally. |
| `v7-voxel/` | 3D · Voxel | **Voxel World** — a Three.js isometric voxel diorama (InstancedMesh, no shadow maps). Every section is an island; the camera flies between them on scroll; day→night sky, windmill, train, beacon, pulsing windows. Signature: clickable voxel progress rail. |
| `v8-abyss/` | Dark · Bioluminescent | **The Abyss** — a single-canvas deep-sea dive. Plankton, jellyfish, light rays, sonar pings; depth rail 0 → 11,204 m (Challenger Deep); projects as glowing specimen jars. Signature: hover a specimen → sonar ping. |
| `v9-ghostware/` | Cyber · Hologram | **Ghostware** — a holographic memory archive. Rotating particle hologram, scanlines, fake telemetry, ARCH-serial memory slots that glitch-load on click. Signature: `ACCESS://` command bar (help / recall ARCH-#### / jump / sync). |
| `v10-typevolt/` | Editorial · Kinetic | **Typevolt** — the kinetic editorial machine. Pure DOM/CSS, zero canvas: split-letter headings choreographed by scroll, rotating role word, magnetic buttons, speaking cursor, spec-sheet skills. Signature: heading letters repel from the pointer. |
| `v11-event-horizon/` | Dark · Cosmic | **Event Horizon** — the portfolio as a black hole. Scroll = falling in; content spirals inward as disk rings; canvas-2D accretion disk with pre-rendered glow sprites. Signature: gravity — depth-scaling + rotation that increases as you descend. |
| `v12-mycelium/` | Dark · Organic | **Mycelium** — the portfolio as a living fungal network. Sections are fruiting bodies connected by hyphae that grow as you scroll; canvas-2D network with dashoffset growth, glowing node halos, drifting spores. Signature: growth — nothing appears, everything grows. |
| `v13-origami-aurum/` | Light · Paper | **Origami Aurum** — warm paper origami gallery (parchment + terracotta + gold foil). Sections unfold like paper flaps (CSS 3D), folded-paper letter hero, stamp-grid achievements, dog-eared project cards. Zero canvas — the light perf showcase. |
| `v14-signal/` | Dark · Radio | **SIGNAL//DECODE** — the portfolio as an intercepted cosmic transmission. The name decodes from static letter by letter, canvas static + spectrogram that gains signal on scroll, `[ DECODED ]` section headers, transmit-back contact. Signature: decode. |

## How to preview

- **Live:** the whole collection is deployed on GitHub Pages —
  [https://garvit-pandia.github.io/p/](https://garvit-pandia.github.io/p/) (chooser)
  with every variant at `…/p/v1-light/` … `…/p/v14-signal/` (all 14 verified live).
- **Local:** open `index.html` in the repo root for the chooser page, or the
  `index.html` inside any variant folder directly. No build step, no npm install,
  no server needed. Internet required for fonts and the Three.js CDN
  (variants 7–14 use zero external images — everything is code-drawn).

## MVP features in ALL fourteen

- Animated hero (petals / starfield / aurora shader / typewriter / glass prisms /
  scrollytelling / voxel world / deep-sea canvas / hologram / kinetic type)
- Scroll-triggered reveals + smooth scrolling
- Contact form with mailto fallback (works with zero backend)
- "Download Resume" button (PDF copy in each folder: `Garvit_Pandia_Resume.pdf`)
- Full resume content: About, Projects, Skills, Education, Achievements,
  Experience, Contact
- `prefers-reduced-motion` support + mobile responsive + focus-visible styles
- Pause-heavy animations when the tab is hidden / canvas off-screen (perf)
- Performance discipline: DPR caps (1.25–1.75), pre-rendered glow sprites (no
  per-frame shadowBlur), InstancedMesh + no shadow maps in the voxel world,
  transform/opacity-only DOM animation, passive listeners, capped particle counts

## Content note

Per the user's brief, all content in every variant (and the chooser) is an
intentionally exaggerated, fictional-but-believable dataset — projects, experience,
testimonials, and stats are curated fiction. **The only real data on the site: the
name "Garvit Pandia" and the real contact block** (email, phone, GitHub, LinkedIn).
The canonical source is `docs/synthetic-data-pool.md`; each variant renders its
curated subset in its own visual language. The fictional-resume-data file it
replaced is preserved in `docs/fictional-resume-data.md` (superseded).

## Quality process

All fourteen sites were verified in a real browser (zero console errors,
interactions tested — glitch-load, command bar, camera flight, rail, pings,
kinetic letters) and rated by an independent vision model (1–10 across visual
design, typography, layout, uniqueness, polish — average 9.32/10 after the
synthetic content update). Audit findings were cross-checked against source before
fixing; only verified flags were changed.

## NOTE — project links

Project cards link to the GitHub profile (`github.com/garvit-pandia`) for now.
When you have the real URLs, swap the `href` on the project links (search for
`github.com/garvit-pandia` inside each `index.html`).

## Tech

- Vanilla HTML / CSS / JS — no frameworks, no build tools
- Three.js r160 via CDN (import map) — voxel world uses InstancedMesh +
  MeshLambertMaterial, fake blob shadows instead of shadow maps
- Canvas 2D engines for the abyss (sprite-based glow), the hologram,
  event-horizon disk, mycelium network, and signal static
- Raw WebGL2 shader for the aurora variant (v3)
- Pure-DOM kinetic typography for Typevolt (zero canvas — the perf showcase)
- Google Fonts (v1–6 also use Unsplash photography; v7–14 are 100% code-drawn)
