# Garvit Pandia — The Material Index

Ten demo websites, each for a different kind of client and each built in its own
visual style: seven for businesses, three for people who work for themselves. The names
are invented. The websites are real: every one has a working feature you can use, not
just a layout to look at.

The repo root `index.html` is the **Material Index**, a gallery that shows them as
animated cards. A card shows a screenshot at rest, loads the live site when you hover
it, and opens the site when you click.

> **Live:** <https://garvit-pandia.github.io/p/> (GitHub Pages, served from `main`).
> The demo sites are on the `concept-sites` branch and are not on that address yet; it
> still shows the older set of fourteen portfolio experiments.
> **Preview of this branch:** <https://material-index.vercel.app>

I built this to show range to people who might want a site of their own: the same
person designing and building a hotel site, a theatre site, a shop, a software product
page, a photographer's portfolio, an architect's and a coach's, with no shared code
between them.

## The ten sites

| Folder | Business | Style | The thing that works |
|--------|----------|-------|----------------------|
| `v13-origami-aurum/` | **Kaagaz Haveli** — a twelve-room heritage hotel in Udaipur | Light. Folded paper, parchment and gold foil, sections that unfold in CSS 3D. No canvas. | Stay calculator: pick a room, dates and guests and it prices the stay. |
| `v16-black-box/` | **Saanjh Repertory** — an 84-seat black-box theatre in Chandigarh | Dark. Matte black stage, bone serif, theatre-red cue marks, a moving spotlight. | Seat map: pick a show, pick your seats, see the total. |
| `v5-glass/` | **Kanch Invoicing** — invoicing software for small businesses | Dark. Glass panels, Three.js prisms, product screens drawn in CSS. | Pricing slider with a monthly / yearly switch that picks the plan for you. |
| `v12-mycelium/` | **Dhingri & Co.** — a gourmet mushroom farm in Solan | Dark. A fungal network on canvas that grows as you scroll. | Shop with a basket: quantities, delivery fee, total, remembered between visits. |
| `v10-typevolt/` | **Typevolt** — an independent type foundry | Light. Kinetic type in pure DOM and CSS, letters that move with the scroll. | Type tester: set your own words in any of eight families, change size and weight. |
| `v8-abyss/` | **Paatal Dive Co.** — a dive school in the Andaman Islands | Dark. A living sea on one canvas, a depth rail from 0 to 40 m. | Depth finder: drag to a depth and see what lives there and which course gets you to it. |
| `v19-photographer/` | **Meera Kapoor** — a wedding photographer | Light. Ivory paper and large serif type, laid out like a printed album. | Photo wall with filters and a full-screen viewer, and a calendar that says whether a date is free. |
| `v20-architect/` | **Arjun Sethi Architects** — an architecture studio | White. A strict grid, thin lines, drawings that draw themselves, one orange accent. | Project browser: filter, sort, grid or index view, and a sheet per project with a generated plan. Plus a time and fee estimate. |
| `v21-fitness-coach/` | **Kabir Anand** — a strength coach | Dark and loud. Near-black, acid lime, huge condensed type. | Three-question plan finder with a price, and a weekly timetable where you hold a place in a class. |
| `v22-clinic/` | **Hitesh Clinic** — a neighbourhood chemist with its own lab and doctor's room, in Indore | Light. Warm paper, pharmacy green and coral, capsule-shaped photographs, a drifting hero and a heartbeat line. | Test slip: search 24 tests, add single tests or a package, choose walk-in or home collection, and it works out the price, the fasting rule, the free times and when the report is ready. Plus a sample tracker, a tablet-strip calculator and a live doctors' timetable. |

Each site carries one small line at the very bottom saying the business or person is
fictional and that I designed and built the site, with a link to <https://garvitpandia.me> and a link back
to the gallery. That line is the only place my own details appear on a concept site.

## How to preview

```bash
cd ~/projects2/portfolio-gallery
python3 -m http.server 5186
# open http://localhost:5186
```

No build step and nothing to install. Pages also open straight from `file://`.
Internet is needed for Google Fonts and, for `v5-glass`, Three.js from the CDN.
The three newest sites keep their photographs in an `img/` folder beside the page.

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
- Each site is a single self-contained `index.html` (plus an `img/` folder where it uses photographs).
- Canvas 2D for the sea (`v8`) and the fungal network (`v12`); Three.js r160 from the
  CDN for the glass prisms (`v5`); pure DOM and CSS for the rest.
- Google Fonts. The six older business sites are drawn entirely in code. The three portfolio
  sites and the clinic use photographs from Unsplash, saved in the repo.
