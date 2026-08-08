# BRIEF — V8 ABYSS "Bioluminescent Deep Sea" (canvas 2D)

Build ONE standalone portfolio: `/home/garvit/projects/portfolio5/variant-8-abyss/index.html`

FIRST read `/home/garvit/projects/portfolio5/docs/fictional-resume-data.md` — it is the ONLY
allowed content source. Use its data verbatim (numbers, names, links). Everything in the
HTML/CSS/JS you write is yours to design.

## Concept
You are diving through Garvit's career as if it were the deep sea. Fixed full-screen canvas
background (2D, no WebGL): faint light rays from the surface, drifting bioluminescent
plankton, 3–5 undulating jellyfish (bezier ribbons with glow), rising bubbles, and sonar
ping rings that fire whenever a section scrolls into view. A fixed depth-meter rail on the
right shows "descent depth": scroll progress mapped 0 m → 11,204 m (the Challenger Deep —
contact section lands at "HADAL ZONE — the bottom, where you resurface"). Section themes:
Hero = SURFACE · About = DIVER PROFILE · Projects = SPECIMENS (project cards are glowing
sample jars) · Skills = CREW (bioluminescent organism chips) · Achievements = DEPTH RECORDS
(each achievement shows depth + pressure in atmospheres) · Experience = DESCENT TIMELINE
(vertical sonar line with blips) · Contact = RESURFACE (button "Send a buoy" → mailto).

## Visual language
- Palette: abyss #020a14, deep #04162b, cyan glow #7df9ff, teal #2dd4bf, violet #a78bfa,
  gold #ffd97a (only for depth records/achievements), text #e6f6ff / dim #8fb3c9.
- Fonts (Google Fonts): 'Syne' (display, 700/800 — organic, slightly alien) + 'IBM Plex
  Mono' (labels, data, dive-log text).
- UI: content cards = dark glass "viewing ports" (rgba(4,22,43,.72), 1px rgba(125,249,255,.22)
  border, radius 16px, backdrop-blur 10px) with a tiny glow dot in the corner; section
  headings = mono dive-log captions like "LOG 003 — SPECIMENS" with a blinking cursor
  block; horizontal hairline rules that glow on reveal.
- Theme must carry past the hero: every card, chip, and timeline node gets a glow treatment;
  the depth rail persists the whole page.

## Interactions
- Sonar ping: on section enter (IntersectionObserver), draw 2 expanding rings at that
  section's vertical center (canvas, cheap: 2 arcs fading).
- Diving-light cursor: a fixed div with radial-gradient (subtle, ~300px) following the
  pointer with transform + slight lerp — ONLY on `(pointer:fine)`; on touch, skip it.
- Jellyfish gently pulse; plankton drift with slow sine paths; bubbles rise faster when
  the user scrolls (scroll velocity feeds the canvas).
- Project cards hover: card tilts 1–2°, glow intensifies, metric reads out in mono.
- Depth rail: fixed right edge (hidden ≤760px), shows "0m" top → "11,204m" bottom, a marker
  gliding with scroll, current depth readout; at the very bottom a tiny caption
  "CHALLENGER DEEP — the floor. Resurface to say hello."

## Performance (critical — this is a canvas-everything page)
- One 2D canvas, `Math.min(devicePixelRatio, 1.75)`, `alpha:false` (opaque fill each
  frame), all entities in object pools. NO `shadowBlur` in the rAF loop — pre-render 2–3
  glow sprites (radial gradients) to offscreen canvases once and drawImage them. Cap:
  ~320 plankton desktop / ~140 mobile; 5 jellyfish max; 40 bubbles.
- rAF loop pauses when `document.hidden` AND when the canvas leaves the viewport
  (IntersectionObserver). Scroll listeners passive; velocity read in the rAF loop, never
  in the listener.
- Animations in DOM are transform/opacity only. Reduced motion: static canvas (one
  painted frame, no loop) + no cursor light + no sonar.

## Content & required features (checklist — ALL must exist)
1. Hero: "SURFACE" dive-log styling, big display name (Syne 800), role title, stats strip
   (from data, mono numbers with glow), CTAs: "Begin the dive" (scroll to about) +
   "Download resume" (→ local Garvit_Pandia_Resume.pdf in your folder; controller copies
   it — just link it).
2. About, Projects (6–8 cards w/ metric + stack), Skills (4 groups, level bars),
   Achievements (with invented depth/pressure flavor but REAL achievement names — e.g.
   "SIH 2024 — depth 8,848 m · 1,086 atm"), Experience (3 roles), Contact (mailto form +
   direct links) — ALL data verbatim from the data file.
3. Download resume button; contact form with mailto: fallback; smooth scrolling +
   scroll-padding; scroll reveals (IO); sticky nav with active state; 44px targets;
   responsive ≤760px (rail hidden, canvas still fixed, cards stack).
4. Footer: name, "built with canvas — zero images, zero tracking", 2026, links.
5. Inline SVG favicon. Zero external images. Zero console errors.

## Write + verify (file tools only, no browser, no server)
- Write the whole file in ONE `write_file` call (aim 1100–1500 lines). Valid HTML: balanced
  tags, every script closed, CSS braces balanced.
- Extract + syntax check: create `/tmp/v8check.py` with this EXACT content, run
  `python3 /tmp/v8check.py`:
```python
import re
html = open('/home/garvit/projects/portfolio5/variant-8-abyss/index.html').read()
blocks = re.findall(r'<script(?![^>]*importmap)[^>]*>(.*?)</script>', html, re.S)
for i, b in enumerate(blocks):
    open('/tmp/v8_%d.js' % i, 'w').write(b)
print('blocks:', len(blocks))
```
  Then `node --check /tmp/v8_0.js` (and each index) — fix failures and rewrite the file.
  `grep -c '<script'` must equal `grep -c '</script>'`.
- Do NOT open a browser, do NOT start a server, do NOT use rm. Do not use `-c`/`-e` shell
  flags (use heredocs/files as shown).

## Report back
Path, line count, script blocks, node --check results, sections built, particle counts,
and anything intentionally simplified.
