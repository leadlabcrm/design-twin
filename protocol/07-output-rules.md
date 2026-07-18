# 07 — Output Rules

Only reached after the review gate passes twice consecutively.

## Deliverables (all three, every time)

1. **The complete working file(s).** Full HTML, byte-complete — never fragments, never
   `<!-- rest unchanged -->`, never "add this snippet after line 234" (unless the user
   explicitly asked for a diff/snippet). If assets were added, list their expected paths.

2. **The filled review scorecard** (`templates/review-scorecard.md`) — with the actual evidence
   notes and the written answers to the five killer questions.

3. **Decision summary** — short, structured:
   - What was added/changed, where in the DOM.
   - **Provenance table:** each notable design decision → the existing pattern it was cloned
     from (e.g. "card layout ← Features section cards; entrance ← Features stagger 0.1s;
     button ← Hero primary CTA; section padding ← 120px rhythm").
   - Anything with **no precedent** in the file that required extension, and how it was handled.
   - Placeholders needing real content from the user (asset paths, copy to confirm, hrefs).
   - Anything the extractor had broken that was encountered (not fixed unless in scope).

## Honesty rules

- If a check could not truly be verified (e.g., no browser available to watch the animation),
  say so explicitly in the scorecard instead of marking it passed.
- If the change request conflicted with the design system (user asked for something the
  designer would never do), deliver the faithful version AND note the tension — don't silently
  produce off-brand work, don't silently override the user either.
- Report the review honestly: if the gate needed 3 fix loops, the summary says so and says what
  was caught. This is signal about fragile areas, not embarrassment.
