# Museum Portfolio Index Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the root link list with a light-mode museum catalogue that showcases fourteen distinct portfolio worlds through custom preview scenes before visitors open them.

**Architecture:** Keep the project zero-build and dependency-free. `index.html` will own one normalized exhibit data array, render the collection and preview stages, and provide client-side filtering; the existing `v1`–`v14` pages remain untouched. CSS will provide the museum shell plus fourteen lightweight DOM/CSS preview compositions, with motion isolated to transform/opacity and disabled for reduced-motion users.

**Tech Stack:** Static HTML, CSS, and vanilla JavaScript; Python `http.server` for local verification; existing relative child-page links.

---

## File Map

- Modify: `index.html` — replace the current root page markup, styles, exhibit data, preview scenes, filters, and interaction logic.
- Create: no runtime assets or dependencies; previews are CSS/DOM compositions.
- Verify: `v1-light/index.html` through `v14-signal/index.html` — route targets only, no edits.

## Task 1: Build The Museum Collection Shell

**Files:**
- Modify: `index.html:1-152`

- [ ] **Step 1: Capture the existing route inventory before editing**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
from html.parser import HTMLParser

class Links(HTMLParser):
    def __init__(self):
        super().__init__()
        self.hrefs = []
    def handle_starttag(self, tag, attrs):
        if tag == "a":
            href = dict(attrs).get("href")
            if href:
                self.hrefs.append(href)

parser = Links()
parser.feed(Path("index.html").read_text())
print("\n".join(parser.hrefs))
PY
```

Expected: the fourteen existing variant links are printed, from `v1-light/index.html` through `v14-signal/index.html`, plus no external child-page route.

- [ ] **Step 2: Replace the document shell with semantic museum sections**

Use this structure inside `body`:

```html
<header class="masthead">
  <div class="masthead__identity">
    <p class="eyebrow">Garvit Pandia / digital worlds</p>
    <h1>Fourteen ways to make a digital world.</h1>
    <p class="masthead__intro">A collection of portfolios exploring code, atmosphere, motion, systems, and play.</p>
  </div>
  <p class="collection-count"><strong>14</strong> exhibits</p>
</header>
<nav class="filters" aria-label="Filter exhibits">
  <button type="button" class="filter is-active" data-filter="all" aria-pressed="true">All</button>
  <button type="button" class="filter" data-filter="light" aria-pressed="false">Light</button>
  <button type="button" class="filter" data-filter="dark" aria-pressed="false">Dark</button>
  <button type="button" class="filter" data-filter="3d" aria-pressed="false">3D</button>
  <button type="button" class="filter" data-filter="motion" aria-pressed="false">Motion</button>
