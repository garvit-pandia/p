# Brief — v12 "MYCELIUM" (genesis wave)

Build `/home/garvit/projects/portfolio5/v12-mycelium/index.html` — a SINGLE self-contained HTML file (embedded CSS/JS, Google Fonts CDN, no build step). ~1100–1500 lines.

## Concept
The portfolio as a living fungal network. Garvit's career is one mycelium: projects are fruiting bodies, skills are enzymes, achievements are spores released into the network. The page grows — as you scroll, new hyphae branch from existing ones, connecting sections like one organism. Light bioluminescent on near-black soil.

## Narrative compass (ONE idea: growth)
Nothing appears; everything GROWS. Lines draw themselves (stroke-dashoffset), nodes bloom (scale from 0.1 with a small glow pop), sections are connected by visible threads. Hovering a project pulses its connection threads — the network is alive.

## Architecture
- Canvas-2D background (NO WebGL): the mycelial network drawn on one canvas — nodes + quadratic bezier connections. Pre-rendered glow sprite for node halos (offscreen canvas once). Particle pool: 90 spores drifting. DPR cap 1.5.
- The network GROWS with scroll: each section's node spawns 2–3 hyphae to the next section's nodes as it enters the viewport; connections animate via dashoffset.
- Fonts: "Fraunces" (display, soft organic serif) + "Space Grotesk" (body). Palette: soil #0a0d08, mycelium cream #f2ead8, glow green #9be564, spore gold #ffd166, ink #10150c, faint #d8e8c8.
- Prefix ALL new classes `my-`.

## Sections (all MVP + genesis data)
1. **Hero** — name "Garvit Pandia" in Fraunces with a growing underline (a hypha that draws itself under the name on load); subtitle "Systems that think, worlds that react"; 6 stats as glowing nodes connected to the name by thin threads (pick 6 verbatim).
2. **About** — bio paragraph + core testimonials as "spore notes" (small cards with dotted borders). Genesis testimonial from the GSoC mentor included.
3. **Projects** — at least 6: 3 core (RAG Resume Analyzer, PulseSync, Drift) + 3 genesis (Helios, Relay, Epoch). Each project = a fruiting body card: name, one-liner, metric line verbatim, star count; hover = threads from the card to its siblings pulse (CSS class toggle, no canvas redraw per hover — a fixed set of connection elements).
4. **Achievements** — 11 total (7 core + 4 genesis) as spores: small round badges with mono index, staggered bloom reveal (scale 0.1→1, 350ms, 60ms stagger).
5. **Experience + skills** — 5 entries as growth rings (left border line that extends with reveal); skills = 4 enzyme groups with bar = mycelial density (soft radial-gradient bars, width animated on reveal, transform-only).
6. **Ratings strip** — genesis ratings as glowing chips with tiny spore dots.
7. **Contact** — form (mailto fallback) + direct links; framed as "drop a seed".

## Mandatory perf rules
DPR cap 1.5 · particle pool capped (90) · pre-rendered glow sprites (no per-frame shadowBlur) · rAF pauses on hidden/offscreen · transform/opacity-only · passive listeners · prefers-reduced-motion: one static frame, no drift, reveals opacity-only, no dashoffset animations.

## MVP checklist (MUST all be present)
Contact form with mailto fallback · Download resume button linking `./Garvit_Pandia_Resume.pdf` (file already in your folder) · scroll reveals + `scroll-behavior:smooth` · animated canvas hero · 44px tap targets · mobile responsive · `<noscript>` un-hide fallback.

## Verification (file-tools only)
`node --check` every script block (extract to /tmp first), brace-balance style blocks, grep duplicate `id=`, each `my-` class defined once + used, PDF link exactly `./Garvit_Pandia_Resume.pdf`. Report line count + all check results.
