# Museum Portfolio Index Design

## Goal

Redesign the root `index.html` into a light-mode portfolio inspiration catalogue. The page should show that Garvit Pandia can create distinctly different digital worlds, while making all fourteen portfolio variants easy to preview and open.

The root page is a discovery surface, not another portfolio variant. Existing variant pages and their links remain unchanged.

## Approved Direction

Use the **Museum collection** direction from the visual companion. The page should feel like a calm, premium exhibition catalogue rather than a dark command centre, generic card grid, or list of links.

Approved choices:

- Light-mode museum/editorial language.
- One complete collection containing all fourteen exhibits.
- Art-directed preview scenes inside every exhibit card.
- No iframes or live embedded portfolio pages.
- Static HTML/CSS/JS with no build step or new dependencies.

Rejected direction:

- The dark “Signal room” concept was rejected and must not influence the root page palette.

## Experience Structure

### Masthead

The top of the page contains:

- A compact museum-style wordmark for Garvit Pandia.
- A thesis headline communicating range: “Fourteen ways to make a digital world.”
- A short supporting sentence explaining that the collection contains different visual languages built from one creative practice.
- A visible collection marker: `14 exhibits`.

The masthead stays compact enough that the first exhibit content is visible on a desktop viewport. It does not use a full-screen hero or a large decorative animation.

### Collection controls

Add a lightweight filter row below the masthead:

- `All`
- `Light`
- `Dark`
- `3D`
- `Motion`

`All` is selected on initial load and displays every exhibit. Filters are an optional browse aid, not the primary navigation. They hide non-matching cards without changing the URL or reordering the source data.

Filter membership is explicit and can overlap:

- `Light`: `v1-light`, `v13-origami-aurum`
- `Dark`: `v2-dark`, `v8-abyss`, `v9-ghostware`, `v11-event-horizon`, `v12-mycelium`, `v14-signal`
- `3D`: `v5-glass`, `v7-voxel`
- `Motion`: `v3-wild`, `v4-brutalist`, `v6-scrollstory`, `v10-typevolt`

### Exhibit gallery

Render all fourteen portfolios as one collection flow. The first exhibit receives slightly more visual weight as the opening exhibit, but no portfolio is hidden behind a “featured only” mode.

Each exhibit has:

- Variant number.
- Category or medium label.
- Custom visual preview stage.
- Portfolio title.
- Short description derived from the existing root inventory.
- Existing link to the variant’s `index.html`.
- One clear action label: `Enter exhibit`.

The complete card surface is a keyboard-accessible link. The action label is visible but does not create a second nested link.

### Footer

Close with a quiet catalogue note that reinforces the collection concept and preserves the existing technology attribution. Avoid adding another competing primary CTA.

## Visual System

### Palette

The page shell uses a light gallery palette:

- Cool ivory paper for the page background.
- Porcelain white for exhibit surfaces.
- Graphite for headings and primary controls.
- Muted grey-green for supporting copy and metadata.
- Restrained terracotta for active labels, rules, and small markers.

Preview stages may use portfolio-specific colors because their job is to demonstrate the range of the fourteen source experiences. Page chrome remains consistent so the collection still feels like one site.

Do not introduce dark full-width sections, neon glows, generic purple gradients, or a second unrelated accent system.

### Typography

- Display and exhibit titles: characterful serif with generous line-height and controlled scale.
- Body and interface labels: clean sans-serif.
- Numbers, categories, filter labels, and metadata: monospace at readable sizes.

The serif is used for the museum/editorial identity, not injected randomly into individual preview scenes. Preview scenes may use their own type treatment only when it communicates the source variant.

### Layout

- Desktop: asymmetric but disciplined gallery grid with varied exhibit proportions.
- Tablet: two-column grid with reduced preview heights.
- Mobile: strict single-column exhibit flow, full-width cards, and wrapped filter controls.
- No horizontal page scrolling at any viewport.
- Use one consistent card radius and border treatment across the root page.

## Preview Scene System

Preview scenes are small, custom DOM/CSS compositions. They must communicate one signature cue per variant without pretending to be a complete screenshot.

Preview mapping:

| Variant | Preview cue |
|---|---|
| `v1-light` | Parchment, framed photo, terracotta archive stamp |
| `v2-dark` | Star points and orbital rings on a light-backed specimen panel |
| `v3-wild` | Woven color bands and fluid aurora shapes |
| `v4-brutalist` | Hard grid, bold type block, terminal cursor |
| `v5-glass` | Translucent prism and refracted edge |
| `v6-scrollstory` | Paper specimen, field mark, and route line |
| `v7-voxel` | Isometric blocks forming a tiny world |
| `v8-abyss` | Luminous specimen circle and depth marker |
| `v9-ghostware` | Holographic scan frame and memory label |
| `v10-typevolt` | Oversized kinetic letter composition |
| `v11-event-horizon` | Orbital ring and singularity marker |
| `v12-mycelium` | Branching nodes and organic growth path |
| `v13-origami-aurum` | Folded paper plane and gold-toned crease |
| `v14-signal` | Waveform/spectrogram strip and decoded stamp |

Preview behavior:

- Resting state is fully legible and does not depend on hover.
- Hover/focus can lift the card slightly and reveal one subtle preview detail.
- Use transform and opacity for motion; do not animate layout dimensions.
- Disable decorative motion under `prefers-reduced-motion: reduce`.
- Decorative preview elements have appropriate `aria-hidden` treatment; the exhibit title and description carry the accessible meaning.

## Data And Implementation Boundaries

Keep the implementation inside the existing root `index.html`. No supporting asset is necessary for the initial implementation.

Use one normalized exhibit data structure in the page script containing:

- `href`
- `number`
- `title`
- `category`
- `filters`
- `description`
- `previewClass`

The filter behavior should derive from that same data rather than maintaining separate hard-coded lists. The current fourteen `href` values are the source of truth and must remain relative links to the existing variant folders.

No iframe, external image dependency, framework, package installation, or changes to the fourteen child sites are in scope.

## Accessibility And Resilience

- Use semantic headings in order.
- Use real links for navigation and exhibit opening.
- Keep visible `:focus-visible` styles on filters and exhibit links.
- Ensure filter buttons expose selected state with `aria-pressed`.
- Do not rely on color alone to identify a category or selected filter.
- Preserve zoom and readable body text on mobile.
- Provide a no-JavaScript fallback where all exhibits remain visible.
- If a filter interaction fails, the unfiltered collection remains usable.

## Verification Plan

Before completion:

1. Parse the root page and confirm all fourteen exhibit links still point to existing `index.html` files.
2. Load the page in a browser and confirm zero console errors.
3. Test `All`, `Light`, `Dark`, `3D`, and `Motion` filters, including returning to `All`.
4. Tab through masthead controls and exhibit links; confirm visible focus and sensible order.
5. Verify each exhibit card preview is visible before opening its link.
6. Check desktop, tablet, 390px mobile, and a reduced-motion environment.
7. Confirm no horizontal overflow and no broken layout from long titles or descriptions.
8. Open a sample from each filter group and confirm the child page route resolves.

## Out Of Scope

- Redesigning any `v1`–`v14` portfolio page.
- Replacing the existing portfolio content or fictional resume data.
- Building a CMS, server, search backend, or persistent filter URL state.
- Embedding live child pages in the root cards.
- Adding dark mode to the root index.
