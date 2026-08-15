# Plan — add four standalone theme variants and replace v7

Date: 2026-08-15
Project: `/home/garvit/projects/portfolio5`

## Corrected scope

The user wants five standalone portfolio experiences on the main chooser page, not one v7 page
that combines five ideas. The final collection will contain the existing 14 variants plus four
new standalone variants, plus the existing commission card:

- v7-voxel/index.html becomes the standalone `Weather//Systems` site. Keep the folder path for
  compatibility; remove voxel identity from all visible copy and the v7 hub card.
- Create v15-transit-map/index.html — `The Impossible Transit Map`.
- Create v16-black-box/index.html — `Black Box / Act I`.
- Create v17-strata/index.html — `Strata / Core Sample`.
- Create v18-optical-bench/index.html — `Optical Bench / Focus`.

The root chooser changes from 14 variants / 15 cards to 18 variants / 19 cards. Each new theme
gets its own full standalone page, screenshot, live iframe preview, hub scene/frame, title,
metadata, and card. The four new pages are not placeholders and are not sections inside v7.

## Variant design summaries

### v7 — Weather//Systems
Warm atmospheric instrument: pressure contours, forecast charts, wind vectors, barometer marks,
weather-paper palette, station navigation, and a calm-to-front-to-clear scroll progression.

### v15 — The Impossible Transit Map
A career represented as a transit network for ideas and systems, with impossible intersections,
route lines, stations, transfers, and a route-tracing scroll journey. Use parchment, cobalt,
vermilion, graphite, and transit-ink accents. Do not make it a generic subway infographic.

### v16 — Black Box / Act I
A premium theatre-stage portfolio: acts, cues, spotlights, stage wings, curtain seams, playbill
credits, and scene changes. Use black, bone, theatre red, brass, and restrained haze. Projects
are staged case files. Keep it distinct from Typevolt: stagecraft and light, not kinetic letter
choreography.

### v17 — Strata / Core Sample
A geological/material cross-section of a technical career: layers, depth logs, assay labels,
core samples, fault lines, and evidence embedded in strata. Use clay, limestone, basalt, amber,
and oxidized copper. This is tactile and earthy, not voxel, underwater, fungal, or archive-like.

### v18 — Optical Bench / Focus
An optical laboratory portfolio: lens diagrams, aperture rings, focal planes, calibration marks,
refraction, and observation. Use warm paper, graphite, teal, signal red, and lens blue. Avoid
full-page glassmorphism and avoid simply duplicating v5 Glass Horizon.

## Hub integration

Update root `/home/garvit/projects/portfolio5/index.html`:

- v7 card becomes Weather//Systems and no longer says Voxel, Island, or 3D Voxel.
- Add four standalone cards for v15–v18 with their own scene markup, CSS, title, description,
  category, href, screenshot, and live-preview layer.
- Add four new rail swatches in both the accessible rail and its aria-hidden duplicate.
- Change all collection counts and footer language from fourteen/fifteen to eighteen/nineteen.
- Extend filter/shuffle/live-preview selectors and card census to v15–v18.
- Preserve existing v1–v14 cards, filters, shuffle, card links, screenshot-at-rest/live-iframe
  behavior, one-live-iframe limit, file:// fallback, reduced motion, mobile, and overall Material
  Index design.
- New hub frames must be distinct at thumbnail size and must not reuse existing v1–v14 motifs.
- Generate shots/v15-transit-map.png through shots/v18-optical-bench.png after the pages are built.

## Content and facts

Read `docs/synthetic-data-pool.md` and the current v7 HTML before curating content. Use canonical
pool facts only. No invented metrics, dates, companies, schools, testimonials, or contact values.
The new pages may curate different theme-matched pool entries, but every name, description,
metric, stack, date, and contact value must be traceable to the pool/current canonical content.
Keep real contact values exact wherever contact appears:
`garvit9829@gmail.com`, `+91-8905402023`, `https://github.com/garvit-pandia`, and
`https://www.linkedin.com/in/garvit-pandia/`.

## Typevolt audit

Inspect and browser-test `v10-typevolt/index.html` because hover interactions are reported broken.
Fix only reproducible bugs, preserving Typevolt's content and visual identity. Specifically test
heading `.hov` reset, pointer `.rep` reset, transform conflicts among scroll/repulsion/snap,
case metric hover-scrub reset, magnetic button/footer reset, custom cursor relatedTarget logic,
hidden-tab recovery, reduced motion, keyboard, and coarse pointer. Prove live behavior before and
after edits and run syntax checks.

## Quality gates

- Every one of v7, v15, v16, v17, v18 is a complete standalone page with working sections,
  navigation, contact, resume, responsive behavior, reduced motion, and static fallback.
- Root hub has exactly 18 variant cards plus the commission card and every href/screenshot resolves.
- Exactly one live iframe is active during hub hover; leaving detaches after the grace period.
- Zero console/page errors, no horizontal overflow, no broken reveal, no overlapping text.
- 390px mobile, coarse pointer, reduced motion, file://, keyboard, and print paths are tested.
- Vision-rate each new page and each new hub card. Iterate until each is at least 8.5/10 with no
  actionable flags, targeting 9/10.
- Update root `STATUS.md` with the new variants, card count, QA, Typevolt fixes, vision quotes,
  timestamps in UTC and IST, and deviations.
