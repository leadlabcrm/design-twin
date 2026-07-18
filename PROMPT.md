# The Prompt

Copy the block below into Claude, fill in the two `[...]` slots, and attach (or point to) the
extracted HTML file.

---

```
You are acting as the ORIGINAL DESIGNER of the attached website — not an assistant editing
someone else's file. Before doing anything, read and follow this protocol end to end, in order:

https://github.com/leadlabcrm/design-twin

Read every file in the protocol/ folder (00 through 07) and both templates. Then:

1. Study the attached HTML file and produce the full Design DNA worksheet
   (templates/design-dna.md) and Pattern Inventory (protocol/02) for THIS file.
   Do not write any new UI code until both are complete.

2. My change request:
   [DESCRIBE THE CHANGE — e.g. "add a pricing section after the testimonials section
   with 3 plans: Starter, Growth, Scale"]

3. Build the change following protocol/03 (Framer conventions), protocol/04 (build rules)
   and protocol/05 (motion fidelity). Reuse ONLY tokens, classes, structures, easings and
   durations that already exist in the file. Never invent new design values.

4. Before showing me anything, run the full review gate (protocol/06) using
   templates/review-scorecard.md — review the work as if you are the original designer
   doing a merciless QA pass on a junior's PR. If ANY hard check fails, fix it and re-run
   the entire gate. Loop until every hard check passes. Do not show me intermediate output.

5. Deliver per protocol/07: the complete working HTML file (no placeholders, no
   "rest unchanged"), plus the filled review scorecard and a short summary of exactly
   what was added/changed and which existing patterns each decision was cloned from.

File: [ATTACHED / path / link]
```

---

## Variations

**Small tweak (copy change, color-consistent swap, reorder):** same prompt — the protocol is
cheap for small edits because the DNA extraction can be scoped to the affected region, but the
review gate still runs in full.

**Multiple files / assets folder:** add: `The extraction includes an assets folder — keep all
asset paths working and place any new assets alongside existing ones following the same naming.`

**When Claude can render/preview (Claude Code, browser tools available):** add:
`You have a browser available — after the review gate passes on code inspection, open the file,
screenshot the affected area at desktop and mobile widths, and visually verify against the
neighboring sections before delivering.`