</nav>
<main id="collection" class="collection" aria-live="polite"></main>
<footer class="catalogue-footer">Fourteen exhibits, one restless practice. Built with HTML / CSS / JS.</footer>
```

The `main` starts with the opening exhibit in the larger grid position and all remaining exhibits in the same collection flow. Do not use nested anchors: each rendered exhibit is one `<a class="exhibit" href="...">` containing its preview and action label as non-interactive text.

- [ ] **Step 3: Add the normalized exhibit data array**

Create one `exhibits` array before the render function. Keep descriptions faithful to the current root inventory while tightening them for the museum catalogue, and use these filter memberships:

```js
const exhibits = [
  { number: "01", slug: "v1-light", title: "Sunlit Archive", category: "Light / Editorial", filters: ["light"], previewClass: "archive", description: "Warm editorial light theme with paper petals, developing photographs, stamps, and handwritten archive notes.", href: "v1-light/index.html" },
  { number: "02", slug: "v2-dark", title: "Midnight Index", category: "Dark / Cosmic", filters: ["dark"], previewClass: "constellation", description: "A deep-space career map with starfield drift, orbiting rings, constellations, and a self-typing terminal.", href: "v2-dark/index.html" },
  { number: "03", slug: "v3-wild", title: "Dream Loom", category: "Wild / Fluid", filters: ["motion"], previewClass: "loom", description: "A living aurora, kinetic type, silk threads, and a dream palette that shifts while you explore.", href: "v3-wild/index.html" },
  { number: "04", slug: "v4-brutalist", title: "Mono Factory", category: "Brutalist / Mono", filters: ["motion"], previewClass: "factory", description: "A mechanical portfolio of hard borders, terminal commands, receipts, and typewriter precision.", href: "v4-brutalist/index.html" },
  { number: "05", slug: "v5-glass", title: "Glass Horizon", category: "Glass / Luminous", filters: ["3d"], previewClass: "prism", description: "Light through glass: drifting orbs, refraction, prisms, frosted panels, and depth.", href: "v5-glass/index.html" },
  { number: "06", slug: "v6-scrollstory", title: "The Field Journal", category: "Scrollytelling / Editorial", filters: ["motion"], previewClass: "field-journal", description: "A scroll-driven field log with pinned scenes, specimen collecting, and a self-drawing timeline.", href: "v6-scrollstory/index.html" },
  { number: "07", slug: "v7-voxel", title: "Voxel World", category: "3D / Voxel", filters: ["3d"], previewClass: "voxel", description: "A tiny isometric world of islands, railways, beacons, and a camera that flies as you scroll.", href: "v7-voxel/index.html" },
  { number: "08", slug: "v8-abyss", title: "The Abyss", category: "Dark / Bioluminescent", filters: ["dark"], previewClass: "abyss", description: "A deep-sea dive through glowing specimen jars, sonar pings, pressure, and light rays.", href: "v8-abyss/index.html" },
  { number: "09", slug: "v9-ghostware", title: "Ghostware", category: "Cyber / Hologram", filters: ["dark"], previewClass: "ghostware", description: "A holographic memory archive with scanlines, telemetry, recall slots, and a command bar.", href: "v9-ghostware/index.html" },
  { number: "10", slug: "v10-typevolt", title: "Typevolt", category: "Editorial / Kinetic", filters: ["motion"], previewClass: "typevolt", description: "A kinetic editorial machine where letters stretch, respond, and choreograph the work.", href: "v10-typevolt/index.html" },
  { number: "11", slug: "v11-event-horizon", title: "Event Horizon", category: "Dark / Cosmic", filters: ["dark"], previewClass: "horizon", description: "A black-hole portfolio where scroll becomes descent through rings of an accretion disk.", href: "v11-event-horizon/index.html" },
  { number: "12", slug: "v12-mycelium", title: "Mycelium", category: "Dark / Organic", filters: ["dark"], previewClass: "mycelium", description: "A living fungal network where projects fruit, skills branch, and everything grows into view.", href: "v12-mycelium/index.html" },
  { number: "13", slug: "v13-origami-aurum", title: "Origami Aurum", category: "Light / Paper", filters: ["light"], previewClass: "origami", description: "A warm paper gallery of folded letters, dog-eared projects, gold foil, and unfolding sections.", href: "v13-origami-aurum/index.html" },
  { number: "14", slug: "v14-signal", title: "SIGNAL//DECODE", category: "Dark / Radio", filters: ["dark"], previewClass: "signal", description: "An intercepted transmission with static, spectrograms, decoded stamps, and a channel back out.", href: "v14-signal/index.html" }
];
```

The `filters` values deliberately describe the dominant concept, not every animation used by a child page. This keeps `Motion` useful instead of matching all fourteen animated sites.

- [ ] **Step 4: Render cards from the array**

Implement `renderExhibits(filter = "all")` so the data remains the single source of truth:

```js
function renderExhibits(filter = "all") {
  collection.innerHTML = exhibits
    .filter((exhibit) => filter === "all" || exhibit.filters.includes(filter))
    .map((exhibit, index) => `
      <a class="exhibit exhibit--${exhibit.previewClass} ${index === 0 ? "exhibit--opening" : ""}" data-slug="${exhibit.slug}" href="${exhibit.href}" style="--index:${index}">
        <div class="exhibit__preview" aria-hidden="true">${previewMarkup(exhibit.previewClass)}</div>
        <div class="exhibit__placard">
          <span class="exhibit__number">${exhibit.number}</span>
          <span class="exhibit__category">${exhibit.category}</span>
        </div>
        <h2>${exhibit.title}</h2>
        <p>${exhibit.description}</p>
        <span class="exhibit__action">Enter exhibit <span aria-hidden="true">↗</span></span>
      </a>
    `)
    .join("");
}
```

Call `renderExhibits()` once after the data is declared. Use only static developer-authored strings in the array; no user input is interpolated.

## Task 2: Implement The Light Museum Visual System

**Files:**
- Modify: `index.html` `<style>` block

- [ ] **Step 1: Define shell tokens and base rules**

Replace the existing warm card-grid tokens with one light museum system:

```css
:root {
  --paper: #f3f1ea;
  --surface: #fffdf8;
  --ink: #272a25;
  --muted: #697168;
  --line: #d9d6cb;
  --accent: #bf684f;
  --radius: 3px;
  --ease: cubic-bezier(.16, 1, .3, 1);
}
```

Use the page background on `body`, a centered `max-width` container, serif display headings, sans body copy, and monospace metadata. Keep body text at or above 16px on mobile. Add `:focus-visible` outlines with the accent color and never remove the native keyboard path.

- [ ] **Step 2: Style the masthead and filters**

Use a split desktop masthead with left-aligned thesis copy and a right-side `14 exhibits` marker. Keep desktop navigation/filter controls on one line where space permits. On screens below 768px, stack the masthead and let filter buttons wrap with at least 8px gaps.

The active filter uses graphite fill with readable light text; inactive filters use the page background with a visible border. Every filter button must retain a 44px minimum touch height.

- [ ] **Step 3: Create the gallery layout**

Use CSS Grid rather than percentage-based flex math:

```css
.collection {
  display: grid;
  grid-template-columns: repeat(12, minmax(0, 1fr));
  gap: 18px;
}
.exhibit { grid-column: span 4; }
.exhibit--opening { grid-column: span 8; }
@media (max-width: 960px) {
  .exhibit, .exhibit--opening { grid-column: span 6; }
}
@media (max-width: 700px) {
  .collection { grid-template-columns: 1fr; }
  .exhibit, .exhibit--opening { grid-column: auto; }
}
```

Keep one card radius, one border weight, and one shadow language. The opening exhibit gets a taller preview and a larger title; no blank grid cells are left behind.

- [ ] **Step 4: Add the fourteen preview compositions**

Implement `previewMarkup(previewClass)` with small, semantic-free decorative primitives inside an `aria-hidden` wrapper. Each preview must be legible at rest and visibly different from the others:

| Class | Required visual primitives |
|---|---|
| `archive` | paper panel, photo block, circular stamp |
| `constellation` | light specimen card, orbit ring, star points |
| `loom` | 3 overlapping woven bands, soft blob |
| `factory` | black rule grid, lime label, block cursor |
| `prism` | two translucent planes, edge highlight |
| `field-journal` | specimen ticket, route line, pressed dot |
| `voxel` | three stepped isometric blocks, beacon square |
| `abyss` | blue specimen well, glow dot, depth ticks |
| `ghostware` | scan frame, serial text, hologram bars |
| `typevolt` | oversized split word, rule, offset letter |
| `horizon` | three elliptical rings, central dark point |
| `mycelium` | branch lines, green nodes, fruiting circle |
| `origami` | folded quadrilateral, crease line, gold marker |
| `signal` | waveform strip, frequency bars, decoded stamp |

Use CSS gradients, borders, `clip-path`, and pseudo-elements instead of external images or SVG illustrations. Keep each scene isolated under `.exhibit--<previewClass>` so selectors cannot leak between previews.

- [ ] **Step 5: Add hover, focus, and reduced-motion states**

Animate only `transform`, `opacity`, and non-layout visual properties. The default card state must already communicate its exhibit. Use a 2–4px lift on hover/focus and reveal the preview’s secondary cue with opacity. Add:

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: .01ms !important;
    animation-iteration-count: 1 !important;
    scroll-behavior: auto !important;
    transition-duration: .01ms !important;
  }
}
```

