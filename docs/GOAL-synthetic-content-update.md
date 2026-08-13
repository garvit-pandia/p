# Goal Brief — Synthetic Content Update for All 14 Portfolio Variants

Date: 2026-08-13. This file is the FULL brief for the /goal session. The pasted /goal text
points here first. If the two ever disagree, this file wins for execution detail; the /goal
text's contract lines (verify / constraints / boundaries / stop when) win for completion
semantics.

## The goal (one line)

Replace all content in all 14 portfolio variants with artistically curated synthetic data
from a huge new pool, theme-matched per variant, vision-QA'd to 9/10+ average, award-winning
copy — the ONLY real data being the name "Garvit Pandia" and the real contact block, and with
OPTIONAL variant renames/reordering (light/dark theme emphasis) at the end. No token limits,
as many subagents as needed, never stop early.

## Data contract

REAL — required verbatim in every variant that shows contact info (and the name wherever a
name appears):

- Name: Garvit Pandia (and "Garvit" alone)
- Email: garvit9829@gmail.com
- Phone: +91-8905402023
- GitHub: https://github.com/garvit-pandia
- LinkedIn: https://www.linkedin.com/in/garvit-pandia/ (exact URL, trailing slash)

FORBIDDEN — zero hits repo-wide in any *.html file after the update (case-insensitive where
apt): India AQI Tracker, RAG Resume Analyzer, LPU, Lovely Professional University, Phagwara,
garvitpandia.me, plus every project/company/name/school from the OLD data file
(docs/fictional-resume-data.md — read it once to build the exclusion list).

Sweep scope = *.html files only (root index.html + all 14 variant index.html files). docs/
files are exempt — this brief itself contains the forbidden tokens as a checklist.

Contact link notes: write the tel: href as a string concatenation ('tel:+91' + '8905402023')
so the output pipeline cannot mask the patch input, then codepoint-verify the landed bytes.
The tool-output pipeline masks phone-like strings in grep/read_file/git output — python
byte-reads and codepoint dumps are ground truth. NEVER "fix" a tel href from masked output.

## Read first, in order

1. docs/GOAL-synthetic-content-update.md — this file, fully.
2. docs/synthetic-data-pool.md — created in Phase 1; the ONLY canonical content source after that.
3. STATUS.md (project root) — rubric conventions, wave tracker, per-variant history.
4. docs/research-digest.md — award-criteria digest; keep every content decision at that bar.
5. docs/iteration-campaign.md — history only; do NOT continue that campaign.
6. docs/brief-vN-*.md — each variant's design brief (concept, palette, metaphor) before curating its content.
7. Each variant's own index.html — full read before editing.

Load skills first: portfolio-variant-builds (conventions, pitfalls, checkers) and
autonomous-goal-briefs (goal loop mechanics).

## Phase 0 — Prepare

- Check STATUS.md wave tracker. If W16/W17 campaign waves show IN PROGRESS with a recent UTC
  timestamp, wait for them to finish (poll STATUS + file mtimes) before touching anything.
- Pause the cron job named portfolio5-iteration-campaign: cronjob action=list to find the id,
  then action=pause. Note the job id. A concurrent campaign session editing the same files
  mid-run corrupts both tasks. Resume at the very end ONLY if campaign waves still remain
  pending, and say so in the report.
- Baseline real-data sweep over every index.html (python byte-read; record hits in STATUS.md
  under a new section: SYNTHETIC CONTENT UPDATE).

## Phase 1 — Build the data pool

Write docs/synthetic-data-pool.md. HUGE — at least 3-5x more than any single variant needs —
and internally consistent:

- Canonical synthetic persona timeline (fictional career of Garvit Pandia, ~2018-2026:
  education arc, internship to mid-level career, side projects, open source). Every pool entry
  must fit it with no date contradictions.
- 80+ projects across 10+ domains (AI/ML, systems/backend, creative/frontend, product design,
  data, 3D/games, security, comms/networks, astrophysics/space, bio/organic, typography,
  luxury/brand). Each: name, one-line tagline, 2-3 achievement bullets with believable
  quantified metrics, stack, year, role, mood keywords, suggested-variant-match list.
