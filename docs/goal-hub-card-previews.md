# /goal — Hub card previews: real glimpses + character (portfolio5 index.html)

Upgrade the variant cards on the portfolio5 chooser hub so each card shows a REAL glimpse of its variant website (screenshot thumbnail at rest, live scaled iframe on hover) wrapped in a theme-native decorative frame, with proper entrance/hover character — and keep everything working on file:// and mobile. SCORE BAR: every card must be rated ≥8/10 on the first vision pass and ≥9/10 on the final run (creativity, design, final look) — token cost is NOT a constraint, creativity is.

---

## 1. One-line goal

Rebuild the 14 variant cards on /home/garvit/projects/portfolio5/index.html so each card shows the actual site (screenshot at rest, live scaled iframe on hover), framed by an upgraded theme-native decorative scene per variant, with boot-in entrance + hover character — zero new dependencies, variant folders untouched, works double-clicked from file:// and served over http. Every single card must rate ≥8/10 on the first vision pass and ≥9/10 on the final audit, scored per-card on creativity, design, and final look. If meeting the bar costs 3x the tokens, spend them — creativity is the product, cost is not a constraint.

## 2. Project path

/home/garvit/projects/portfolio5
- Hub file: index.html (single-file hub, ~1982 lines, warm light theme: parchment #f5f4ed family, terracotta accent, Georgia/Inter/JetBrains Mono, rounded corners, soft shadows — do NOT change the hub's overall design language; cards get the upgrade)
- 14 variants in sibling folders: v1-light … v14-signal (READ-ONLY — never edit files inside any vN-* folder)
- Dev server: python3 -m http.server 5176 (run from the project root; pin port 5176)

## 3. Read FIRST, in this order

1. docs/STATUS.md — build status, rubric, round conventions (update it at the end)
2. index.html — full read: the existing card system (grid, .card, .stage, per-variant scene parts c1-* … c14-*, badge, filters data-f=light/dark/motion/3d, shuffle, .sw quick rail, reveal system, style-block organization). Map every style block boundary and the script blocks BEFORE editing.
3. docs/index-redesign-brief.md and docs/goal-brief-index-redesign.md — prior hub-round context (conventions, what was already decided)
4. Skills: load portfolio-variant-builds, frontend-design, popular-web-designs (design quality bar — the user hates AI-slop defaults; every frame/hover decision must be intentional, not generic gradient-card styling). Use popular-web-designs' real design systems as reference fuel for the frames, not as templates to copy.

## 4. What to build (compact)

For EACH of the 14 cards (card--v1 … card--v14, names: Archive / Midnight / Loom / Factory / Glass / Journal / Voxel / Abyss / Ghost / Type / Horizon / Mycelia / Origami / Signal):

A. REAL GLIMPSE — screenshot at rest
- Generate one viewport screenshot per variant (~1280x800, hero area, reveal-forced so all reveals have fired and animations settled — use the reveal-forced-fullshot technique: scroll to bottom, sweep back up, reset to top, wait, capture) via headless Chromium/Playwright; save as shots/v1-light.png … shots/v14-signal.png (project-root shots/ folder, committed with the hub).
- Each card's .stage shows its screenshot as the resting visual: crisp, correctly cropped, slightly desaturated at rest, color-normalized on hover.

B. LIVE PREVIEW — scaled iframe on hover
- On hover (pointer:fine only), load the variant's real index.html in an iframe inside the card, scaled down to card size (classic scale technique: iframe at 4x stage size, transform scale(0.25), transform-origin top left, pointer-events:none so the card stays a link — clicking the card still opens the variant in a new context exactly as today).
- PERF CONTRACT: never more than ONE live iframe at a time; detach (swap src to about:blank) ~400ms after pointer leaves the card, unless the pointer re-entered (grace window); lazy-init on first hover (no iframes at page load); a live iframe must never run while its card is off-screen (IntersectionObserver gate). If the iframe fails to load (file:// or error), the screenshot remains — never a blank card.
- Fade the live layer in over ~300ms so the first-hover load reads as a beat, not a flash.

C. CHARACTER — decorative frames + entrance + hover
- Upgrade the existing per-variant scene parts (c1-* … c14-*) into a theme-native FRAME around the screenshot (a bezel/chrome treatment that matches each site's identity: e.g. v1 archive = paper/stamp margins, v2 midnight = HUD corner brackets + scan tick, v4 factory = terminal chassis, v7 voxel = pixel border, v10 type = letterpress rules, v13 origami = folded-gold edge, v14 signal = waveform rails). Each frame must be DIFFERENT and unmistakably its variant's motif. Keep frames subtle — the screenshot is the hero; the frame is the setting.
- Entrance: replace the plain fade-up with a staggered boot-in (cards power on with a per-family flavor: light = warm settle, dark = scan-in, motion = kinetic slide, 3d = depth pop — use the existing data-f family attribute). Entrance must be one-shot (runs once on reveal), not per-hover.
- Hover character: subtle 3D tilt on the stage (few degrees, transform-only, released on leave), slow Ken Burns drift on the screenshot while the live iframe is loading, a themed scanline/sheen sweep across the stage, the badge + caption (variant name + one-line tagline) brightening, and a clear "OPEN" affordance (corner arrow chip sliding in). All hover effects pointer:fine + hover:hover gated.
- Keep every existing behavior: whole card is an anchor to the variant, filters (light/dark/motion/3d) and shuffle keep working, .sw rail untouched, badge chips stay readable.

D. HYGIENE
- prefers-reduced-motion: no tilt, no sweep, no Ken Burns, no boot animation — screenshots + frames render statically, iframe preview still allowed (it is the user's explicit action).
- Mobile/coarse pointer: screenshots + frames only, NO iframes, NO tilt; cards stack as today; 44px hit targets preserved.
- 14 PNGs lazy-loaded (loading=lazy, below-fold), total budget reasonable; no layout thrash; rAF loops gated to visible cards.
- file:// must work: relative paths for shots/, no fetch() of JSON, no external assets beyond the fonts the hub already uses.

E. CREATIVITY MANDATE (the bar)
- Each card must be a small DESIGN STATEMENT, not a standard card treatment. FORBIDDEN as the main move: uniform rounded hover-glow, the same sheen sweep on every card, generic 3D tilt alone, identical layouts with different colors. Every frame, entrance flavor, and hover beat must be derived from ITS variant's identity — if two cards share a move, one of them is generic.
- The 14 cards must be distinguishable in SILHOUETTE at a glance: a viewer should recognize "this is the Voxel card" and "this is the Signal card" from the frame alone, without reading the name.
- Craft matters: consistent per-variant accent tokens, crisp corners/edges, no half-pixel lines, no muddy gradients, deliberate spacing. A card that merely "works" is a failed card.
- Score bar: first full rating pass must land every card at ≥8/10 on all three dimensions (creativity, design, final look); the final audit must land every card at ≥9/10. Below the bar = keep iterating, spend whatever tokens it takes. (Escalation only if 4 dedicated passes cannot move one card past 8.5 — see section 6.)

## 5. Hard environment rules

- Port 5176 only for the dev server; serve from the project root so /shots/ and /vN-*/ resolve.
- Variant folders v1-light … v14-signal are READ-ONLY. The hub round does not touch them (an unrelated v2-dark CSS fix already landed on disk — screenshots must simply capture current disk state).
- No npm, no build step, no new dependencies — hub stays a double-click static page plus committed image assets.
- All index.html edits are SEQUENTIAL same-file patches, one at a time, diff-reviewed, checker-run after every patch (scripts/check-round-html.py index.html; known artifacts: the <a> loose-count false alarm and the <N> JS-loop false tag — adjudicate, don't chase). Parallel subagents are OK ONLY for independent asset generation (per-variant screenshot scripts); never two writers on index.html.
- No bash heredocs; write helper scripts with write_file; keep shell commands small and split.
- Git: commit the hub + shots/ with the project's normal commit style; update docs/STATUS.md with a hub-round row (what shipped, verification results, vision scores before/after).
- TOKEN SPEND: not a constraint. Never stop, skip, or cheapen a polish cycle for cost. If raising a card from 8 to 9 takes three more passes, do them. The user explicitly accepts 3x spend for the bar.

## 6. Verification gates (ALL must pass before done)

1. Server check: python3 -m http.server 5176 from project root; hub loads at http://127.0.0.1:5176/ with zero console errors.
2. Screenshot pass: all 14 shots exist in shots/, each matches its variant (spot-check 3 by eye/vision against the live variant), none blank/black/white.
3. Card behavior in browser: every card shows its screenshot at rest; hover activates EXACTLY one live iframe (probe: count document.querySelectorAll('iframe:not([src*=about])') === 1 while hovering); leaving the card detaches it after the grace window; clicking a card still navigates to the variant; filters + shuffle still work.
4. file:// pass: open index.html directly via file:// — all 14 thumbnails + frames render, no console errors, hover preview degrades gracefully (screenshot stays, no blank).
5. Mobile + reduced motion: 375px viewport — cards stack, no iframes, no tilt; emulated prefers-reduced-motion — static-safe states, no motion.
6. VISION SCORE GATES (MANDATORY, the creative bar — verbatim quotes in the report):
   - RATING PROTOCOL: rate EVERY card individually — per-card cropped screenshots at stage size (not just a full-page pass), one rating prompt with fixed wording, three dimensions scored 0-10: creativity (originality of concept/frame/motion), design (composition, hierarchy, craft), final look (pixel polish, coherence, "would this win on a gallery page"). Average the three per card; the card's score is its average.
   - FIRST PASS: after the initial build, run the full 14-card rating. Every card must score ≥8/10. Any card below 8 gets dedicated polish (that card only), then a re-rate. Repeat until all 14 clear 8.
   - FINAL AUDIT: when all gates above pass and all cards clear 8, run the final full 14-card audit. Target: every card ≥9/10. Keep polishing until it clears. ESCALATION (rare): if 4 dedicated creative passes cannot move one specific card past 8.5, land the best 8.5+ version, document exactly what was tried and the critic's verbatim quotes, and move on — never ship a card below 8.5, never accept an average card.
   - Discipline: vision baselines shift between moods — always re-rate with the SAME prompt, baseline-compare against the pre-change crop of the same card, and measure any "overlap / blur / broken" claim with real rects/pixels before acting on it. 8/10 must mean "award-worthy small composition", not "passes at a glance".
7. Keyboard: tab through cards — visible focus outline, Enter opens the variant.

## 7. Reporting (final summary must include)

- Tasks completed with the round's file-change summary (style blocks added, scripts added, shots/ contents)
- Screenshot pipeline: exact commands/script used, dimensions, technique (reveal-forced)
- Verification results: console-clean confirmations, iframe-count probe output, file:// + mobile + RM results
- PER-CARD SCORE TABLE: all 14 cards × 3 dimensions × first-pass score → final score, with one verbatim critic quote per card on the final audit. Any card that used the 8.5 escalation gets its full history.
- Perf notes: page weight with 14 PNGs, max live iframe count observed
- Plan deviations with reasons; start/end timestamps (UTC + IST)

## 8. Autonomy rules

- Do NOT stop after the first working version. The build is only "done" when every card clears the score gates — build, rate, polish, re-rate, iterate until the bar is met. At least 2 polish cycles are the floor, not the plan; the score bar is the plan.
- Do NOT ask the user anything mid-run — pick the best option and continue. The preview approach is already decided (screenshot at rest + live iframe on hover + themed frames). The score bar is already decided (≥8 first pass, ≥9 final, per card).
- Token cost is explicitly waived by the user. Never trade quality for tokens.
- Major progress updates and the final completion report must be delivered to BOTH the origin chat and Telegram.

## 9. Stretch (only after the score bar is met and verified)

- Per-variant micro boot on first hover (e.g. v4 terminal types a line, v14 signal squelches a waveform) lasting <600ms before the live preview fades in.
- Card tagline/readout row (variant name + tech strip) with per-variant accent coloring.
- A "PREVIEW" / "OPEN" affordance refinement pass based on the vision audit.
- Slight per-card parallax on the frame layer when the stage tilts.

## Structured /goal contract (paste these lines with the brief)

verify: zero console errors on hub + file://; all 14 shots exist and match; exactly one live iframe at a time on hover; filters/shuffle intact; reduced-motion and 375px passes; PER-CARD vision scores: every card ≥8/10 on the first full rating pass and ≥9/10 on the final audit (creativity + design + final look, verbatim quotes + score table in the report); STATUS.md updated
constraints: variant folders read-only; no new deps; port 5176; sequential same-file patches on index.html; file:// must work; one-live-iframe perf contract; token spend is not a constraint
boundaries: do not redesign the hub's overall theme or the variant sites; do not add a build step; do not remove existing card features (filters, shuffle, sw rail, badges); do not ship any card below 8.5/10
stop when: all verification gates pass AND every card scores ≥9/10 on the final audit (or the documented 8.5+ escalation is the only blocker) AND docs/STATUS.md has the hub-round row with the per-card score table
