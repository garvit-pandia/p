# The Material Index — current state

**Last updated:** 2026-10-12
**Folder:** `/home/garvit/projects2/portfolio-gallery`
**Branch:** `concept-sites` (from `main`). Nothing on it is committed yet.
**Local server:** `http://127.0.0.1:5186/` (`python3 -m http.server 5186`, registered in `../PORT-REGISTRY.md`)
**Live:** https://garvit-pandia.github.io/p/ (GitHub Pages, serves `origin/main` from the repo root)

---

## The idea changed

The repo used to be "the same portfolio, fourteen ways". Every variant needed a full set
of career details, and the placeholder copy invented a college, employers and
certificates under my real name. That was the wrong shape for what I want to show.

Now each variant is a **concept website for a fictional business**. The point is range:
different kinds of site, different styles, and one working feature in each. My own
details appear in one place only, a footer credit on each site. Nothing on a concept
site claims anything about my education or work history, so there is nothing to get wrong.

## What is in the repo on this branch

| Part | State |
|------|-------|
| `index.html` — the gallery | 6 site cards + 1 full-width commission card. Rail, filters, shuffle and hover live preview all work. |
| `v13-origami-aurum/` | **Kaagaz Haveli**, hotel, Udaipur. Stay calculator at `#og-stay`. |
| `v16-black-box/` | **Saanjh Repertory**, theatre, Chandigarh. Seat map booking at `#booking`. |
| `v5-glass/` | **Kanch Invoicing**, software. Pricing slider and monthly / yearly switch at `#pricing`. |
| `v12-mycelium/` | **Dhingri & Co.**, mushroom farm, Solan. Shop `#myShop` and basket `#myBasket` (saved in `localStorage`). |
| `v10-typevolt/` | **Typevolt**, type foundry. Type tester at `#tester`, eight families on Google variable fonts. |
| `v8-abyss/` | **Paatal Dive Co.**, dive school, Andamans. Depth finder at `#finder`, depth rail 0 – 40 m. |
| `shots/` | Fresh 1280×800 screenshots for the six. The other twelve files are old and unused by the gallery. |
| The other twelve `vN-*/` folders | Unchanged and unlinked. They still hold the old invented career copy. |
| `DOC-20260716-WA0002.pdf` | My real résumé. Nothing links to it. |
| `parts/` | Leftover card fragments. Unused. |

Shared pattern on the six sites:

- Footer credit: "<Name> is a fictional <thing>. Concept site designed and built by
  Garvit Pandia · Back to the gallery". Links to `https://garvitpandia.me` and `../index.html`.
- Forms confirm on the page and say that nothing was sent. No `mailto:` on any form.
- Contact addresses use the `.example` domain. No résumé links, no phone number of mine.

## Left over from the old idea

- **Twelve old variant folders** are still in the repo and would still be published by a
  push, because GitHub Pages serves every folder whether or not the gallery links it.
  They need to be rebuilt as concept sites or deleted before this branch goes live.
- **Fourteen invented résumé PDFs** (`v1`–`v14`, `Garvit_Pandia_Resume.pdf`). The six
  rebuilt sites no longer link to theirs, so `v5`, `v8`, `v10`, `v12`, `v13` have a PDF
  nothing points at. All fourteen are live on `main` today.
- `docs/synthetic-data-pool.md` and the old briefs describe the portfolio idea. The six
  concept sites do not use them.

## Local and live are different

The live site is `origin/main`: the fourteen-portfolio gallery, three commits behind
local `main`, with the invented career copy and résumé PDFs. None of the concept-site
work is live.

`garvitpandia.me` (project `../garvit`, `src/lib/data.ts`) describes this repo as
fourteen portfolios and shows a strip of them. That text and strip need updating when
this branch ships.

## Next

1. Decide what happens to the twelve old folders: rebuild more of them as concept sites, or delete.
2. Delete the invented résumé PDFs.
3. Commit this branch, merge to `main`, push.
4. Update the gallery entry on `garvitpandia.me`.
5. Optional: stop publishing `docs/`, `STATUS.md`, `HANDOFF.md` and `.hermes/`, which
   GitHub Pages serves along with everything else.

## Which docs are current

- **Current:** `README.md`, this file, `docs/content-rules.md`, the newest entry in `STATUS.md`.
- **History, do not follow as instructions:** `docs/synthetic-data-pool.md`, every
  `docs/brief-*.md`, `docs/goal-*.md`, `docs/GOAL-*.md`, `docs/iteration-campaign.md`,
  `docs/research-digest.md`, `docs/index-redesign-brief.md`,
  `docs/synthetic-content-update-final-report.md`, `docs/fictional-resume-data.md`,
  `docs/superpowers/`, `.hermes/plans/`, and the older sections of `STATUS.md`. They
  belong to the portfolio idea.

## Working notes

- Serve from the repo root so `/shots/` and `/vN-*/` resolve. Pages also work from `file://`.
- The gallery's hover preview loads a live iframe of the site. It only starts on a fine
  pointer with hover, so a headless browser needs that media emulated to test it.
- The rail repeats the six tiles three times per copy so the strip is wider than the
  screen and loops without a gap. Add a seventh site and it still works; drop below
  about four and it will not.
- Each site is one self-contained `index.html`. Some have a `<noscript><style>` block as
  well as the main `<style>`, so check which one you are editing.
- After changing a site's hero, retake its card screenshot: load the site at 1280×800,
  wait about four seconds for the intro to settle, save to `shots/<folder>.png`.
- The gallery's card scenes are CSS under `.card--vN` in `index.html`. Styles for the
  cards that were removed are still in the file, unused.
