# Brief — v11 "EVENT HORIZON" (genesis wave)

Build `/home/garvit/projects/portfolio5/variant-11-event-horizon/index.html` — a SINGLE self-contained HTML file (embedded CSS/JS, Google Fonts CDN, no build step). ~1100–1500 lines.

## Concept
The portfolio as a black hole. You are falling in. Every section is a ring of the accretion disk; content is light that has to escape. Scroll = descent toward the singularity. The page is one continuous fall — hero far outside, projects spiraling closer, achievements inside the photon sphere, contact at the event horizon itself.

## Narrative compass (ONE idea: gravity)
Everything orbits, warps, and accelerates inward. Text enters from the disk's edge, curves as it settles, and every heading carries a slight rotation that increases with depth. Motion always pulls DOWN/INWARD — never sideways decoration.

## Architecture
- Canvas-2D background (NO WebGL): accretion disk rendered with pre-rendered radial-gradient glow sprites (offscreen canvas, drawn once) — no per-frame shadowBlur. Particles = dust spiraling in, pool capped at 140. DPR cap 1.5.
- DOM sections scroll normally over the canvas; sections get a `data-depth` attribute; a scroll-linked rAF applies `transform: scale() rotate()` + opacity per depth (transform/opacity ONLY — no layout props in the loop).
- Fonts: "Space Grotesk" (display) + "JetBrains Mono" (data). Palette: accretion gold #ffb347 / #ff7a1a, disk amber #ffd9a0, void #050208, text #f5e9d8, accent rim #ffe6c7.
- Prefix ALL new classes `eh-`.

## Sections (all MVP + genesis data)
1. **Hero** — huge name "GARVIT PANDIA" in Space Grotesk 800, slowly orbiting accent ring behind it (CSS animation, transform-only), stats strip as orbital data chips (pick 6 stats verbatim from data file). Subtitle "Engineer of improbable interfaces". Scroll hint: "descend".
2. **About/signal** — short bio paragraph + the 3 core + 2 genesis testimonials as "transmissions" (mono, bracketed timestamps).
3. **Projects** — at least 6: 3 core (NebulaOS, QuantumSort, Gridlock) + 3 genesis (Helios, Bloom, Relay). Each card = disk ring segment: name, one-line description, metric line (verbatim numbers), star count. Cards reveal with a slow spin-in (rotate -4° → 0, scale 0.96 → 1, 500ms, stagger 90ms).
4. **Achievements** — all 7 core + 4 genesis achievements as a "mass log": rows that slide in from the right edge (the disk's outer edge) with mono index numbers (01…11).
5. **Experience + skills** — 5 experience entries; skills as 4 grouped "spectral bands" (languages/AI/web/systems) with level as arc-length (SVG arc or conic-gradient bar, no canvas). Genesis contributions strip (4 lines, mono).
6. **Ratings strip** — the genesis ratings row as glowing chips (4.9★ Bloom etc.) — simple flex row, reveal stagger.
7. **Contact** — form (name/email/message → mailto:garvit9829@gmail.com fallback) + direct links (email/phone/GitHub/LinkedIn/site). Section framed as "transmitting at the horizon".

## Mandatory perf rules
DPR cap 1.5 · particle pool capped (140) · no per-frame shadowBlur (pre-rendered sprites) · rAF pauses on `document.hidden` + when the canvas is offscreen (IntersectionObserver) · transform/opacity-only animations · passive listeners · prefers-reduced-motion: paint ONE static frame, no orbit/spin, reveals become opacity-only.

## MVP checklist (MUST all be present)
Contact form with mailto fallback · Download resume button linking `./Garvit_Pandia_Resume.pdf` (the file is copied into your folder already — do not create it) · scroll-triggered reveal animations + `scroll-behavior:smooth` · animated canvas hero · 44px tap targets · mobile responsive (stack sections, shrink type) · `<noscript>` fallback that un-hides content.

## Verification (file-tools only — controller does browser checks)
`node --check` every script block (extract to /tmp first), brace-balance every style block, grep duplicate `id=` values, confirm every `eh-` class defined once + used, confirm the PDF link path is exactly `./Garvit_Pandia_Resume.pdf`. Report line count + all check results.
