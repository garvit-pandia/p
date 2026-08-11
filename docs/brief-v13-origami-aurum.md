# Brief — v13 "ORIGAMI AURUM" (genesis wave)

Build `/home/garvit/projects/portfolio5/v13-origami-aurum/index.html` — a SINGLE self-contained HTML file (embedded CSS/JS, Google Fonts CDN, no build step). ~1000–1400 lines.

## Concept
The portfolio as a warm origami gallery — the LIGHT variant of the genesis wave. Every section is a folded paper plane; scroll unfolds it (rotateX 90° → 0, like a page folding open). The whole page is cream paper, terracotta ink, gold foil accents. Zero canvas — a pure CSS 3D + kinetic-type performance showcase (this variant must fly on a mid-range phone).

## Narrative compass (ONE idea: paper craft)
Everything is folded paper: cards have fold creases (subtle gradient lines), headers sit on paper strips with punched-hole borders, buttons are paper tabs that lift on hover. Sections open like origami flaps — motion is always a fold or an unfold, never a slide.

## Architecture
- NO canvas, NO WebGL. All animation = CSS 3D transforms + one rAF for scroll-linked unfold progress (transform/opacity only).
- Section headers: `perspective: 900px` wrapper, header rotates `rotateX(88deg)` → `0` with `transform-origin: top` as it enters (600ms cubic-bezier(.2,.7,.2,1)); content reveals stagger 70ms.
- Fonts: "Fraunces" (display serif) + "Inter" (body) + "JetBrains Mono" (data). Palette (user's warm tokens): parchment #f5f4ed, terracotta #c96442, ink #2b2620, gold foil #d9a441, soft shadow rgba(43,38,32,.12), paper white #fffdf7.
- Prefix ALL new classes `og-`.

## Sections (all MVP + genesis data)
1. **Hero** — name "Garvit Pandia" as folded paper letters (each letter a div that unfolds on load, 40ms stagger), subtitle "Engineer of improbable interfaces", 6 stats as gold-foil chips. A folded-paper sun (CSS conic-gradient circle with fold lines) behind the name — the light theme's centerpiece.
2. **About** — bio + 2 core testimonials as folded note cards (crease line across the middle, tape corners via pseudo-elements).
3. **Projects** — at least 6: 3 core (NebulaOS, India AQI Tracker, Paperweight) + 3 genesis (Bloom, Mira, Monolith). Cards = paper sheets with a fold corner (the classic dog-ear, via a clipped pseudo-element); hover = card lifts 3px + dog-ear unfolds slightly (transform only, 180ms).
4. **Achievements** — 11 (7 core + 4 genesis) as a paper-stamp grid: each achievement = a stamp (rounded rect, dashed border, rotated ±1.5°, terracotta ink) that "stamps" in (scale 1.4 → 1 + opacity, 400ms).
5. **Experience + skills** — 5 entries as paper strips with a date tab; skills = 4 groups with paper bars (terracotta fill on cream track, width animated, transform-origin left, scaleX reveal).
6. **Ratings strip** — gold-foil chips (4.9★ Bloom etc.), foil shimmer on hover (background-position shift — cheap).
7. **Contact** — form styled as a letter (lined paper background via repeating-linear-gradient) + direct links as tabs.

## Mandatory perf rules
Zero canvas · transform/opacity-only (the ONE exception: width/scaleX bar reveals use transform scaleX) · single rAF, paused on hidden/offscreen · passive listeners · prefers-reduced-motion: everything visible instantly, no unfolds, static paper look.

## MVP checklist (MUST all be present)
Contact form with mailto fallback · Download resume button linking `./Garvit_Pandia_Resume.pdf` (file already in your folder) · scroll reveals + smooth scrolling · animated hero (paper letter unfold counts) · 44px tap targets · mobile responsive · `<noscript>` un-hide fallback.

## Verification (file-tools only)
`node --check` every script block (extract to /tmp first), brace-balance style blocks, grep duplicate `id=`, each `og-` class defined once + used, PDF link exactly `./Garvit_Pandia_Resume.pdf`. Report line count + all check results.