- 30+ experience entries across ~12 fictional companies (intern → senior → freelance → founder).
- 40+ skills across categories; 20+ testimonials (fictional names/roles/quotes that sound
  human); 30+ achievements (hackathons, awards, papers, OSS, speaking); 10+ certifications;
  6+ education options (internally consistent with the timeline; variants pick one); 15+
  stat-strip sets (theme-flavored, believable); 12+ hobbies/interests/about material;
  fictional location + studio-name options for flavor.
- Per-variant curation table: recommended picks + tone for v1-light, v2-dark, v3-wild,
  v4-brutalist, v5-glass, v6-scrollstory, v7-voxel, v8-abyss, v9-ghostware, v10-typevolt,
  v11-event-horizon, v12-mycelium, v13-origami-aurum, v14-signal. Examples: v11 gets
  cosmic/astrophysics work; v12 organic/network systems; v13 luxury brand/design; v14
  comms/radio/decoding; v9 security/terminal; v4 raw engineering; v10 typography/creative-tech.
  Guidance, not a straitjacket — deviations allowed if justified in the report.
- Prepend a banner to docs/fictional-resume-data.md: SUPERSEDED — canonical content is now
  docs/synthetic-data-pool.md. Do not reuse its content.
- Generate ONE synthetic resume PDF: name Garvit Pandia, REAL contact header (email, phone,
  github, linkedin), synthetic body from the pool. Build as HTML, print via headless chromium
  (playwright page.pdf) or any reliable method. Copy into all 14 variant folders as
  Garvit_Pandia_Resume.pdf, overwriting the real one.

## Phase 2 — Implement, waves of 3

Waves: A = v1,v2,v3 · B = v4,v5,v6 · C = v7,v8,v9 · D = v10,v11,v12 · E = v13,v14 + root
index.html. Per-variant subagent spec:

- Read the variant's design brief, its index.html fully, and the pool curation table.
- Map every content-bearing spot: hero title/tagline, about, experience, projects, skills,
  education, certifications, testimonials, stats strip, contact, footer, and any data arrays
  in script blocks (many variants render projects from JS arrays — update the string values
  in the arrays, NEVER restructure the code).
- Artistically curate from the pool: the subset that best matches theme, mood, palette,
  metaphor. State rationale in 3-5 lines in the report.
- Contact block: real values verbatim (see Data contract; tel concat trick). Add a minimal
  contact block in the variant's style if none exists. Name = "Garvit Pandia".
- Replace content ONLY. Preserve all structure, classes, ids, data-attributes, script logic.
  No renames, no element removal/reorder, no feature code. Keep string lengths close to
  originals; mind heading wrapping; no overflow.
- Award-winning copy: believable, specific, human. ZERO AI-slop clichés ("passionate about",
  "cutting-edge", "driven developer", "transforming the future"). Metrics internally
  consistent within the variant.
- delegate_task goal strings must contain NO { } curly-brace blocks — write code/structure
  contracts into spec FILES the subagent reads. Subagents: file-tools only, no browser;
  execute code via write_file script to /tmp then terminal python3 (execute_code is blocked
  in subagent contexts); no rm -rf, no destructive git.
- 600s hard timeout. Pre-write timeout = re-dispatch with efficient-read spec (search_files
  to map structure, then targeted reads). Post-write timeout = file complete, verify directly,
  do NOT re-dispatch.
- After each wave: python3 /home/garvit/.hermes/skills/creative/portfolio-variant-builds/scripts/check-round-html.py <file>
  (known false positives: a-tag open/close report on every file; bogus N-tag match from JS
  loop source like for(let i=0;i<N;i++) — adjudicate once, do not chase). node --check every
  extracted script block. Commit with prefix "content:".

## Phase 3 — Vision QA + fix loop

Per variant, controller-side:

- Browser: zero console/page errors, no horizontal scroll, no overlapping text,
  reduced-motion path intact, 390px mobile viewport intact. Verify contact links: mailto
  garvit9829@gmail.com, github/linkedin hrefs exact, tel href codepoint-verified.
- Screenshot hero + 2 scrolled sections (desktop) + one mobile capture. vision_analyze with
  strict rubric: design integrity 10, content/copy quality 10, theme coherence 10, layout
  cleanliness 10. Record VERBATIM quotes in STATUS.md.
- Target: every variant avg >= 9/10. Floor 8.5. Fix rounds for anything below floor or any
  real flag (contrast, overlap, broken reveal, theme drift, weak copy). Micro-fixes applied
  directly; bigger rework via subagent. Re-verify after every fix. No "looks fine" without
  the model's numbers and quotes.
