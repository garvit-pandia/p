# BRIEF — V7 VOXELWORLD "Isometric Diorama" (three.js)

Build ONE standalone portfolio: `/home/garvit/projects/portfolio5/variant-7-voxel/index.html`

FIRST read `/home/garvit/projects/portfolio5/docs/fictional-resume-data.md` — it is the ONLY
allowed content source. Use its data verbatim (numbers, names, links). Everything in the
HTML/CSS/JS you write is yours to design.

## Concept
A tiny isometric voxel world built in three.js. Each page section is its own voxel island:
About = lighthouse island · Projects = city skyline · Skills = skill tree · Achievements =
trophy mesa · Experience = railway island (train circling) · Contact = beacon tower.
The hero is a big voxel-letter "GARVIT" monument. Scroll progress flies the camera along a
smooth path from island to island (camera lerps toward a target position per scroll depth;
when a section scrolls into view, its island glows/activates). Floating DOM labels hover
over each island via CSS transform tied to scroll. Clicking a label smooth-scrolls to that
section. Subtle day→night gradient shift across the page (scroll-driven, cheap: change
scene background + fog color + sun color).

## Visual language
- Palette: day sky #8ec9f2→#cfe8f7, grass #67c96f, dirt #b07a4f, water #3aa7e0, night #0b1b3f
  + warm window-glow #ffd97a. Accent for UI chrome: ink #12233f on translucent white panels.
- Fonts (Google Fonts): 'Sora' (display/UI) + 'JetBrains Mono' (labels/data). Sora 800 for
  big headings.
- UI: floating translucent "data plates" (white .12 panels, 1px white border, backdrop-blur
  12px, radius 18px, soft shadow) — island labels + section content cards look like
  inspection readouts from a drone. Mono uppercase micro-labels with a small square bullet.
- The theme MUST carry past the hero: every section card gets a voxel motif — e.g. corner
  brackets like a targeting HUD, a tiny canvas-free CSS voxel cube icon (isometric div
  stack) next to each section heading, section numbers as "ISLAND 0X".

## Architecture / perf (three.js r160 via jsdelivr import map, same pattern as:
`<script type="importmap">{"imports":{"three":"https://cdn.jsdelivr.net/npm/three@0.160.0/build/three.module.js"}}</script>`)
- One THREE.Scene on a `<canvas id="world">` fixed behind content (z-index -1, pointer-events
  none). Build all terrain from box geometries via THREE.InstancedMesh (one instance mesh
  per island = few draw calls). Simple vertex-colored or MeshLambertMaterial meshes; NO
  shadow maps — fake shadows with flat dark translucent circles under objects.
- Camera path: define 6 target [position, lookAt] keyframes (one per island, generous
  spacing along -x or +z); scroll progress p ∈ [0,1] maps to path index = p*(N-1); lerp
  camera position/lookAt with exponential smoothing (time-based, not frame-based: use
  clock delta, factor 1 - Math.pow(0.001, dt) style).
- Animated bits (cheap): slowly rotating windmill on the lighthouse island, orbiting sun
  cube, beacon light = rotating cylinder + additive glow sprite on contact island, a few
  emissive window boxes that pulse in the city (randomize via a tiny JS loop over ~40
  instances, update only their color), train = small box group moving on a circular track.
- Renderer: `renderer.setPixelRatio(Math.min(devicePixelRatio, 1.5))`, antialias true,
  `powerPreference:'high-performance'`, fog enabled (fog color matches sky). Pause the
  rAF loop on `document.hidden` and when the canvas is off-screen (IntersectionObserver).
- Wrap ALL three.js init in try/catch: if WebGL fails or `prefers-reduced-motion`, hide the
  canvas and show a static CSS gradient sky (page must still be complete and beautiful).
- Reduced motion: skip camera animation (jump straight to final frame per scroll), no
  ambient spins.

## Content & required features (checklist — all MUST exist)
1. Hero: voxel monument "GARVIT" (instanced boxes forming letters) + DOM overlay with big
   display heading, title, CTA buttons ("Explore the world" scrolls to about; "Get resume"
   links to local Garvit_Pandia_Resume.pdf).
2. Sections (each = island + DOM section): About (short bio from data + stats strip),
   Projects (6–8 cards, each: name, one-line, stack chips, metric in mono — all verbatim),
   Skills (4 groups, level bars 0–100 verbatim), Achievements (list with year/label),
   Experience (3 roles with bullets), Contact (form name/email/message → mailto: fallback;
   direct links: email, phone, GitHub, LinkedIn, site).
3. Download resume button → `/variant-7-voxel/Garvit_Pandia_Resume.pdf` (file already copied
   into your folder by the controller — just link it).
4. Scroll-triggered reveals (IntersectionObserver adding a class; transform+opacity only),
   smooth scrolling (`scroll-behavior:smooth` + `scroll-padding-top`).
5. Sticky top nav (island names) that highlights the active section (IO), 44px hit targets,
   mobile responsive at 760px (canvas still fixed; DOM stacks; labels shrink).
6. Footer: name, "built with three.js — no images, no tracking", year 2026, links.
7. `prefers-reduced-motion` respected. Inline SVG favicon. Zero external images (everything
   code-drawn). Zero console errors.

## Write + verify (file tools only, no browser, no server)
- Write the whole file in ONE `write_file` call (aim 1100–1500 lines). Keep it valid:
  balanced tags, every `<script>` closed, CSS braces balanced.
- Extract JS and syntax-check: create a script file `/tmp/v7check.py` with this EXACT
  content, then run `python3 /tmp/v7check.py`:
```python
import re
html = open('/home/garvit/projects/portfolio5/variant-7-voxel/index.html').read()
blocks = re.findall(r'<script(?![^>]*importmap)[^>]*>(.*?)</script>', html, re.S)
for i, b in enumerate(blocks):
    open('/tmp/v7_%d.js' % i, 'w').write(b)
print('blocks:', len(blocks))
```
  Then run `node --check /tmp/v7_0.js` (and each index) — fix anything that fails and
  rewrite the file. Also `grep -c '<script'` vs `grep -c '</script>'` must be equal.
- Do NOT open a browser, do NOT start a server, do NOT use rm. Do not use `-c` flags or
  `-e` flags in shell commands (use heredocs/files as shown).

## Report back
Path, total line count, script block count, node --check results, list of sections built,
the camera path keyframe positions, and anything you intentionally left simplified.
