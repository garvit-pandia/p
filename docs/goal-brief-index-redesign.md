# /goal brief — Finish & polish the Material Index (portfolio5 index.html)

Paste the block below into `/goal` in a fresh session. Self-contained — no
conversation history required. Workdir: run `cd /home/garvit/projects/portfolio5` first.

---

GOAL: Complete, verify, and polish the redesigned portfolio index page at
/home/garvit/projects/portfolio5/index.html — the "Material Index": a single
self-contained HTML page where each of the 14 portfolio variants is a card
made of that variant's own visual material (glass card for v5-glass, signal
static for v14-signal, etc.). Finish the in-flight merge of the card scene
parts, run the full structural + browser + vision verification gates, then
run 2-4 vision-driven polish rounds until the vision model rates the page
8.5+/10 with no remaining actionable flags. Do NOT stop after one round, do
NOT ask the user anything — pick the best option and continue. Only declare
done after every gate below passes AND the vision rating target is met, then
update docs/STATUS.md and write the final report.

READ FIRST, in order:
1. /home/garvit/projects/portfolio5/docs/index-redesign-brief.md — the scene-part contract (markup/CSS file formats, class prefixes, verification commands). Follow it for ANY new scene work.
2. /home/garvit/projects/portfolio5/index.html — the current skeleton (base design, 15 card shells, JS). Read via search_files mapping + targeted chunks if large.
3. /home/garvit/projects/portfolio5/parts/ — the scene part files cards-A.html/.css (cards 01-05), cards-B.html/.css (cards 06-10), cards-C.html/.css (cards 11-15). These may or may not be complete; a prior session dispatched 3 subagents to write them.
4. /home/garvit/projects/portfolio5/docs/STATUS.md — project status convention; append your round.
5. Load these skills with skill_view: portfolio-variant-builds, localhost-browser-qa, frontend-design. Read the localhost-browser-qa skill's setup section before any browser work.

WHAT EXISTS (do not rebuild from scratch):
- Skeleton index.html: warm parchment #f5f4ed + terracotta #c96442, Georgia/Inter/JetBrains Mono, hero "Choose your material.", a 14-swatch marquee rail of clickable material links, filter bar (All/Light/Dark/3D/Motion) + Shuffle button, 15 cards (14 variants + a mailto commission card), scroll reveals (js-gated .rv/.in), pointer-tracked glint on the glass card (card--v5), ambient background orbs, skip link, footer, reduced-motion and print CSS blocks.
- Merge markers inside index.html: CSS markers /* ==SCENES_A== */, /* ==SCENES_B== */, /* ==SCENES_C== */ and markup markers <!-- SCENE_A1 --> through <!-- SCENE_C5 --> (one per card stage).
- Card scenes must stay theme-native: 01 archive photo/petal/stamp, 02 constellation, 03 loom threads, 04 factory grid, 05 glass prisms, 06 field journal leaf, 07 voxel cubes, 08 abyss jelly, 09 ghostware holo, 10 typevolt letter, 11 event horizon ring, 12 mycelium network, 13 origami folds, 14 signal static, 15 commission placeholder.

