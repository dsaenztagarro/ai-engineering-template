# Designs — the Claude Design workflow

This folder is the **visual source of truth** for the project's UI, and the front of the delivery pipeline. UI is not hand-built ad hoc: it is **designed first with Claude Design**, then implemented against that design. `AGENTS.md` enforces this.

## The pipeline

```
brief (markdown)        Claude Design            design canvas            /epic skill
docs/designs/briefs/ ─▶ generates a high-  ─▶ docs/designs/*.html   ─▶  decomposes the canvas
proposed/*.brief.md     fidelity UI canvas     (self-contained,          into phased tickets,
                        vs the design system   the visual truth)         built & verified to match
```

1. **Brief.** Describe the surface, its states, and the intent in `briefs/proposed/<name>.brief.md` (see [`briefs/README.md`](briefs/README.md)). A brief is short — it's a prompt for the design, not a spec.
2. **Canvas.** Use **Claude Design** to turn the brief into a **high-fidelity, self-contained HTML design canvas** in this folder, rendered against the project's design system (tokens, components, typography). The canvas is what "done" looks like.
3. **Build to it.** `/epic` (or a normal ticket) implements the canvas. `AGENTS.md`'s design rules require matching it exactly — no colors, spacing, radii, or components outside the token set — and every interactive workflow the canvas shows gets a test (**design fidelity is verified, not assumed**).
4. **Promote.** When the surface ships, move its brief `proposed/ → shipped/`. A design decision worth keeping (a pattern, a contract) becomes an ADR.

## What Claude Design is, in this workflow

**Claude Design** is the step that *produces the design*: given a brief and a design system, it generates a polished, reviewable UI canvas as self-contained HTML you can open in a browser. In this template it plays one role — it makes the **visual source of truth** that the rest of the pipeline (`AGENTS.md` enforcement + `/epic` implementation) builds against. Without it, "build the UI" has no reference and fidelity can't be verified; with it, the design is an artifact in the repo, versioned alongside the code that implements it.

## The design system

<!-- FILL: where your design system lives — tokens, components, typography, foundation CSS —
     and how to reference it. If it is shared across several projects, point here. The canvases in
     this folder render against it; implementations must use its tokens, not hardcoded values. -->

## Conventions

- **Canvases are self-contained** `*.html` (inline everything) so they open with no build step and render identically for any reviewer.
- **ASCII diagrams** in the accompanying markdown, per the repo documentation style.
- Keep **one canvas per surface**; keep the brief next to it in `briefs/`.
- If this project has **no UI**, delete this folder and the design section of `AGENTS.md`; the `/epic` skill still works on markdown backend designs.
