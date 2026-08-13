# Material Index — card scene build brief (parts contract)

You are building decorative "scene" pieces for 5 portfolio cards on a redesigned
index page. Each card represents one portfolio website, and its scene must
embody that website's visual material (glass, paper, signal, soil, etc).
The controller has already built the page skeleton. Your job is ONLY the
two part files listed in your goal. Do not touch index.html.

## Card anatomy (already built in the skeleton — do not modify)

Each card is an anchor with class card card--vN. Inside it:
  <div class="stage" aria-hidden="true"><!-- SCENE_XN --></div>
  <div class="body"> ... title, description, meta ... </div>

- The stage is position:relative, height ~200px desktop / ~170px mobile,
  overflow:hidden, border-radius inherited. Everything you draw inside it is
  position:absolute. The controller replaces the SCENE marker comment with
  your markup line, so your markup must be a SINGLE LINE of spans.
- The card body is skeleton-owned: never style .card, .stage, .body, .meta,
  h2, p, .foot or any non-cN- class.

## Your part files

1. MARKUP file: exactly 5 lines, one per card, in the order listed in your
   goal. Each line is one row of span elements, e.g.:
   <span class="c1-photo"></span><span class="c1-petal"></span><span class="c1-stamp">POSTAGE</span>
   - Every span must carry your card's prefix class (c1-, c2-, ...).
   - Text labels: short, 1-3 words, uppercase, kept inside a span.
   - Empty spans are fine. No newlines inside a line. No other elements.
2. CSS file: all rules for your cards, concatenated. First rule per card:
   .card--vN { --bg: ...; --ink: ...; --mut: ...; --line: ...; --m1: ...;
   --m2: ...; --m3: ...; }
   - You MAY add extra declarations inside your own .card--vN rule ONLY for
     theme-native needs: border-radius (e.g. 0 for the brutalist card),
     background gradients, backdrop-filter + translucent --bg for glass.
   - Every other rule must be scoped: .card--vN .cN-element { ... }
   - Define each class exactly once.
   - No :hover on the card itself (skeleton owns card hover). Scene hover
     reactions are fine: .card--vN:hover .cN-element { ... }, but ONLY inside
     @media (hover:hover) and (prefers-reduced-motion: no-preference).
   - Animations: max 2 per card, subtle, slow (3-8s loop), and they MUST live
     inside @media (prefers-reduced-motion: no-preference). Static frame must
     look good on its own.
   - Never write <style>, <script>, </tag or any <tag> text inside comments
     or strings. Keep comments plain words.

## Scene guidance

The scene is a tiny still life of the variant's world, drawn with CSS.
3-6 elements per card. Mix of shapes (borders, gradients, clip-path,
box-shadow for depth, repeating-linear-gradient for texture). Sizes in % of
the stage or small px values. Labels: font-family JetBrains Mono fallback
monospace, 9-11px, letter-spacing .1em.

## Verification you must run before reporting

1. Markup: exactly 5 non-empty lines; every class on every span starts with
   your card prefix; count occurrences of each class.
2. CSS: brace balance via
   python3 -c "s=open('PATH').read();print(s.count('{'),s.count('}'))"
   (must be equal); every cN- selector defined exactly once
   python3 -c "import re;print(re.findall(r'\.(c\d+-[a-z0-9-]+)',open('PATH').read()))"
   and every class used in markup appears in CSS and vice versa.
3. Report: files written, card count, class counts, brace counts.
