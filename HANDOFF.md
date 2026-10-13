# The Material Index — current state

**Last updated:** 2026-10-13
**Folder:** `/home/garvit/projects2/portfolio-gallery`
**Branch:** `concept-sites` (from `main`). Committed and pushed to GitHub, ten sites, as of 2026-10-12.
**Local server:** `http://127.0.0.1:5186/` (`python3 -m http.server 5186`, registered in `../PORT-REGISTRY.md`)
**Live:** https://garvit-pandia.github.io/p/ (GitHub Pages, serves `origin/main` from the repo root)
**Preview:** https://material-index-git-concept-sites-garvits-projects-1883ee4b.vercel.app/ (Vercel project `material-index`, connected to the GitHub repo; every push to `concept-sites` rebuilds it, and it opens without a login)
**Own addresses:** https://meera-kapoor.vercel.app, https://arjun-sethi.vercel.app and https://hitesh-clinic.vercel.app (three more Vercel projects on the same repo, each with its Root Directory set to the site's folder and `concept-sites` as production branch; the same push rebuilds them)

---

## The idea changed

The repo used to be "the same portfolio, fourteen ways". Every variant needed a full set
of career details, and the placeholder copy invented a college, employers and
certificates under my real name. That was the wrong shape for what I want to show.

The direction settled on 2026-10-12: the gallery is a mix of **demo sites for fictional
businesses and for fictional people** (a photographer, an architect, a coach), aimed at
freelance clients who want a site for their own business or for themselves. New sites are
designed from scratch for the profession rather than re-skinned from an old variant.

Each site is a **demo website for a fictional client**. The point is range:
different kinds of site, different styles, and one working feature in each. My own
details appear in one place only, a footer credit on each site. Nothing on a concept
site claims anything about my education or work history, so there is nothing to get wrong.

## What is in the repo on this branch

| Part | State |
|------|-------|
| `index.html` — the gallery | 10 site cards + 1 commission card that fills the rest of the last row. Rail, filters, shuffle and hover live preview all work. |
| `v13-origami-aurum/` | **Kaagaz Haveli**, hotel, Udaipur. Stay calculator at `#og-stay`. |
| `v16-black-box/` | **Saanjh Repertory**, theatre, Chandigarh. Seat map booking at `#booking`. |
| `v5-glass/` | **Kanch Invoicing**, software. Pricing slider and monthly / yearly switch at `#pricing`. |
| `v12-mycelium/` | **Dhingri & Co.**, mushroom farm, Solan. Shop `#myShop` and basket `#myBasket` (saved in `localStorage`). |
| `v10-typevolt/` | **Typevolt**, type foundry. Type tester at `#tester`, eight families on Google variable fonts. |
| `v8-abyss/` | **Paatal Dive Co.**, dive school, Andamans. Depth finder at `#finder`, depth rail 0 – 40 m. |
| `v19-photographer/` | **Meera Kapoor**, wedding photographer. Built from scratch. Photo wall with filters and viewer; date check at `#dates`. Photos in `img/`. |
| `v20-architect/` | **Arjun Sethi Architects**. Built from scratch. Project browser at `#work` with sheet and generated plan; estimate at `#contact`. Photos in `img/`. |
| `v21-fitness-coach/` | **Kabir Anand**, strength coach. Built from scratch. Plan finder at `#finder`; timetable at `#timetable`. Photos in `img/`. |
| `v22-clinic/` | **Hitesh Clinic**, chemist, lab and doctor's room, Indore. Built from scratch. Test slip at `#tests` / `#slip` (saved in `localStorage`), packages at `#checkups`, sample tracker at `#reports`, strip calculator at `#strip`, live doctors' timetable at `#doctors`. Photos in `img/`. |
| `shots/` | Fresh 1280×800 screenshots for the ten. The other twelve files are old and unused by the gallery. |
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
work is on GitHub Pages. The ten sites are on the Vercel preview above;
`material-index.vercel.app` still serves the earlier six-site deployment. The footer
link of the three stand-alone sites points there, so it shows six sites until the
gallery's production address is moved to this branch.

`garvitpandia.me` (project `../garvit`, `src/lib/data.ts`) describes this repo as
fourteen portfolios and shows a strip of them. That text and strip need updating when
this branch ships.

## Next

0. Review the three people sites and Hitesh Clinic on the Vercel preview. Still open: plainer names for the six
   business sites (Kaagaz Haveli, Saanjh, Kanch, Dhingri, Paatal read as forced), and which
   professions come next (fashion designer, author, music producer, filmmaker, travel
   planner, garden designer, podcast host were on the list).
1. Decide what happens to the twelve old folders: rebuild more of them as demo sites, or delete.
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
- The rail repeats the ten tiles twice per copy so the strip is wider than the
  screen and loops without a gap. Add a seventh site and it still works; drop below
  about four and it will not.
- Each site is one self-contained `index.html`. Some have a `<noscript><style>` block as
  well as the main `<style>`, so check which one you are editing.
- After changing a site's hero, retake its card screenshot: load the site at 1280×800,
  wait about four seconds for the intro to settle, save to `shots/<folder>.png`.
- The gallery's card scenes are CSS under `.card--vN` in `index.html`. Styles for the
  cards that were removed are still in the file, unused.
