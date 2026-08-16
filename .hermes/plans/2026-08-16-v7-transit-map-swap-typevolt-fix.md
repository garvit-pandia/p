# Plan — v7 → Transit Map swap + Typevolt broken-text fix

**Date:** 2026-08-16
**Project:** `/home/garvit/projects/portfolio5`
**Local server:** `python3 -m http.server 5176 --bind 0.0.0.0` (http://127.0.0.1:5176/)

## Context (verified from disk, 2026-08-16)

- `v7-voxel/index.html` (83,765 bytes) = **v7 Weather//Systems** — warm atmospheric instrument (pressure contours, wind vectors, forecast charts). Card slot 07 on the hub.
- `v15-transit-map/index.html` (80,746 bytes) = **"The Impossible Transit Map"** — transit network for ideas/skills/projects; nav: Origin / Interchange / …; brand `TM//GARVIT PANDIA`. Currently NOT linked on the hub (v15–v18 were trimmed).
- Hub `index.html` (137,933 bytes, 2868 lines):
  - v7 card markup at **lines 2587–2595**: `class="card card--v7 rv" data-f="light"`, stage has `c7-iso i1/i2`, `c7-bar`, `c7-mast`, `c7-ticks`, `c7-ann "ISOBAR 07"`, `c7f-cr tl/tr/bl/br`, `img.pvc-shot shots/v7-voxel.png`, `pvc-live/fx/open`.
  - v7 card CSS at **lines 2176–2226** (`--surface #F4F0E8`, `--accent #1F7A78`, isobar/dial/mast styles).
  - **Unused v15 card CSS already present at lines 2227–2268** (`.card--v15`: transit map bg grid, `c15t-line-a/b`, `c15t-node n1/n2`, `c15t-transfer`, `c15t-label`, tokens `#F6F1E5 / #1F3A93 / #D4402A / #2E4AC2`) + **entrance keyframes `c15t-line-in / c15t-lineb-in / c15t-node-in / c15t-xfer-in` at lines 2390–2393** — reuse these.
  - Quick-switch names, two copies: **line 2479** (desktop) and **line 2495** (mobile): `sw--v7` "Weather" → change to transit name.
  - `shots/` has `v7-voxel.png` (weather shot) and `v15-transit-map.png` (transit shot, 1280×800).
- `v10-typevolt/index.html` (64,872 bytes): broken text in **`#work` section heading** — `.sechead h2[data-split] "Case Files"` renders overlapping/clipped/illegible ("ACESS"-like glitch in user screenshot) **at rest AND on hover**. Mechanism: `h2 .k-l` inline-block letter spans (CSS lines 166–168) + `letterPop` animation (line 110: `translateY(110%) rotate(8deg)` with `--i` delays), `perspective:800px` on h2, `data-split` JS. Same `.k-l` mechanism used by hero `h1.name` — hero must stay intact.

## Task A — Replace v7 slot with the Transit Map site

1. **Site swap:** copy `v15-transit-map/index.html` → `v7-voxel/index.html`. Keep folder name `v7-voxel`. **Do NOT delete `v15-transit-map/`** (backup; hub stays unlinked to it). Verify the copied page serves 200 and all its internal references (resume PDF, assets) resolve inside `v7-voxel/`.
2. **Hub card stage:** replace the v7 stage markup (isobar/dial/mast/ticks/"ISOBAR 07") with transit elements — `c15t-map`, `c15t-line-a`, `c15t-line-b`, `c15t-node n1/n2`, `c15t-transfer`, `c15t-label` (label like `ROUTE 07`) — reusing the existing `.card--v15` CSS (rename block to `.card--v7` or duplicate; keep `data-f="light"`). Keep `pvc-shot` / `pvc-live` / `pvc-open` chrome.
3. **Card body:** meta `Material 07 / 14` + new descriptor (e.g. `Light · Cartographic`); `<h2>` → **`Transit//Map`** (matches existing naming pattern; alternative `The Transit Map` — pick one, stay consistent with hub copy); description → transit-flavored copy about route lines/stations/one long journey through the work; foot `Step inside →` unchanged.
4. **Quick-switch:** lines 2479 + 2495: `Weather` → `Transit`. Check `.sw--v7` tile tint still fits transit palette.
5. **Card screenshot:** replace `shots/v7-voxel.png`. Fast path: copy `shots/v15-transit-map.png` (identical site); better path: capture a fresh 1280×800 browser shot of `http://127.0.0.1:5176/v7-voxel/` and save as `shots/v7-voxel.png`. Verify the thumb renders inside the card (hover = live preview `pvc-live` already works since it loads the page).
6. **Docs:** update `STATUS.md` + `HANDOFF.md` (v7 is now Transit Map; v15 folder = unlinked backup).

## Task B — Fix Typevolt (v10) broken heading text

1. Reproduce at `http://127.0.0.1:5176/v10-typevolt/` (browser + screenshot). Confirm which headings break (`#work` "Case Files" per screenshot; check every `[data-split]` heading + hero `h1.name`).
2. Root-cause: split-letter JS + `.k-l` transforms/`letterPop` + `perspective` + hover handlers (`.sec.kinetic` may have per-letter scrub). Look for: letters stuck mid-animation (animation never settling / `animation-fill-mode`), transforms causing overlap on `inline-block` spans, `white-space` collapse, or a hover distort effect applied at rest.
3. Fix so text is **crisp and legible at rest AND on hover**, kinetic character retained (motion on entry only or subtle hover, no corruption), reduced-motion path clean, keyboard accessible. No regression to hero.
4. Re-verify all other sections' headings + hero on the page.

## Quality bar (hard gates)

- **Vision-model polish loop (user mandate):** with the configured auxiliary vision model, rate **each** of: (1) the transit-map site (v7-voxel/), (2) the hub card `card--v7` (screenshot of the card in situ on index.html), (3) Typevolt headings. **Target ≥ 9/10** for aesthetics / vibe / originality / "award-winning, non-AI-slop" feel. Loop: rate → quote score → improve → re-rate, until ≥9/10 on all three (cap 10 rounds, then report best + gap). No look/perf regression between rounds.
- **Design rules:** load `frontend-design` + `popular-web-designs` skills BEFORE any UI edit. No AI-slop defaults (warm cream + terracotta serif + hairline columns is the default trap — transit direction must feel deliberate, cartographic, distinctive). Type: display + body + mono roles; JetBrains Mono fits the map labels.
- **Browser QA (localhost-browser-qa skill):** all pages 200 (root, v7-voxel/, v15-transit-map/, v10-typevolt/); zero console errors; no horizontal overflow at 780px desktop AND 390px mobile; `prefers-reduced-motion` path renders correct static text; keyboard nav works; 44px touch targets on touched controls; card hover/preview works.
- **Git:** commit to `main` with a clear message; `git diff --check` clean. Do NOT push / deploy. Do NOT touch other variants (v1–v6, v8–v14, v16–v18) or other cards.

## Scope boundaries

- Core: Task A (site swap + card + screenshot + docs), Task B (Typevolt fix), vision loop on (1)+(2)+(3), browser QA, commit.
- Stretch (only if all core gates pass with rounds to spare): one extra polish pass on the transit site's signature interaction (route scrubber / station hover) if the vision model flags it.
- Keep hub card count at 14. `data-f="light"` stays.

## Report

Final summary must include: start/end timestamps (UTC + IST), files changed, per-surface vision-model quotes + scores per round (N → M), browser QA results (console/overflow/RM/keyboard), git commit hash, deviations from this plan with reasons.