Do not add a custom cursor, scroll hijack, perpetual marquee, or full-page dark transition.

## Task 3: Add Filtering And Resilience

**Files:**
- Modify: `index.html` page script

- [ ] **Step 1: Wire filter button state**

Add one click listener to `.filters` using event delegation. For the clicked filter:

```js
filters.addEventListener("click", (event) => {
  const button = event.target.closest("button[data-filter]");
  if (!button) return;
  const filter = button.dataset.filter;
  document.querySelectorAll(".filter").forEach((item) => {
    const selected = item === button;
    item.classList.toggle("is-active", selected);
    item.setAttribute("aria-pressed", String(selected));
  });
  renderExhibits(filter);
});
```

Do not change the URL or scroll position when filtering. `All` must restore all fourteen exhibits and preserve the opening-exhibit treatment.

- [ ] **Step 2: Preserve the no-JavaScript fallback**

Because this is a static page and the collection is rendered from the JavaScript data array, add a `<noscript>` block immediately after `#collection` with direct links to every variant:

```html
<noscript>
  <p>JavaScript is disabled. Open an exhibit directly:</p>
  <ul>
    <li><a href="v1-light/index.html">Sunlit Archive</a></li>
    <li><a href="v2-dark/index.html">Midnight Index</a></li>
    <li><a href="v3-wild/index.html">Dream Loom</a></li>
    <li><a href="v4-brutalist/index.html">Mono Factory</a></li>
    <li><a href="v5-glass/index.html">Glass Horizon</a></li>
    <li><a href="v6-scrollstory/index.html">The Field Journal</a></li>
    <li><a href="v7-voxel/index.html">Voxel World</a></li>
    <li><a href="v8-abyss/index.html">The Abyss</a></li>
    <li><a href="v9-ghostware/index.html">Ghostware</a></li>
    <li><a href="v10-typevolt/index.html">Typevolt</a></li>
    <li><a href="v11-event-horizon/index.html">Event Horizon</a></li>
    <li><a href="v12-mycelium/index.html">Mycelium</a></li>
    <li><a href="v13-origami-aurum/index.html">Origami Aurum</a></li>
    <li><a href="v14-signal/index.html">SIGNAL//DECODE</a></li>
  </ul>
</noscript>
```

