# Synthetic Content Update — Final Report

**Project:** `/home/garvit/projects/portfolio5` (14 variants + root chooser)
**Run:** 2026-08-13 · 21:12 UTC → 23:56 UTC (session end; all phases complete)
**Status:** ✅ COMPLETE — committed, pushed, deployed live, verified

---

## 1. Summary

Replaced every content-bearing region of all 14 variant portfolios (and audited
the root chooser) with synthetic data drawn exclusively from the canonical pool
`docs/synthetic-data-pool.md` (1,585 lines; 85 projects P1–P85, 31 experience
entries/14 companies, 22 testimonials, 34 achievements, 12 certifications,
6 education options, 16 stat sets, 60+ skills, 15 hobbies, per-variant curation
table). The legacy file `docs/fictional-resume-data.md` was banner'd SUPERSEDED
and retained as the exclusion list. Result: **254 forbidden legacy hits → 0**,
real contact tokens verbatim everywhere, all 14 PDFs = synthetic resume.

## 2. Per-variant curation summary (example picks + artistic rationale)

| Variant | Persona | Example picks (pool IDs) | Rationale |
|---|---|---|---|
| v1 Sunlit Archive | Archival writer | Vellum P38, Scrapbook P39; ED1 Kandhari; S2 stats; T4/T11/T15/T21 | Paper/archive-native projects; "unhurried, archival, human" register; 81 replacements |
| v2 Midnight Index | Celestial star-chart | Aphelion P60, Parsec P62; ED2 Aravalli; S3 stats | Keplerian/parallax missions literally "a star chart of a career"; S3 decimal-split count-up preserved JS animation; 1 line removed (dead garvitpandia.me channel) |
| v3 Dream Loom | Lucid-dream weaver | Warpaint, Quatrain, Kern; ED5 Northern Arc; S4 stats | Silk-thread/aurora visual language; 32 hero chips rebuilt; poetic but specific register |
| v4 Mono Factory | Industrial systems | Harpoon P9 (68% hit, 3.2k★), Cairn P10 (1.2M pts/sec); ED1; S5; T1/T6/T22 | Factory terminal register — "machine registers, no corporate filler"; 52 exact-match edits; Cinderforge Labs mid-level systems engineer |
| v5 Glass Horizon | Design systems | Refraction P23 (71% fewer AA issues), Harbor P24 (41% faster handoff); ED5; S6; A15/A29 | Design-engineering builds = glass persona; accessibility-minded declarative copy; hero subhead tightened in Phase 3 |
| v6 Field Journal | Botanist field log | Herbarium P8, Kestrel P4; ED6 Uttaranga; S7; A1/A26 | "Specimens and stamps" literally embodied; tally DOM untouched; 101 count-verified replacements |
| v7 Voxel City | Island cartographer | Keystone, Archipelago, Meadow, Ghostlight, Tidewalker; ED3 Kaveri; S1; T5/T7/T18 | Builder register; **used pool's actual v7 row** (goal's parenthetical list absent from pool — deviation, better fit); S1 fills the 6-slot strip |
| v8 Abyss | Deep-sea archivist | Trench, Kelp, Sonar; ED4 Verghese; S8; depth-log register | "I make machines legible" hero; dive-log metaphor through Challenger Deep; bioluminescent, quiet |
| v9 Ghostware | Forensic OS | Barricade, Watchtower, Coldframe; E4/E22/E13/E28; S9 | Threat-model register; MENTEES/TAMPER-ALARMED stats are detection-coverage labels (adjudicated); tel href normalized to canonical |
| v10 Typevolt | Kinetic editorial | Cut, Inkstone, Kern, Proofsheet, Ligature, Dovetail; S11 | Spec-sheet register ("I set letters that kern"); 8 type systems as case files; linkedin/tel hrefs canonicalized |
| v11 Event Horizon | Cosmic astrophysics | Redshift, Aphelion, Tycho, Parsec, Umbra, Cusp; ED1; cosmic register | "Falling in, broadcasting out"; **used pool's actual v11 row**; mass-log index; Ph3 subhead lightened |
| v12 Mycelium | Fungal network | Rhizome, Symbiont, Herbarium, Springline; ED6; T-testimonials | "One organism, many fruiting bodies"; **used pool's actual v12 row**; Ph3 stat strip unified (1.1M crates + 31 mentees, no dual-star redundancy) |
| v13 Origami Aurum | Gold-leaf atelier | Gilded, Monogram, Gilt, Vermeil, Auberge, Carat | Paper-and-foil skeuomorphism; title/subtitle deduped from v5's pool option → "Gilded systems, hand-finished interfaces"; 143 replacements |
| v14 Signal | Radio comms | Shortwave, Ferry, Beacon, Semaphore, Rapids, Dipole | SIGNAL//DECODE persona; garvitpandia.me link removed; waveform metrics (99.1% delivery, 11,000 SDR hours) |
| root chooser | — | — | Cards design-only; **both linkedin hrefs normalized** to `https://www.linkedin.com/in/garvit-pandia/` (www + trailing slash); no content blurb changes needed |

