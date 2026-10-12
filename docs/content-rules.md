# Content rules — demo sites

Every site in the gallery is a demo website for a business or a person that does not exist. This
file decides what such a site may say. It replaces `docs/synthetic-data-pool.md` and the
older briefs, which belong to the earlier "one portfolio, many styles" idea.

The rule in one line: **the business is invented and says so; I appear once, in the
footer credit, with real details.**

## 1. Where my real details go

Only in the notice at the very bottom of every site. It is small print, in the same
style as a copyright line, and it never appears as a banner or pop-up:

> Demo site. *Name* is a fictional *photographer / practice / coach*, and the names,
> prices and reviews here are made up for illustration. Designed and built by
> [Garvit Pandia](https://garvitpandia.me), who can build one like this for you.
> [See more demo sites](../index.html).

The six business sites use the shorter form "*Name* is a fictional *kind of business*.
Concept site designed and built by Garvit Pandia · Back to the gallery".

- Name: Garvit Pandia
- Link: https://garvitpandia.me

Nothing else of mine goes on a concept site: no email, phone, GitHub, LinkedIn, college,
employer, résumé or city. The gallery page (`index.html`) is the one place that carries my
contact links.

## 2. The fictional business or person

- **A fictional person is never me.** Portfolio demos are for an invented photographer,
  architect, coach and so on, with an ordinary name. Nothing on them describes my own
  education or work.
- **An invented person must not be a real, findable professional** in that trade. Search
  the name with the profession before using it.

- **The name must not belong to a real business** in the same trade or city. Search it
  before using it.
- **No real company, client, publication, award or person is named** as a customer,
  partner, reviewer or press mention. "A film festival" is fine; a named festival is not.
- **Testimonials carry a role, not a name** ("a guest from Pune", "an accountant in Surat").
- **Places may be real** (a hotel can be in Udaipur). Street addresses are invented and
  plainly so.
- **Email addresses use the `.example` domain** (`stay@kaagazhaveli.example`), which can
  never reach a real inbox. Phone numbers are left out or shown as an obvious placeholder.
- **Prices, stats and dates may be made up**, but they should be believable for that
  kind of business and consistent across the page. A room that costs ₹9,400 in the list
  costs ₹9,400 in the calculator.
- **Typefaces, software and standards may be named** where the site really uses them
  (a type tester may name the Google font it loads).

## 3. Forms and actions

- A form confirms on the page and says the site is a concept and nothing was sent.
- No form opens a mail client, posts to a server or stores what was typed, apart from a
  basket or preference saved in the visitor's own `localStorage`.
- "Book", "Buy" and "Start trial" buttons end in that same on-page confirmation. They
  never lead to a real payment or sign-up page.

## 4. Checks before a site counts as done

1. The footer credit is present, with both links working.
2. Zero hits for `garvit9829`, my phone number, `Garvit_Pandia_Resume`, `github.com/garvit-pandia`
   and `linkedin.com` in the site's `index.html`.
3. Every `mailto:` and every printed email address ends in `.example`. Input placeholders
   use `you@example.com`.
4. No college, employer, certificate or career timeline anywhere on the page, including
   the `<title>`, the meta description and the Open Graph tags.
5. Photographs are free-licence stock (Unsplash), saved in the site's own `img/` folder
   and credited in the notice. Nothing is hot-linked from a stock-photo host. A photo of a
   recognisable person is never captioned with an invented full name.
6. The site's feature has been used end to end in a browser, at desktop and phone width,
   with no console errors and no sideways scroll.
