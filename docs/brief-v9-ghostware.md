# BRIEF — V9 GHOSTWARE "Holographic Archive" (canvas particle hologram)

Build ONE standalone portfolio: `/home/garvit/projects/portfolio5/variant-9-ghostware/index.html`

FIRST read `/home/garvit/projects/portfolio5/docs/fictional-resume-data.md` — it is the ONLY
allowed content source. Use its data verbatim (numbers, names, links). Everything in the
HTML/CSS/JS you write is yours to design.

## Concept
The site is a memory archive of a digital ghost: Garvit's holographic self. A fixed canvas
renders a slowly rotating hologram — an abstract wireframe "bust" built from glowing points
+ a sparse web of lines (like a point-cloud portrait, not a face — abstract is fine: a
sphere-ish head volume + shoulders, 900–1500 points, some lines between near neighbors).
Around it: faint falling data-stream glyphs (only in the hero area of the canvas, low
density). The DOM is the archive UI: a top status bar ("GHOSTWARE v7.3 — MEMORY ARCHIVE //
SUBJECT: GARVIT PANDIA") with fake telemetry (SYS INTEGRITY 98.2%, MEM LOAD, FRAME RATE)
that updates every 600ms (not per frame). Content cards are "MEMORY SLOTS" with serials
ARCH-0001…, and clicking one "loads" it: a 160ms CSS glitch (clip-path slices + hue shift +
brief static noise via a pseudo-element) before the card settles open. Nav is an
"ACCESS://" command bar. Hovering the hologram tilts it (pointer-fine only). A faint
scanline overlay + subtle chromatic-aberration text treatment on headings.

## Visual language
- Palette: void #050508, panel #0b0b14, hologram cyan #7ff5ff, violet #b388ff, magenta
  glitch #ff3d81, amber warn #ffc24b, text #e8f6ff / dim #8a93b8.
- Fonts (Google Fonts): 'Chakra Petch' (600/700 — techno/holo) + 'IBM Plex Mono'
  (400/500 — all data, serials, captions).
- UI: panels = 1px rgba(127,245,255,.18) border, rgba(11,11,20,.8) fill, radius 8px (sharp,
  technical — not rounded-soft), corner tick marks (4 tiny L-brackets per card, via
  ::before/::after or a wrapper), mono uppercase labels with `▮` cursor blocks. Section
  headings = "QUERY: IDENTITY" / "QUERY: WORK" / "QUERY: CAPABILITY" / "QUERY: PROOF" /
  "QUERY: CONTACT". Card hover: border glows cyan + translateY(-2px).
- Theme carries past the hero: serial numbers on every card, telemetry bar stays fixed at
  top (or bottom), scanlines overlay the whole page (fixed, pointer-events none, CSS
  repeating-linear-gradient at 3% opacity — cheap), every reveal = "boot-in" (fade +
  translateY + slight blur→0, 500ms).

## Interactions
- Hologram: canvas draws points on a wireframe bust (precompute 3D points on a sphere +
  cone-ish shoulders; rotate slowly; project with a tiny manual perspective — NO three.js,
  plain 2D canvas + math). Lines: only a fixed subset (e.g. 140 pairs) redrawn each frame
  at low alpha — or pre-render rings. Pointer tilt: rotate the whole point cloud ±0.15 rad
  toward the cursor, lerped. Clicking the hologram = "EXECUTE RECALL": a cyan pulse ring
  + the hero name types itself again.
- Memory slots: clicking a card adds `.glitching` for 160ms (clip-path polygon slices via
  keyframes + a ::after static-noise layer with a few box-shadows) then expands the card's
  hidden detail (max-height transition).
- Telemetry: setInterval 600ms, randomizes MEM LOAD 61–79%, FRAME RATE 58–61 (it's a
  portfolio — keep the lie subtle), SYS INTEGRITY drifts 98.1–98.4%. Respect
  prefers-reduced-motion: stop the interval drift, render hologram once, no glitch anims.
- Performance: 2D canvas, `Math.min(devicePixelRatio,1.5)`, alpha:false; points drawn as
  fillRect/arc into a pre-rendered glow sprite via drawImage (NO shadowBlur per frame);
  pause rAF on document.hidden; data-stream glyphs only drawn in the top 60% of the canvas
  and capped at ~60 glyphs; passive listeners only.

## Content & required features (checklist — ALL must exist)
1. Hero: the hologram canvas + DOM overlay: "MEMORY ARCHIVE // SUBJECT 001", huge name
   (Chakra Petch 700, chromatic-aberration via 2 text-shadows), role title, stats strip
   (mono, from data), CTAs: "ACCESS://identity" (scroll to about) + "EXTRACT RESUME"
   (→ local Garvit_Pandia_Resume.pdf in your folder; controller copies it — just link it).
2. About, Projects (6–8 ARCH-serial cards, each with name/one-line/stack chips/metric —
   verbatim data), Skills (4 groups as "CAPABILITY MATRICES" with bars 0–100), Achievements
   ("PROOF LOG", all 7 verbatim), Experience (3 "DEPLOYMENTS" with bullets), Contact
   ("QUERY: CONTACT" — mailto-fallback form + direct links: email, phone, GitHub,
   LinkedIn, site).
3. Download resume button; contact form mailto fallback; smooth scrolling + scroll-padding;
   scroll reveals (IO, boot-in); sticky ACCESS:// nav with active state; 44px targets;
   responsive ≤760px (hologram shrinks/scales down or hides behind content, telemetry bar
   simplifies, cards stack).
4. Footer: name, "GHOSTWARE v7.3 — zero images, zero tracking", 2026, links.
5. Inline SVG favicon (cyan circle w/ scanline). Zero external images. Zero console errors.

## Write + verify (file tools only, no browser, no server)
- Write the whole file in ONE `write_file` call (aim 1100–1500 lines). Valid HTML: balanced
  tags, every script closed, CSS braces balanced.
- Extract + syntax check: create `/tmp/v9check.py` with this EXACT content, run
  `python3 /tmp/v9check.py`:
```python
import re
html = open('/home/garvit/projects/portfolio5/variant-9-ghostware/index.html').read()
blocks = re.findall(r'<script(?![^>]*importmap)[^>]*>(.*?)</script>', html, re.S)
for i, b in enumerate(blocks):
    open('/tmp/v9_%d.js' % i, 'w').write(b)
print('blocks:', len(blocks))
```
  Then `node --check /tmp/v9_0.js` (and each index) — fix failures and rewrite the file.
  `grep -c '<script'` must equal `grep -c '</script>'`.
- Do NOT open a browser, do NOT start a server, do NOT use rm. Do not use `-c`/`-e` shell
  flags (use heredocs/files as shown).

## Report back
Path, line count, script blocks, node --check results, sections built, hologram point
count, telemetry cadence, anything intentionally simplified.