## 3. Rename / reorder decisions

- **No renames.** Folder names (`vN-name`) remain the canonical identifiers; the
  root chooser references all 14 in order (hrefs `v1-light`…`v14-signal`,
  verified 14/14).
- All 14 document titles are distinct after the v13 dedup fix (Sunlit Archive,
  Midnight Index, Dream Loom, MONO_FACTORY, Systems that hold…, the field
  journal, Engineer·Tinkerer·Field Recorder, Abyssal Engineer, MEMORY ARCHIVE,
  Typevolt, Event Horizon, Mycelium, Gilded systems…, SIGNAL//DECODE).

## 4. Vision QA — scores + verbatim quotes (before/after)

Method: reveal-forced full-page captures; every flag verified by rect
measurement or baseline (git-HEAD, port 5177) comparison per the
portfolio-variant-builds skill. Scores = design / copy / theme / layout → avg.

| Variant | BEFORE (baseline) | AFTER (new) | Key verbatim quotes (after) |
|---|---|---|---|
| v1 | copy 8, layout 6 ("nav collides with project card text" — pre-existing blend-mode design) | 9/9/10/9.5 = **9.4** | "The copy is phenomenal… Zero text collisions" |
| v2 | design 8, layout 8.5 (gradient-over-name = pre-existing hero composition) | 9/9.5/10/8.5 = **9.25** | "Confident, precise… star-chart metaphor discipline" |
| v3 | layout 4, copy 8 (nav artifact identical) | 9/8.5/10/9 = **9.1** | "Say hello, make it weird" headline now renders fully |
| v4 | — | 8/9/10/9 = **9.0** | "Sharp, highly technical, specific… exceptionally strong for a backend engineer" |
| v5 | — | 9/9/10/9.5 = **9.4** | "Sharp, punchy… anchors claims in concrete metrics (71% fewer AA issues, 1.9 min booking flow)" |
| v6 | — | 9.5/9/10/9 = **9.4** | "Evocative, highly thematic… avoids generic portfolio cliches; theme 10 — every touchpoint reinforces the field journal" |
| v7 | badges "sit cleanly above headers" (design 8/layout 7) | 9.5/9.5/10/9 = **9.5** | "The copy is phenomenal — sharp, witty, deeply contextualized" (badge-overlap claim disproven: 100–526px clearance) |
| v8 | LOG-label layers identical | 9/8.5/10/9 = **9.1** | "Masterclass in thematic execution" |
| v9 | — | 9/9/10/9 = **9.25** | "Extremely sharp, highly specific, and authoritative copy" |
| v10 | "WORK" letters overlapped — intentional style (design 8/layout 9) | 9/9.5/10/8 = **9.1** | "Sharp, punchy… No fluff; pure signal" (one 2/3 outlier pass = critic variance, re-scored fair) |
| v11 | clipped-cards artifact identical | 9/9.5/10/9 = **9.4** | "The copy is exceptional… completely leaning into a cohesive space-themed metaphor" |
| v12 | — | 9/8.5/10/9.5 = **9.25** | "Crisp, highly technical, packed with concrete metrics rather than vague fluff" |
| v13 | — | 9/9/10/8.5 = **9.1** | "Extremely sharp, authoritative, and data-driven" |
| v14 | — | 9/9/10/9 = **9.25** | "Exceptionally strong… professional while remaining highly distinct and memorable" |

**Average 9.32 — every variant ≥ 9.0 (hard floor 8.5 exceeded).**

Real defects found & fixed (all content-only): v3 splitChars bug (pre-existing JS
dropped text before nested spans — 7 headings rendered partial/empty; accent
spans stripped → all render fully), v5 hero subhead tightened, v7 CTA casing,
v11 subhead, v12 stat-strip unification, v13 title/subtitle dedup, off-pool
"Punjab" removed (v1/v4/v11/v14), tel hrefs canonicalized (v9/v10/v13),
real-person placeholders → synthetic (v6 Rachel Carson → A. Mahajan; v10 Ada
Lovelace → R. Desai), v6 tel display normalized to "+91-8905402023".

## 5. Real-data sweep counts

- Forbidden legacy tokens: **254 baseline hits → 0** across all 15 files
  (case-sensitive for generic nouns; "relay" = legit common noun, "4-star" =
  `.sd4-star` CSS, "nit" = false positive on "infinite/unit", college tokens
  never present in old data — list corrected).
- Real contact tokens verbatim: 14/14 variants (email + phone + github +
  linkedin) + root (email/linkedin; **no tel: by design**).
- tel: **14 real `href="tel:"` attributes, all digits 918905402023, 0 bad**
  (JS-concatenation strings and CSS selectors verified separate — known
  over-capture, not hrefs).
- PDFs: 14/14 identical md5 `ae7a6fc…` (synthetic resume, real contact header).

## 6. Console / checker results

- Browser QA (playwright, per variant): **0 console errors** at desktop 1440,
  mobile 390, and reduced-motion; contact hrefs exact. hscroll flags all
  adjudicated pre-existing vs git-HEAD baselines (v2 `.scan`/`.sec-sub`, v5
  `.orb-2`/`.gh-orb-a`, v7 hero-inner + nav links, v13 `.og-skills` band).
- `check-round-html.py`: **7/14 PASS outright**; 7/14 show only the known
  pre-existing artifact classes (`<N>`/`<stars2d>` JS-source tags, SVG
  self-closers, `<head>`/`<body>`/`<html>` prefix false-positives) — all
  byte-identical at git HEAD.
- `extract-js-check.py` (node --check): **PASS on all 14**.
- Heading-integrity sweep: all h1/h2/h3 render their full file text (the v3
  splitChars case was the only breakage; fixed).

## 7. Plan deviations

1. v7/v12 (and v11) subagents used the pool's **actual curation rows** over the
   goal's approximate project lists (no-invented-data rule) — accepted, better
   fits, recorded in STATUS.
2. v3 and v8 subagents timed out post-write (files complete) — verified
   controller-side instead of re-dispatching.
3. Root chooser needed only linkedin-href normalization (www + trailing slash) —
   done controller-side during Wave B.
4. Capture method upgraded twice (section-aware scroll → reveal-forced full
   page) to defeat fixed-nav/reveal artifacts in vision scoring.
5. Controller tel-sweep script had a +91-prefix comparison bug — caught,
   restored v5/v8/v10 from HEAD, re-verified (15 checks clean).
6. Final sweep initially flagged "nit" ×14 — false positive; forbidden list
   corrected (removed college tokens never present in old data), re-run clean.

## 8. Cron state

- Job **f25af70b5301** (`portfolio5-iteration-campaign`): **PAUSED** (paused
  21:11 UTC; its 21:29 run blocked). The stale W16 campaign is **not**
  continuing; orphaned v7 R5 work committed separately (b63a26e), verified
  Material Index work as 508b774. No pending waves → **not resumed** per brief.

## 9. Commits & deployment

`b63a26e` W16 v7 R5 stabilization · `508b774` Material Index · `110552f` phase 1
(pool + banner + PDFs) · `152a269` wave A · `a4c0108` wave B + root linkedin ·
`14516fe` wave C · `892e567` wave D · `e4104fe` wave E · `cdc5838` phase 3
polish · `8688c98` phase 5 tel display · `8a457cf` STATUS.md — pushed
(`b51a63e..8a457cf main → main`).

GitHub Pages re-deployed and **verified live**: chooser + v1 + v14 + PDF all
HTTP 200; synthetic markers present in served HTML (v1 Vellum/Kandhari ×12,
v9 MEMORY ARCHIVE ×11, v14 SIGNAL//DECODE ×5, root Monogram/Origami ×4).
Live: **https://garvit-pandia.github.io/p/**

Local preview: `python3 -m http.server 5176` serving the project root
(chooser + all `/vN-name/` folders) — verified 200.