PHASES:
- Phase 1 — Merge: if parts/ files exist and are complete (5 markup lines each, matching CSS), merge them into index.html at the markers (write a small python merge script if needed: replace each marker comment with the part content; CSS parts go in the style block). If a part file is missing or malformed, rebuild ONLY that part yourself following the brief contract (prefixes c1-c15, each class defined once, animations gated on prefers-reduced-motion no-preference, hover reactions gated on hover hover + no-preference).
- Phase 2 — Structural checks after EVERY patch: extract every script block to /tmp and node --check each; python brace-balance the style block (counts of open and close braces must be equal); python tag-balance the html; grep duplicate ids; class census: every cN- class must appear exactly once as a selector and be used in its card's stage markup. Never write literal tag names inside comments or strings. Same-file edits sequential, never parallel. Keep every patch diff-reviewed.
- Phase 3 — Serve + browser QA: start python3 -m http.server 8777 --bind 127.0.0.1 from the project root as a background process. Start a headless Linux Chrome with remote debugging: find the newest ~/.cache/ms-playwright/chromium-*/chrome-linux64/chrome, launch it with --headless=new --remote-debugging-port=9222 --user-data-dir=/tmp/qa-chrome --no-first-run --no-default-browser-check about:blank as a background process. Use browser_exec against http://127.0.0.1:8777/index.html (cache-buster ?v=N after every edit; hard reload). Assert: zero console errors; all 15 cards render; all 14 variant hrefs resolve (HTTP 200); filters hide/show correct cards and aria-pressed persists; Shuffle navigates to a visible card; glass card glint element exists; no-JS check (block JS once) leaves all cards visible; mobile emulation 390px wide shows no horizontal overflow and every visible button >= 44x44px; reduced-motion emulation renders static frames with all content visible.
- Phase 4 — Vision rating loop (HARD GATE, user rule): capture full-page screenshots (hero + rail, card grid top, card grid middle/lower, footer; scroll with js window.scrollTo then wait before each capture; save each to /tmp/qa/NN-view.png via CDP Page.captureScreenshot base64). Rate each with vision_analyze (aux vision is configured — just call it with the file path). Ask for: aesthetic rating 1-10, vibe, and a numbered list of specific visual flaws. Fix every flag that survives source-verification (check computed styles/geometry before touching code — false flags are common: contrast claims, "static" claims on animated pages, overlap claims). After fixes, re-capture and re-rate. Target: 8.5/10 or higher and zero actionable flags. Run 2-4 rounds; stop early only if a rating drops — then revert the last change and try a smaller fix.
- Phase 5 — Report: update docs/STATUS.md (rubric, scores before/after with vision quotes, what shipped, what is pending). Final summary must include: start/end UTC timestamps, phases completed, structural check results, browser QA results, each vision round's verbatim rating line, total rounds, plan deviations with reasons. Deliver the final report in this session; if a messaging gateway is connected, mirror a short summary to Telegram.

HARD ENVIRONMENT RULES:
- Only touch: index.html, docs/ (STATUS.md, brief), parts/ (if you create parts). NEVER modify anything inside v1-light through v14-signal folders — they are the variants; the index only links to them.
- Keep all 14 hrefs byte-identical (v1-light/index.html etc.) and the mailto:garvit9829@gmail.com commission link.
- Ports: dev server 8777, chrome debug 9222 — these may be taken by a prior session; if so, reuse them (curl http://127.0.0.1:8777 and http://127.0.0.1:9222/json/version to check) instead of starting new ones.
- Concurrency: another session may still be building parts/. Before merging, poll parts/ mtimes 3 times over ~60s; if they change, wait for stability. If index.html mtime changes under you, re-read before patching.
- Background processes: use terminal background=true (never nohup or trailing ampersand).
- Subagents (only if you dispatch any for new polish features): pool max 3 concurrent, ~600s timeout; delegate_task goal strings must contain NO curly-brace blocks (keep goals brace-free prose, put all code contracts in brief files); subagent commands with -e/-c flags and rm -rf are auto-denied — write files instead; each subagent owns separate files, never the same file in parallel; verify every subagent claim yourself (stat the file, re-read, browser-assert).
- Preserve: prefers-reduced-motion support, no-JS fallback (cards are static HTML — reveals only hide when html has the js class), keyboard focus-visible styles, 44px touch targets, no horizontal overflow on mobile.
- Do not add external dependencies. Google Fonts CDN links already present are fine.
- Keep the page a single self-contained index.html: embedded CSS/JS, no build step.

VERIFICATION GATES (all must pass before done):
- node --check on every extracted script block.
- Style block brace-balanced; HTML tag-balanced; no duplicate ids.
- Browser console: zero errors.
- All 14 variant links + mailto resolve.
- Filters, shuffle, glint, reveals all function in-browser.
- Mobile 390px: no horizontal scroll, all touch targets >= 44px.
- Reduced motion: everything visible, no animation.
- No-JS: everything visible.
- Vision rating >= 8.5/10 with zero actionable flags (quote the rating line verbatim in your report).

CORE vs STRETCH: Core = phases 1-5 with gates green. Stretch (only after core is done and rated) = one extra polish pass per card (deep hover micro-interaction, print CSS audit for blank-sections trap, an open-graph meta block). Do not start stretch until the core vision target is met.

Remember: autonomous run — never ask the user to decide; if a choice is ambiguous, pick the option that best matches the warm editorial Material Index concept and note the decision in the report.
