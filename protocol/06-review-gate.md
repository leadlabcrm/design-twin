# 06 — The Review Gate

You are now the original designer, tired, protective of your craft, reviewing a PR from someone
claiming to have matched your style. You are looking for reasons to REJECT. Run the full
scorecard (`templates/review-scorecard.md`) — every item, evidence required, no "looks fine."

**Protocol:** any HARD item fails → fix → re-run the ENTIRE gate (fixes cause regressions).
Deliver only after two consecutive fully-green passes. Never show the user a version that has
not passed.

## How to review (method, not vibes)

For each check, do the comparison mechanically:

- **Side-by-side value diff:** for the new section and its clone source, extract and compare
  actual values from the code — font-size/weight/line-height per text tier, paddings, gaps,
  colors, radii, shadows, durations, easings. Any value not traceable to the DNA closed sets
  is a fail.
- **Structure diff:** compare DOM skeletons (tag nesting, class stacks, data attributes,
  wrapper depth) between new section and clone source. Unexplained divergence = fail.
- **Breakpoint sweep:** verify the new content at EVERY breakpoint the file supports —
  duplicated-DOM variants all updated, visibility classes correct, per-breakpoint values match
  the neighbors' per-breakpoint pattern.
- **Motion trace:** every new animated node registered in the file's mechanism; params equal to
  sibling params; no orphaned opacity-0 states; unique appear-ids.
- **Voice read-aloud:** read all new copy immediately after reading three existing sections'
  copy. Same author? Casing, punctuation, CTA verbs, sentence length all consistent?
- **Integrity pass:** file parses (balanced tags), scripts/JSON valid, no duplicate ids, no
  broken hrefs/anchors, untouched regions byte-identical, no comments/TODOs introduced.
- **Browser pass (when tools available):** load the file. Screenshot the new section between
  its neighbors at desktop AND mobile widths. Compare alignment edges, rhythm, type sizes
  optically. Watch the entrance animation fire. Check console for new errors.

- **Diversity pass (HARD, for added sections):** name each new section's layout archetype.
  Fail if a new section shares its archetype with an adjacent section, or if any archetype now
  appears more times on the page than the designer's own pages ever use it. "Same skeleton,
  different words" counts as the same archetype — check the DOM, not the copy.
- **Novelty pass (HARD, for added sections):** diff the new section's DOM skeleton against
  EVERY existing section. If it is ≥90% identical to any one of them, it is a re-skin, not a
  design — fail, return to the Design Studio (04 §0), and produce a real concept. Exception:
  the user explicitly asked for "another one like X".
- **Model-consistency pass (HARD, for added sections):** check the built section against the
  Designer Model: every applicable decision rule honored, zero "nevers" violated, tensions
  resolved the designer's way. Quote the specific rules checked and the evidence in the built
  markup.

## The five killer questions (answer in writing on the scorecard)

1. If the designer scrolled past this section tomorrow, would anything make them stop?
2. Is there any value in the new code that exists nowhere else in the file? (Search to prove.)
3. Does the section exist and behave correctly at every breakpoint?
4. Does the entrance animation match its neighbors parameter-for-parameter?
5. Could a reader of the raw HTML spot where the "different author" starts? (Naming, comment
   style, attribute order, indentation, class dialect.)

A confident "no issue" backed by evidence on all five → gate passes. Anything hedged
("should be fine", "probably") is a fail by definition — go verify it.

---

## The Parameter Matrix (run in full, every pass)

Fifteen parameters. Each gets PASS / FAIL / UNVERIFIED-with-reason plus one line of evidence
(a measured value, a search count, a screenshot ref). ALL P-checks marked HARD must pass;
UNVERIFIED is allowed only for checks that genuinely cannot be run (say why), never as a
shortcut. Compare against the Reference Capture baseline (00), not against memory.

| # | Parameter | HARD | How to verify |
|---|-----------|------|---------------|
| P1 | Typography fidelity | ✔ | Computed font/size/weight/spacing of every new text tier ∈ measured type table; unchanged elements byte-identical |
| P2 | Color discipline | ✔ | Scan built markup: every color literal ∈ palette, correct format, tokens used where the file uses tokens; zero foreign colors |
| P3 | Spacing & rhythm | ✔ | Every pad/margin/gap ∈ spacing set; new section's vertical rhythm within the pattern of its neighbors |
| P4 | Surface (radius/border/shadow) | ✔ | Exact string matches to the closed sets |
| P5 | Motion fidelity | ✔ | Entrance/hover/stagger params equal to siblings; runtime-dependent mechanisms (fit-text, appear runtimes) not used in static clones; nothing stuck at initial state |
| P6 | Voice & copy | ✔ | Read new copy against 3 existing blocks: casing, punctuation, CTA verbs, heading length in designer's range; no banned filler; no invented facts/quotes |
| P7 | Archetype (diversity/novelty/model) | ✔ | Named archetype differs from both neighbors; DOM skeleton <90% match to any existing section; Designer Model rules quoted and honored; zero "nevers" |
| P8 | Responsive integrity | ✔ | All breakpoint variants present/wired; no horizontal overflow at 375/810/1200 (measure scrollWidth); per-breakpoint values follow neighbors |
| P9 | Hydration integrity | ✔ | Text edits applied to EVERY copy (HTML, JS chunks, handover, search index — grep-proven); new DOM present 5s after load and after a forced re-render; placement stable (no observer shuffle) |
| P10 | Links & wiring | ✔ | Every new href resolves (no dead pages/#), tel/mailto/maps/socials are the client's real ones, ids unique, forms post somewhere real or are flagged |
| P11 | Assets | ✔ | Referenced files exist locally; no foreign hotlinks; alt text truthful to the actual image; banned imagery (per client) absent |
| P12 | Meta & brand sweep | ✔ | title/desc/OG/canonical updated; case-insensitive sweep for old template brand across text, attributes, JSON and search indexes returns only intentional leftovers (URL slugs), each listed |
| P13 | Untouched-region stability | ✔ | Diff shows changes only where the task required them; no reformatting drift |
| P14 | Optical parity | — | Screenshots (or DOM-geometry probes where capture fails) at 2 breakpoints: alignment edges, rhythm, type scale vs Reference Capture |
| P15 | Weight & console | — | No new console errors vs baseline; page-weight delta reported; no new blocking scripts |
| P16 | Wireframe conformance (when a wireframe was given) | ✔ | Built page walked against the Wireframe Read: every region present in order with all drawn elements realized or flagged; every taste-over-sketch deviation justified by a quoted Model rule (protocol/08) |

**Protocol:** run P1–P15 → fix all HARD fails → re-run the ENTIRE matrix. Two consecutive
all-green (or green + justified-UNVERIFIED) runs required. The filled matrix ships with the
delivery — the user should be able to audit every line.
