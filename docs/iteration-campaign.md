# Iteration campaign plan — round 7+ (5 rounds × 10 variants)

Goal: at least 5 iteration rounds per variant, reference-driven (docs/research-digest.md),
burning serious tokens via parallel subagent waves. Every round = ONE themed feature
(theme-native, per the digest's narrative compass) + 2–3 fixes + file-level verification.
Controller does browser verification + vision scoring between waves, updates STATUS.md.

## Round themes (each variant gets all five, in order)

- R1 — **Point of view**: strengthen the single narrative + static-frame strength.
- R2 — **Choreography**: a scroll-driven story beat (sequence, camera move, paced reveal).
- R3 — **Micro-interactions**: themed hover/pointer states + transition polish.
- R4 — **Performance + resilience**: budget audit (DPR, rAF pauses, paint), reduced-motion
  path, mobile pass, graceful fallbacks.
- R5 — **Jury pass**: full-page vision audit, fix verified flags, final polish, re-score.

## Wave schedule (3 variants per wave, next round for each)

| Wave | Variants / rounds | Status |
|---|---|---|
| W1 | v1 R1, v2 R1, v3 R1 | ← NEXT |
| W2 | v4 R1, v5 R1, v6 R1 | |
| W3 | v7 R1, v8 R1, v9 R1 | |
| W4 | v10 R1, v1 R2, v2 R2 | |
| W5 | v3 R2, v4 R2, v5 R2 | |
| W6 | v6 R2, v7 R2, v8 R2 | |
| W7 | v9 R2, v10 R2, v1 R3 | |
| W8 | v2 R3, v3 R3, v4 R3 | |
| W9 | v5 R3, v6 R3, v7 R3 | |
| W10 | v8 R3, v9 R3, v10 R3 | |
| W11 | v1 R4, v2 R4, v3 R4 | |
| W12 | v4 R4, v5 R4, v6 R4 | |
| W13 | v7 R4, v8 R4, v9 R4 | |
| W14 | v10 R4, v1 R5, v2 R5 | |
| W15 | v3 R5, v4 R5, v5 R5 | |
| W16 | v6 R5, v7 R5, v8 R5 | |
| W17 | v9 R5, v10 R5, + final sweep | |

## Round-scope ideas per variant (pick the best for the round's theme)

- **v1 Sunlit Archive** — R1: Archive TOC index (sticky right-edge book index, sliding
  terracotta marker, hover shows section first line). R2: photo "developing" pass — duotone
  photos develop/sepia-tone as they enter view (scroll-linked filter). R3: ink-bleed hover
  on marginalia (blur→sharp 200ms) + stamp press feedback on buttons. R4: budget pass +
  fonts swap audit (Fraunces optical sizing) + print-friendly CSS. R5: jury pass.
- **v2 Midnight Index** — R1: star twinkle layer (per-star phase, two-layer alpha) + "you
  are here" pulse on the star-chart rail. R2: constellation narrative — hero orbit
  re-traces a path on scroll (celestial journey through sections). R3: comet cursor trail
  (tiny, themed) + orbit tilt on pointer. R4: perf pass (star budget, DPR), reduced-motion
  static sky. R5: jury pass.
- **v3 Dream Loom** — R1: thread sag between eyelets (gravity sag, tension-linked) +
  dreamlog wet-ink smudge hover. R2: scroll-weave — the thread "weaves" a new color band
  per section (already palette-linked — extend into the hero). R3: aurora pointer warp
  (shader mouse uniform) + silk trail thinning on slow motion. R4: shader budget (res
  scale), mobile fallback. R5: jury pass.
- **v4 Mono Factory** — R1: machine states — every card gets a boot sequence (power-on
  line by line) on reveal. R2: "hack the DOM" — nav commands glitch section content
  (pending from inventory). R3: mechanical hovers (lever/switch cursor words, 2px inversions)
  + receipt tear on contact send. R4: perf pass (terminal render, type budget). R5: jury pass.
- **v5 Glass Horizon** — R1: prism spotlight — cards get a refraction sheen that tracks
  pointer (already have tilt sheen — extend to sections) + glass edge highlight pass.
  R2: camera-move section transitions (scroll-linked translate on .sec, like V7 flight).
  R3: orb hover magnetism (orbs drift toward pointer gently). R4: backdrop-filter budget
  audit (limit blur surfaces on mobile). R5: jury pass.
- **v6 Field Journal** — R1: FIELD COMPLETE confetti (pending) + tally into the rail.
  R2: journal page-turn reveal for sections (skewY page-flip entrance). R3: sketch hover —
  pencil underline draws on hover, stamps press with ink. R4: perf + reduced-motion
  (journal opens flat). R5: jury pass.
- **v7 Voxel World** — R1: island spotlight — active island gets warm emissive bloom +
  monument beacon pulse on activation (extend existing glow), label click pulses rail cube.
  R2: meteor shower at night (cheap points) + city windows spell section numbers. R3:
  pointer-follow clouds/sun parallax (camera micro-tilt) + hover island = tooltip card.
  R4: instancing budget audit, fog tuning, mobile camera FOV. R5: jury pass.
- **v8 The Abyss** — R1: jellyfish follow pointer (gentle, pointer-fine) + pressure-gauge
  sweep on depth-record reveal. R2: dive-pacing — hero → about transition descends through
  a light-ray corridor (scroll-linked). R3: bubble burst on section titles + card glow
  surge on hover (beyond ping). R4: particle budget on mobile, canvas resize audit. R5:
  jury pass.
- **v9 Ghostware** — R1: command history (↑/↓) + 'whoami' easter egg + per-section
  hologram recolor. R2: boot sequence — the archive "boots" on load (progress bar, sector
  checkmarks) then reveals hero. R3: slot drag-to-recall (pointer-fine drag scrubs
  glitch intensity) + cursor becomes crosshair+word. R4: canvas budget + telemetry pause
  when hidden. R5: jury pass.
- **v10 Typevolt** — R1: case-file hover-scrub metric counter (number scrubs with cursor X)
  + marquee pause on hover. R2: letter stretch/snap on section enter (letters over-rotate
  then settle — Mat Voyce style, keep readable). R3: ink-press hover — letters get
  "printed" texture stamp on hover (subtle) + magnetic links in footer. R4: content-visibility
  audit + print styles + reduced-motion letter static. R5: jury pass.

## Dispatch rules (from memory + skill)

- 3 subagents max per wave, 600s hard timeout — ONE round per task, tight scope (1 feature
  + 2–3 fixes), add-only where possible.
- Every task MUST read: docs/research-digest.md, docs/iteration-campaign.md (its row),
  STATUS.md, the inventory reference, and the variant's own index.html (read fully first).
- Feature must carry the theme past the hero; guard with reduced-motion + pointer gates;
  zero console errors; node --check every script block; tag-balance greps; report exact
  line counts + verification output. No browser/server in subagents.
- Controller between waves: browser-verify (cache-buster ?v=N), vision-score hero + the
  changed section, update STATUS.md score table + inventory, then dispatch next wave.
- Optionally ONE subagent per wave may probe X via the xurl skill for portfolio-design
  threads (skip gracefully if unauthenticated) and fold findings into its report.
