# Garvit Pandia — The Material Index

Six concept websites, each for a different kind of business and each built in its own
visual style. The businesses are invented. The websites are real: every one has a
working feature you can use, not just a layout to look at.

The repo root `index.html` is the **Material Index**, a gallery that shows the six as
animated cards. A card shows a screenshot at rest, loads the live site when you hover
it, and opens the site when you click.

> **Live:** <https://garvit-pandia.github.io/p/> (GitHub Pages, served from `main`).
> The six concept sites are on the `concept-sites` branch and are not live yet; the
> live site still shows the older set of fourteen portfolio experiments.

I built this to show range: the same person designing and building a hotel site, a
theatre site, a shop, a type foundry, a dive school and a software product page, with
no shared code between them.

## The six sites

| Folder | Business | Style | The thing that works |
|--------|----------|-------|----------------------|
| `v13-origami-aurum/` | **Kaagaz Haveli** — a twelve-room heritage hotel in Udaipur | Light. Folded paper, parchment and gold foil, sections that unfold in CSS 3D. No canvas. | Stay calculator: pick a room, dates and guests and it prices the stay. |
| `v16-black-box/` | **Saanjh Repertory** — an 84-seat black-box theatre in Chandigarh | Dark. Matte black stage, bone serif, theatre-red cue marks, a moving spotlight. | Seat map: pick a show, pick your seats, see the total. |
| `v5-glass/` | **Kanch Invoicing** — invoicing software for small businesses | Dark. Glass panels, Three.js prisms, product screens drawn in CSS. | Pricing slider with a monthly / yearly switch that picks the plan for you. |
| `v12-mycelium/` | **Dhingri & Co.** — a gourmet mushroom farm in Solan | Dark. A fungal network on canvas that grows as you scroll. | Shop with a basket: quantities, delivery fee, total, remembered between visits. |
| `v10-typevolt/` | **Typevolt** — an independent type foundry | Light. Kinetic type in pure DOM and CSS, letters that move with the scroll. | Type tester: set your own words in any of eight families, change size and weight. |
| `v8-abyss/` | **Paatal Dive Co.** — a dive school in the Andaman Islands | Dark. A living sea on one canvas, a depth rail from 0 to 40 m. | Depth finder: drag to a depth and see what lives there and which course gets you to it. |

Each site carries one line in its footer saying the business is fictional and that I
designed and built the site, with a link to <https://garvitpandia.me> and a link back
to the gallery. That line is the only place my own details appear on a concept site.

## How to preview

```bash
cd ~/projects2/portfolio-gallery
python3 -m http.server 5186
# open http://localhost:5186
```

No build step and nothing to install. Pages also open straight from `file://`.
Internet is needed for Google Fonts and, for `v5-glass`, Three.js from the CDN.

## What every site has

- An animated hero and scroll reveals in its own style
- One interactive feature (table above) that works without a backend
- A contact or enquiry form that confirms on the page. Nothing is sent anywhere, and
  the form says so.
- Fictional contact details on the `.example` domain, so no real business or inbox is
  ever pointed at
- `prefers-reduced-motion` support, a phone layout, and visible keyboard focus
- Animations that pause when the tab is hidden or the canvas is off screen

## Also in the repo

| Folder | What it is |
|--------|------------|
| `v1-light/` … `v4-brutalist/`, `v6-scrollstory/`, `v7-voxel/`, `v9-ghostware/`, `v11-event-horizon/`, `v14-signal/`, `v15-transit-map/`, `v17-strata/`, `v18-optical-bench/` | Twelve older portfolio experiments. Not linked from the gallery on this branch. They still carry placeholder career copy and are waiting to be rebuilt as concept sites or removed. |
| `shots/` | Card screenshots (1280×800) the gallery shows at rest. |
| `docs/content-rules.md` | What a concept site may and may not say. Read this before writing copy. |
| `HANDOFF.md`, `STATUS.md` | Current state, and the running log. |
| `docs/` (everything else), `parts/` | Old build briefs and leftover fragments. Nothing at runtime reads them. |

## Quality checks

Every site and the gallery were loaded in a real browser at 1280 and 390 px wide:
no console errors, no sideways scroll, and the feature used end to end (seats picked,
basket filled, slider dragged, form submitted).

## Tech

- Plain HTML, CSS and JavaScript. No framework, no build tools, no dependencies to install.
- Each site is a single self-contained `index.html`.
- Canvas 2D for the sea (`v8`) and the fungal network (`v12`); Three.js r160 from the
  CDN for the glass prisms (`v5`); pure DOM and CSS for the rest.
- Google Fonts. No stock photography: everything on the six sites is drawn in code.