- [ ] **Step 3: Add interaction and accessibility checks in source**

Confirm each card is a real `<a>` with a descriptive title and action text, each preview is `aria-hidden="true"`, and each filter has `aria-pressed`. Keep focus outlines visible against both the paper background and exhibit preview surfaces.

## Task 4: Verify The Root Index End To End

**Files:**
- Verify: `index.html` and all fourteen child `index.html` files

- [ ] **Step 1: Run static syntax and route checks**

Run:

```bash
python3 - <<'PY'
from pathlib import Path
from html.parser import HTMLParser

class Links(HTMLParser):
    def __init__(self):
        super().__init__()
        self.hrefs = []
    def handle_starttag(self, tag, attrs):
        if tag == "a":
            href = dict(attrs).get("href")
            if href and href.startswith("v"):
                self.hrefs.append(href)

parser = Links()
parser.feed(Path("index.html").read_text())
assert len(parser.hrefs) == 14, parser.hrefs
assert all(Path(href).is_file() for href in parser.hrefs), parser.hrefs
assert len(set(parser.hrefs)) == 14
print("14 unique exhibit routes verified")
PY
```

Expected: `14 unique exhibit routes verified`.

- [ ] **Step 2: Serve the repository and inspect the page in a browser**

Run:

```bash
python3 -m http.server 8892 --directory .
```

Open `http://127.0.0.1:8892/index.html` and verify:

- Desktop shows the light museum shell, masthead, filters, and opening exhibit without a giant empty hero.
- All fourteen cards show their custom preview before opening.
- `Light` shows 2 cards, `Dark` shows 6, `3D` shows 2, `Motion` shows 4, and `All` restores 14.
- Clicking an exhibit opens the correct existing child page.
- Browser console reports no errors.

- [ ] **Step 3: Check keyboard and responsive behavior**

In the browser:

- Tab from the page start through every filter and exhibit link; focus remains visible and order follows the gallery.
- At 390px width, the page is single-column with no horizontal overflow and filters remain usable.
- At tablet width, the grid is two columns and preview text does not overlap.
- Enable reduced motion and confirm preview animations become static.

- [ ] **Step 4: Perform the final visual audit**

Compare the implemented page against `docs/superpowers/specs/2026-08-11-museum-portfolio-index-design.md`. Remove any preview that reads as a generic colored rectangle, any duplicated CTA intent, and any shell element that competes with the exhibit collection. Record only verified issues; do not modify the child portfolio pages.

## Plan Self-Review

- Spec coverage: masthead, one complete collection, filters, light museum palette, fourteen preview cues, accessible links, reduced motion, no-JS fallback, responsive layout, route checks, and browser verification are all covered above.
- Completeness scan: no `TBD`, `TODO`, fake API, or unspecified asset task remains in the implementation steps.
- Type consistency: the data properties `number`, `slug`, `title`, `category`, `filters`, `previewClass`, `description`, and `href` are used consistently by `renderExhibits()` and the filter listener.
- Scope: only `index.html` changes at runtime; existing child pages and dependencies remain outside the task.
