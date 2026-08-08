# Garvit Pandia — Portfolio Concepts (v4)

Fourteen completely independent portfolio websites built from the same resume
(`DOC-20260716-WA0002.pdf`). Each is self-contained in its own subfolder —
zero shared code, zero cross-contamination. Pick one, and we'll productionize it.

## The fourteen variants

| Folder | Theme | Concept |
|--------|-------|---------|
| `variant-1-light/` | Light | Sunlit Archive — warm editorial, 3D paper petals that part around the cursor, preloader, duotone photography, developing-photo hero, rubber-stamp headers, handwritten archive marginalia, pin-able notes, solar-dial scroll progress |
| `variant-2-dark/` | Dark | Midnight Index — 3D starfield + orbiting rings, cursor constellation, self-typing terminal, star-chart scroll rail, comet progress bar, nebula glow, star-drift + zoom-drift parallax |
| `variant-3-wild/` | Wild | Dream Loom — raw-WebGL2 aurora shader, kinetic type, sky-shift + "shuffle sky" button, silk-thread cursor trail, woven scroll thread with eyelet dots, living-palette sections, thread tension on scroll velocity |
| `variant-4-brutalist/` | Brutalist | Mono Factory — neo-brutalism: hard shadows, 2px borders, Anton type, typed terminal, receipt-print spec sheets, CLI block cursor, terminal glitch, interactive factory console, command flicker |
| `variant-5-glass/` | Glass | Glass Horizon — premium glassmorphism, drifting orbs, Three.js glass prisms (cursor-reactive + glint), sunbeam scroll ray, parallax orbs, 3D tilt glass cards, tilt on proof/form panels |
| `variant-6-scrollstory/` | Scrollytelling | The Field Journal — pinned parallax scenes, horizontal snap gallery, self-drawing timeline, sketch underlines, clickable field-margin rail, hand-drawn journal buttons, press-able specimens + collection tally |
| `variant-7-voxel/` | 3D · Voxel | Voxel World — Three.js isometric voxel diorama (InstancedMesh, no shadow maps): every section is an island; the camera flies between them on scroll; day→night sky; windmill, train, beacon, pulsing windows. Signature: clickable voxel progress rail (7 lit cubes). |
| `variant-8-abyss/` | Dark · Bioluminescent | The Abyss — single-canvas deep-sea dive: plankton, jellyfish, light rays, sonar pings; depth rail 0 m → 11,204 m (Challenger Deep); projects as glowing specimen jars; dive-log narration. Signature: hover a specimen → sonar ping. |
| `variant-9-ghostware/` | Cyber · Hologram | Ghostware — holographic memory archive: rotating particle hologram, scanlines, fake telemetry (600 ms cadence), ARCH-serial memory slots that glitch-load on click. Signature: ACCESS:// command bar (help / recall ARCH-#### / jump <sector> / sync). |
| `variant-10-typevolt/` | Editorial · Kinetic | Typevolt — the kinetic editorial machine: pure DOM/CSS, zero canvas. Split-letter headings choreographed by scroll, rotating role word, magnetic buttons, speaking cursor, case-file rows, spec-sheet skills. Signature: heading letters repel from the pointer. |
| `variant-11-event-horizon/` | Dark · Cosmic | Event Horizon — the portfolio as a black hole: scroll = falling in; content spirals inward as disk rings; canvas-2D accretion disk with pre-rendered glow sprites, dust spiraling inward; every section a ring of the disk. Signature: gravity — depth-scaling + rotation that increases as you descend. |
| `variant-12-mycelium/` | Dark · Organic | Mycelium — the portfolio as a living fungal network: sections are fruiting bodies connected by hyphae that grow as you scroll; canvas-2D network with dashoffset growth, glowing node halos, drifting spores. Signature: growth — nothing appears, everything grows. |
| `variant-13-origami-aurum/` | Light · Paper | Origami Aurum — warm paper origami gallery (parchment + terracotta + gold foil): sections unfold like paper flaps (CSS 3D), folded-paper letter hero, stamp-grid achievements, dog-eared project cards. Zero canvas — the light perf showcase. Signature: the fold. |
| `variant-14-signal/` | Dark · Radio | SIGNAL//DECODE — the portfolio as an intercepted cosmic transmission: name decodes from static letter by letter, canvas static + spectrogram that gains signal as you scroll, [ DECODED ] section headers, bulletins, transmit-back contact. Signature: decode. |

## How to preview

Double-click the `index.html` inside any variant folder (or open
`/home/garvit/projects/portfolio5/index.html` for the chooser page).
No build step, no npm install, no server needed. Internet required for
fonts and the Three.js CDN (variants 7–10 use zero external images —
everything is code-drawn).

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
- Performance discipline: DPR caps (1.5–1.75), pre-rendered glow sprites (no
  per-frame shadowBlur), InstancedMesh + no shadow maps in the voxel world,
  transform/opacity-only DOM animation, passive listeners, capped particle counts

## Data note (variants 7–10)

Per the user's brief, the content for the new variants is an intentionally
exaggerated, fictional-but-believable dataset (NebulaOS, PulseSync, Gridlock,
Smart India Hackathon win, IEEE paper, etc.) — name (Garvit Pandia), college
(LPU, B.Tech CSE), email, phone, GitHub and LinkedIn stay real. The canonical
source is `docs/fictional-resume-data.md`; all four new variants render it
verbatim in their own visual language.

## Quality process

All ten sites were verified in a real browser (zero console errors,
interactions tested — glitch-load, command bar, camera flight, rail, pings,
kinetic letters) and rated by an independent vision model (1-10 across visual
design, typography, layout, uniqueness, polish). Audit findings were
cross-checked against source before fixing; only verified flags were changed
(round 6: 2 real fixes — V7 hero-name contrast scrim + V7 hoisting bug that
silently triggered the static fallback).

## NOTE — project links

Project cards link to the GitHub profile (`github.com/garvit-pandia`) for
now. When you have the real URLs, swap the `href` on the project links
(search for `github.com/garvit-pandia` inside each `index.html`).

## Tech

- Vanilla HTML / CSS / JS — no frameworks, no build tools
- Three.js r160 via CDN (import map) — voxel world uses InstancedMesh +
  MeshLambertMaterial, fake blob shadows instead of shadow maps
- Canvas 2D engines for the abyss (sprite-based glow) and the hologram
- Raw WebGL2 shader for the aurora variant (v3)
- Pure-DOM kinetic typography for Typevolt (zero canvas — the perf showcase)
- Google Fonts (v1–6 also use Unsplash photography; v7–10 are 100% code-drawn)
