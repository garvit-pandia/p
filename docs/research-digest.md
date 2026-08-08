# Research digest — what award-winning actually means (round 7+)

Distilled from an Awwwards jury member's "why they win" breakdown (hontran.dev, Jun 2026),
Awwwards/FWA/CSSDA patterns, Webflow/reallygooddesigns micro-interaction roundups, kinetic
typography guides (Studio Meyer, Creative Bloq, Threestudio), and WebGL studio craft
(Lusion, Active Theory, Locomotive-style weighted scroll, Iventions, Minh Pham, Mat Voyce,
By-Kin, Uncommon Studio). Every iteration round should be judged against THIS.

## The three pillars (miss one → capped at mid-7s; hit all three → award territory)

1. **Point of view.** Every type choice, color, grid serves ONE idea. Take away the
   animation and the static frames must still look like they were made on purpose.
   → Each round must strengthen the variant's single narrative, not add decoration.
2. **Choreography, not animation-for-its-own-sake.** Transitions carry meaning; scroll
   sequences pace a story; micro-interactions reward attention. Motion has a "why".
   → New effects must deepen the theme's story (e.g. V8 sonar = diving, V7 flight = world).
3. **Performance discipline.** 60fps on a mid-range phone; jurors throttle CPU 4× + Fast 3G.
   Beauty is the whole discipline — a 3D hero at 18fps on Android will not win.
   → Every round: DPR caps, transform/opacity only, rAF pause, no per-frame shadowBlur,
   no layout thrash, passive listeners. Verify budgets after every feature.

## How to read a site like a juror

1. Screenshot the hero — is the STATIC frame still strong? If motion is hiding weak art
   direction, it fails.
2. DevTools → CPU 4× slowdown + Fast 3G — still ~60fps and fast paint?
3. Craft lives in STATES: page-to-page, hover-to-active, scroll-in. Cheap sites cut;
   award-winners transition.
4. Toggle prefers-reduced-motion — a real craftsperson built a graceful fallback.

## Patterns that win (with the concrete move)

- **Weighted / continuous scroll** (By-Kin, Uncommon): sections transition like camera
  moves; the page feels like one continuous surface. → Scroll-linked transforms that
  anticipate the next section (camera keyframes, parallax layers, scroll velocity easing).
- **Atmosphere over spectacle** (Iventions): WebGL used for lighting/mood, not tricks.
  → Our V7 world: light, fog, day/night are the story; don't add gimmicks.
- **Kinetic type that never blocks reading** (Mat Voyce): letters stretch, snap,
  recombine ON SCROLL, timeline-driven, tuned so text stays readable.
  → Our V10: keep letter transforms within ±8% size and never reduce contrast below AA.
- **Spotlit reveals** (Iventions): GSAP-paced reveals read like a guided walkthrough.
  → Sequence reveals with a per-card rhythm (stagger by index, not random).
- **Soft cursor trail + calm reveals** (Shchebetovska): "scrolling feels calm and
  immersive" — micro-interactions must soothe, not compete.
  → Hover states: 150–250ms ease-out, 1–3px lift, glow ≤ 0.2 alpha. Never flashy.
- **Meaningful micro-interactions** (Webflow/Really Good Designs): hover shifts an
  individual project; cursor-scrub previews; tilt reacts to pointer.
  → One signature hover per variant per round, themed (e.g. V8 ping, V9 glitch, V7 glow).
- **Performance as craft**: instancing, sprite-based glow, DPR caps, `content-visibility`,
  no images where code suffices. (All our variants already follow this — keep it.)

## Per-variant narrative compass (the "why" each variant exists)

- V1 Sunlit Archive — a warm, human archive: handwriting, stamps, sunlight. Motion =
  paper, ink, developing photos. Rounds should add paper/ink behaviors, never neon.
- V2 Midnight Index — a star chart of a career: you navigate constellations.
  Motion = celestial (orbit, drift, twinkle, parallax). Rounds: sky behaviors.
- V3 Dream Loom — a lucid dream woven of silk threads and aurora. Motion = fluid,
  breathing, thread-like. Rounds: loom behaviors (weave, sag, shimmer).
- V4 Mono Factory — an industrial machine that prints proof. Motion = mechanical
  (receipts, cursors, glitches, precision). Rounds: machine behaviors.
- V5 Glass Horizon — light through glass. Motion = refraction, prism, glint, depth.
- V6 Field Journal — a botanist's field log. Motion = collecting, stamping, drawing.
- V7 Voxel World — a playable diorama. Motion = flight, day/night, living islands.
- V8 The Abyss — a deep-sea dive. Motion = descent, sonar, bioluminescence.
- V9 Ghostware — a memory archive of a digital ghost. Motion = recall, glitch, telemetry.
- V10 Typevolt — the kinetic editorial machine. Motion = letter choreography, ink, print.

## Techniques queued from the research (use in rounds, theme-filtered)

- Scroll-velocity easing on the whole page (weighted scroll feel) — V4, V10
- Section "camera-move" transitions — V7 (already), V5, V6
- Letter stretch/snap/recombine — V10, V3
- Cursor-scrub project previews (hover scrubs a row) — V10, V4, V1
- Tilt + spotlight per card — V5, V7 (spotlight = warm glow on active island)
- Ink-bleed / smudge hover on text — V1, V3, V6
- Star twinkle with per-star phase — V2
- Thread sag between eyelets — V3
- Glass refraction shift on pointer — V5
- Glitch "state machine" (idle → hover → active → done) — V9, V4
- Sonar/bioluminescent reactions to pointer — V8
- Calm micro-reveals with stagger — ALL (audit each round)
- Hero static-frame test — ALL (audit each round: hide canvas, is hero still designed?)
- Reduced-motion full path — ALL (audit each round)
