# 02 — Pattern Inventory

The Design DNA is the palette; this inventory is the brushwork. Here you learn *how this
designer assembles* sections, so a new section is a recombination of their own moves.

## A. Section map

Walk the DOM top to bottom and list every major section:

```
#  | Name (data-framer-name / semantic guess) | Purpose        | Layout skeleton                  | Motion
1  | Hero                                     | headline + CTA | centered stack, 720px text col   | fade-up stagger 0/.1/.2s
2  | LogoBar                                  | social proof   | marquee, 32px logos, 64px gap    | infinite marquee 30s linear
3  | Features                                 | 3-col cards    | grid 3×, 24px gap, cards p:32    | fade-up on scroll, stagger .1s
...
```

For each section also note: background treatment (color band? gradient? same as page?),
vertical padding, container width, heading tier used, and how it separates from neighbors
(spacing only? border? background change?).

## B. Structural conventions

Answer each with evidence from the file:

1. **Section wrapper anatomy** — what does the outermost element of a section look like
   (tag, classes, data attributes)? Is there a consistent wrapper → container → content-stack
   nesting depth? New sections replicate this anatomy exactly.
2. **Heading block pattern** — do sections share a repeated intro pattern (eyebrow/label +
   heading + subtext, with specific gaps)? Extract it as a reusable recipe.
3. **Card anatomy** — icon/image position, text stack, padding, footer/CTA, hover.
4. **CTA placement** — do sections end with CTAs? Which variant, aligned how?
5. **Class naming** — Framer's generated classes (`framer-a1b2c3`) vs semantic classes. What
   would this file plausibly generate for a new node? (See 03 for how to mint new class names.)
6. **Style placement** — when this file styles a node, where does the CSS live (inline
   `style=""`, `<style>` block with generated classes, CSS variables on ancestors)? New styles
   go in the same place in the same way.
7. **Ordering habits** — CSS property order inside rules, attribute order on elements. Match it.

## C. The "nearest sibling" selection

For the requested change, explicitly pick:

- **Primary clone source:** the existing section closest in role and structure to what's being
  built (adding pricing? clone the features grid if it's the closest card grid).
- **Secondary sources:** where specific atoms come from (button from hero CTA, badge from nav,
  toggle from FAQ accordion).

Write these down. During BUILD you will copy the primary source's markup skeleton verbatim and
mutate content — not write a new structure from scratch. This single habit kills 90% of
"an AI wrote this" tells: wrong nesting depth, foreign class patterns, alien spacing.

## D. Compositional vocabulary — the designer's taste, made explicit

The inventory so far catalogs what exists. This step extracts the *moves* behind it, so a new
section can be a **fresh composition in the same taste** rather than a re-run of an existing
skeleton. Write down:

1. **Layout archetypes** — every distinct section skeleton in the file, named. Typical examples:
   statement stack (label + giant words + para + CTA), card grid with hover overlay, list rows
   with prices, big-numeral stats row, marquee of oversized words, editorial split (small label
   column + prose), people grid, full-bleed media mask, image-card rows. Count how many
   sections use each — this reveals the designer's defaults AND their limits.
2. **Contrast moves** — how the designer creates drama: giant serif vs tiny sans labels,
   cream-on-black inversion bands, dense sections vs near-empty ones, static vs moving.
3. **Rhythm rules** — how archetypes alternate down the page (rich → statement → rich…),
   where inversions land, how often a "loud" section is allowed.
4. **Recombination space** — which atoms travel between archetypes (the pill CTA appears in
   heroes and cards; the giant-word element appears in statements and marquees). New sections
   are built by RECOMBINING these — an existing archetype filled with a different atom set, or
   two vocabulary elements composed in a way the designer hasn't used yet but plausibly would.

## E. Asymmetries and quirks — keep them

Real designers are consistently *in*consistent: maybe one section's heading is 48px while the
rule says 40, maybe one card grid uses 20px gap instead of 24. Record quirks, and do not "fix"
them. If the new section neighbors a quirky section, matching the neighbor beats matching the
global rule. Perfect global consistency where the file has local quirks is itself a tell.