- No look/perf regression vs pre-update state (side-by-side screenshots; content swap must
  not degrade the design).

## Phase 4 — Naming + order review

- Review all 14 names and chooser order. Renaming OPTIONAL but encouraged when a name is too
  broad/generic — v1-light and v2-dark are prime candidates: rename to something evocative
  that EMPHASIZES the theme (light-evoking names for light themes, dark-evoking names for
  dark themes). Rename any other variant whose name under-sells its concept.
- Keep the vN- folder convention (v1-slug … v14-slug); only the slug changes.
- Renumbering ALLOWED if it genuinely improves the chooser's aesthetic flow (palette family,
  light-to-dark gradient, concept lineage) — never for its own sake.
- Every rename: git mv the folder, update root index.html links + blurbs, update STATUS.md
  tables, grep repo for other references to the old folder name (HTML only) and fix. Re-run
  the round checker on the root index. Commit prefix "rename:".
- "No change needed" is a valid outcome — state the reasoning in the report.

## Phase 5 — Final sweep + deploy + report

- Python sweep *.html files: real contact present verbatim wherever contact appears; zero
  forbidden tokens (see Data contract; build the exclusion list from the OLD data file).
- All 14 folders contain the synthetic Garvit_Pandia_Resume.pdf.
- Root index.html: no forbidden data; blurbs updated; every chooser link resolves post-rename.
- STATUS.md: SYNTHETIC CONTENT UPDATE section — per-variant table (curated picks summary,
  sweep result, console status, vision before/after with verbatim quotes, line counts,
  rename/reorder notes).
- Commit every wave; final commit + git push origin main after ALL gates pass (deploys GitHub
  Pages — the live site the user wants updated). Verify live: fetch
  https://garvit-pandia.github.io/p/ and confirm new content + renamed folders resolve.
- Resume the paused cron job if campaign waves remain pending.

## Hard rules

- Content-only edits. Never design/features/structure/class/ids/JS logic. Wrap-safe additive
  CSS only, never redesign.
- No shared code between variants; each stays standalone.
- Subagents: 3 concurrent max, 600s, file-tools only, no { } in goal strings, no execute_code.
- Contact + name real and verbatim; everything else synthetic.
- Do not touch docs files except: synthetic-data-pool.md (write), fictional-resume-data.md
  (banner only), STATUS.md (update).
- Do not continue/claim waves of the old iteration campaign.
- NEVER stop after a round to ask the user anything — auto-decide with best judgment and
  continue. Only declare done after Phase 5 is fully verified.

## Verification gates (all must pass before done)

1. Real-data sweep: contact present verbatim in all 14; zero forbidden tokens in *.html.
2. All variants + root: console clean; no layout breaks at desktop / 390px / reduced-motion;
   contact links exact.
3. check-round-html.py passes on every touched file (adjudicated artifacts only).
4. Vision: every variant >= 9/10 avg (floor 8.5), verbatim quotes in STATUS.md.
5. Synthetic resume PDF in all 14 folders.
6. All committed (content:/rename: prefixes), pushed, live verified on GitHub Pages.
7. STATUS.md updated with full per-variant table incl. naming/order decisions.

## Reporting (final summary must include)

Per-variant curation rationale (3-5 example picks) · rename/reorder decisions (or why none) ·
vision scores + verbatim quotes before/after · sweep presence/absence counts · checker and
console results · plan deviations with reasons · cron job pause/resume state + id · start and
end timestamps (UTC).

## Completion contract (also carried in the /goal text)

verify: all 14 variants + root index contain zero forbidden legacy data; real contact
(garvit9829@gmail.com, +91-8905402023, github.com/garvit-pandia, linkedin.com/in/garvit-pandia)
present verbatim everywhere contact appears; every variant vision-rated 9/10+ average with
verbatim quotes in STATUS.md; console clean; synthetic resume PDF in all 14 folders; naming
and order review done with rationale logged; pushed and live on GitHub Pages.

constraints: content-only edits, no design or feature changes, no shared code, subagent pool
max 3, 600s timeouts, no user questions, contact and name real and verbatim, everything else
synthetic.

boundaries: do not touch the old iteration campaign waves, do not modify docs other than the
pool file, the old-data banner, and STATUS.md, do not stop early; renames only via git mv
with root-index and STATUS updates.

stop when: Phase 5 complete, all gates pass, live deployment verified, final report delivered.
