# Plan — v7 five-system portfolio redesign

Date: 2026-08-15
Target: `/home/garvit/projects/portfolio5/v7-voxel/index.html`

## Decision

Replace the voxel/isometric world completely with one cohesive composite identity called
`WEATHER//SYSTEMS`. Keep the existing `v7-voxel` folder path for compatibility with the hub
and GitHub Pages links, but remove all user-facing voxel/world/island/cube language. The five
selected ideas are not five modes or five separate themes; they are five visual instruments
inside one art-directed portfolio:

1. Weather//Systems — the atmosphere, pressure field, and global visual language.
2. The Impossible Transit Map — the navigation spine and progress system.
3. Black Box / Act I — the project-card and case-study presentation.
4. Strata / Core Sample — the skills, experience, and evidence treatment.
5. Optical Bench / Focus — the observation/focus behavior used across cards and controls.

## Visual system

- Warm light base: weather-paper ivory, storm navy, graphite, oxidized teal, rust, brass,
  fog blue.
- Use one quiet low-cost contour/isobar canvas or SVG field behind the page with a robust CSS
  fallback. No voxel geometry, isometric islands, city skyline, or generic neon particle cloud.
- Typography: a characterful editorial display face paired with a restrained sans and a mono
  instrument face. Choose and document exact Google Fonts; do not default to Sora again unless
  the design review proves it is necessary.
- Use sharp instrument marks, station codes, contour labels, route ticks, stage-light cones,
  assay bands, and lens rings as semantic structure, not decoration.
- Spend boldness on the atmospheric field plus the route spine. Keep content panels readable,
  keyboard-visible, and quiet enough for the copy to lead.

## Section mapping

- Hero: a weather station at the edge of a pressure front. Isobars and wind vectors gather
  around the name; the page moves from clear morning to an incoming front as the user scrolls.
- About: station log / barometer readout with canonical biography and stat strip.
- Projects: Black Box / Act I. Projects are cueable stage cards with a small spotlight, a
  curtain seam, an act code, a project title, canonical description, stack, and metric.
- Skills: Strata / Core Sample. Skill groups are layered cutaway bands; percentages are assay
  readings and remain readable without animation.
- Achievements: evidence labels and alert slips pulled from the same instrument language.
- Experience: a vertical core sample / route ledger combining role dates and evidence.
- Contact: station closeout / final transmission, retaining the working mailto form and links.
- Footer: instrument calibration note, build note, year, and links.

## Interaction contract

- Impossible Transit Map: a fixed or sticky route spine with six accessible stations. Active
  section updates through IntersectionObserver and scroll progress; clicking a station smoothly
  navigates to its section. Hide or simplify it at mobile widths without blocking content.
- Optical Bench / Focus: project cards and important data plates have a restrained focus ring or
  lens aperture. Pointer hover sharpens emphasis and reveals a small observation readout; focus,
  keyboard, and touch must provide the same information without requiring hover.
- Black Box cards: hover/focus cues a spotlight and stage edge, not a generic translateY plus
  shadow. Cards must not become unreadable when idle and must not rely on blur-only text.
- Weather field: cursor influence is optional, throttled, pointer-fine only, and additive. Pause
  when hidden or offscreen. Reduced-motion gets a static contour composition.
- Strata: the core bands can reveal once, but no perpetual noisy animation. Every transform and
  opacity effect must have a clean reset path.

## Content contract

Read `docs/synthetic-data-pool.md` and the current v7 HTML before editing. Preserve canonical
names, descriptions, metrics, dates, contact values, links, and resume behavior. Do not invent
quantum reinterpretations or rename project facts merely to fit the metaphor. Theme vocabulary
may change labels such as `Island 02` to `Station 02`, but facts remain canonical. The page may
continue showing the existing curated v7 project count; do not add unsupported projects just to
make the design look fuller.

## Hub card contract

Update only the v7 card/scene in `/home/garvit/projects/portfolio5/index.html` and its v7
screenshot asset as needed. Keep the hub's overall Material Index design, all other cards, filters,
shuffle, links, and one-live-iframe behavior unchanged. Replace visible Voxel World / voxel copy
with `Weather//Systems` and a concise atmospheric-instrument tagline. The frame must read at a
small size as weather paper plus route spine plus lens aperture plus stage edge plus strata cut:
not a generic rounded card, not a pixel border, and not a reused signal/glass treatment. Refresh
`shots/v7-voxel.png` after the variant is finished if the hub uses the existing screenshot system.

## Typevolt audit

Inspect and browser-test `/home/garvit/projects/portfolio5/v10-typevolt/index.html` because
some hover interactions are reported broken. Fix only real v10 interaction bugs, preserving its
identity and content. In particular test transform ownership between scroll choreography,
`.hov` letter hover, `.rep` pointer repulsion, `t10c` snap animation, magnetic buttons/footer
links, hover-scrub metrics, and custom cursor labels. Check pointerleave/out reset, letters stuck
in repulsion, stale inline transforms after hover, operator-precedence behavior in the cursor
mouseout guard, hidden-tab recovery, reduced motion, keyboard focus, and coarse pointers. Use a
single composable transform/reset strategy if needed. Prove each repaired interaction live and
run node syntax checks on every script block.

## Gates

- v7 and hub have zero console/page errors and no horizontal overflow at desktop and 390px.
- v7 has working navigation, resume download, contact mailto form, all canonical links, reveals,
  reduced-motion behavior, no-JS-safe content, visible focus, and 44px targets.
- WebGL/canvas failure falls back to a complete static page; hidden tabs/offscreen loops pause.
- Hub v7 card screenshot loads at rest, live preview still obeys one-live-iframe behavior, and
  the v7 frame/label no longer says Voxel World.
- v10 hover interactions are live-probed before and after any fix; no regression elsewhere.
- Run vision QA on hero, projects, skills/experience, mobile, and the hub v7 card. Iterate until
  there are no actionable visual flags and the composite theme feels intentional rather than
  five unrelated skins.
- Update root `STATUS.md` with files changed, checks, v10 fixes, visual scores/quotes, and UTC
  plus IST start/end timestamps.
