# Design briefs

A **brief** is the short markdown prompt that Claude Design turns into a UI canvas. It states *what* the surface is and *why*, not *how* it looks — the design is the answer, the brief is the question.

## Lifecycle

```
proposed/   a brief awaiting (or in) design + build
shipped/    the surface has been designed, built, and merged
```

Move a brief `proposed/ → shipped/` when its surface lands. Keep it — a shipped brief is a record of intent that pairs with the canvas and the code.

## Writing one

Copy [`TEMPLATE.brief.md`](TEMPLATE.brief.md) to `proposed/<surface-name>.brief.md` and fill it in. Keep it to a page: the surface, the states it must cover, the primary user intent, and any hard constraints. Detail that belongs in the *design* (exact spacing, color, component choice) is Claude Design's job, not the brief's.

## Convention

- One brief per surface; name it after the surface (`week-planning.brief.md`, not `feature-1.brief.md`).
- Prose is one line per paragraph (repo documentation style).
- Link the resulting canvas from the brief once it exists, and the brief from the canvas — both ways.

## Technical decisions belong in an ADR, not the design

When a surface embodies an architecture or technical decision — an access model, a storage choice, a protocol, an integration — the brief names the **governing ADR** and instructs the design step to *reference* it. The design renders the decision; it does not invent, restate, or re-decide it. That keeps the rationale in one reviewable place and stops a mockup from quietly becoming the source of truth for a choice it isn't equipped to make. If no ADR covers a decision the surface depends on, write one first, then point the brief at it.
