# 04 — Build Rules

You may only start here with a completed Design DNA worksheet, Pattern Inventory, and written
plan. Every rule below is a hard rule.

## 1. Clone atoms, compose sections — the diversity rule

Clone-first applies at the ATOM and ARCHETYPE level, never as "duplicate a whole section and
change the words." A page of near-identical skeletons with different copy is the #1 tell that
a template was stamped, not designed.

1. **Editing an existing section** → clone-in-place: keep its skeleton, mutate content only.
2. **Adding a NEW section** → pick its layout archetype from the compositional vocabulary
   (02-D), under these constraints:
   - Its archetype must **differ from both adjacent sections** in the final page order.
   - Prefer an archetype the page doesn't overuse. If the vocabulary is rich, a new section
     should usually introduce variety, not repeat the most common skeleton.
   - Two sections with the same skeleton and different copy = ONE archetype used twice.
     Twice on a page is the ceiling for any archetype unless the designer's own pages exceed it.
3. **Building the chosen archetype:** clone its skeleton from wherever it exists (any page of
   the site — cross-page cloning is expected), then fill it with atoms from the inventory.
   Every value still comes from the DNA closed sets; every atom from an inventory recipe.
4. **Novel recombination** is allowed and encouraged when it stays inside the vocabulary:
   an existing skeleton carrying a different atom set, or two vocabulary elements composed in
   a way the designer plausibly would (e.g. the giant-word element used as a stacked index).
   What is NOT allowed remains unchanged: foreign values, foreign class dialects, layouts with
   no basis in the file.
5. Repeat per breakpoint variant if the file duplicates DOM per breakpoint (03-4).

Composing fully from scratch is still the last resort (no comparable archetype anywhere in the
site) — atoms cloned, precedent gap flagged in delivery notes.

## 2. Closed sets are law

Before typing any literal value, check it against the DNA sets:

- font-size, weight, line-height, letter-spacing → from the type scale
- color → from the palette, in the file's format, via token/variable if the file uses them
- padding/margin/gap → from the spacing scale; section vertical padding on the section rhythm
- radius, border, shadow → from the surface sets, exact strings
- duration, delay, easing → from the motion sets, exact strings

If the perfect value seems to be missing (you "need" 28px in a 24/32 world): you don't. Pick
the set member the designer would use — usually the one used in the analogous position elsewhere.

## 3. Copy voice

Write all new copy in the voice profile from DNA §7. Match: heading length and casing, CTA verb
pattern, punctuation habits, "you/we" register, and the level of concreteness (real designers
rarely write "Lorem ipsum" or generic "Amazing feature that helps you succeed" — write copy as
specific as the site's real copy; if you lack facts, use the site's own domain language and
flag copy for the user to review). **Banned:** em-dash overuse if the site doesn't use them,
"seamless/effortless/unlock/supercharge" filler unless the site already talks like that,
exclamation marks the site doesn't use.

## 4. Every state, not just the happy render

For each interactive element you add: default, hover, focus-visible, active — matching the
sibling element's treatment exactly (same transition property list, duration, easing). If the
file does nothing on focus, you do nothing on focus (fidelity beats your preferences —
accessibility improvements are offered in notes, not silently injected).

## 5. Wiring completeness

- New nav items scroll/link correctly using the file's mechanism.
- New animated nodes are registered with the file's animation runtime (03-3).
- New content exists in every breakpoint variant with correct visibility classes (03-4).
- ids are unique; minted class hashes collide with nothing (search the file to confirm).
- No console errors: any script you touched still parses; any JSON blob you extended is valid.

## 6. Untouched code is untouchable

No reformatting, no re-indentation, no attribute reordering, no dead-code cleanup outside the
change. Your diff should read as: designer opened file, added/edited one thing, saved.

## 7. Placeholder policy

Real hrefs, real anchor targets, real copy. Where genuinely user-supplied assets are needed
(product screenshots, logos), reference them in the file's existing asset style with a clearly
flagged path (e.g. same-format `framerusercontent` sibling image reused, or `assets/…` path if
the extraction uses local assets) and list every such placeholder in delivery notes. Never ship
`href="#"` on a CTA whose siblings have real targets, never `TODO` comments — the file has no
comments; yours don't either (check: most Framer exports contain zero HTML comments).
