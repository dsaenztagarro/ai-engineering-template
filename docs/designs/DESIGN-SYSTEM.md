# Design system & the Claude Design project

Consistency across a UI is only real if it's enforced when designs are *created*, not just at review. This project does that by binding a **Claude Design project** to a **design system**: every design is generated inside that project, so it inherits the system's components, tokens, and typography **by construction** — not by hoping each new design remembers to.

## The binding

<!-- FILL: record the real names so any agent or contributor generates designs in the right place. -->

- **Claude Design project:** `<project name>` — the Claude Design project all of this repo's UI designs are generated in.
- **Design system:** `<Design System name>` — the design system attached to that project; every generated canvas uses its components.
- **Source of truth:** `<where the design system is defined — in Claude Design, and/or a repo/path if you mirror it>`.

Designs generated **outside** the bound project don't inherit the system and must not be used.

## Why bind a project to a design system

- **Consistency by construction.** A design generated in the bound project reuses the system's real components (buttons, inputs, tables, tokens) instead of inventing look-alikes. Drift is prevented, not caught later.
- **One vocabulary.** Every surface speaks the same visual language — colors, spacing, radii, typography all come from one token set.
- **Cheaper review.** "Does this match the system?" is largely answered *before* implementation, because the design was generated from the system.

## Setup (once per project)

1. Create a **Claude Design project** for this repo — or reuse a shared one (see below).
2. **Attach a design system** to it: define the components, tokens, and typography, or point it at an existing system.
3. Record the project and design-system names under **The binding** above.
4. From then on, **generate every UI design inside that project** (the pipeline is in [`README.md`](README.md)).

## Shared vs per-project design system

- **Per-project** — the design system belongs to this repo. Simple; good when the UI is standalone.
- **Shared across projects** — one design system is reused by several repos so they look identical. Point **Source of truth** at the shared location; if you mirror its tokens into this repo for the build, note the mirror path and the rule: **edit the source, then mirror — never edit the mirror**.

<!-- FILL: which model this project uses, and the relevant paths. -->

## In the repo

The design system's canonical definition lives in Claude Design (and/or its shared home). Design **canvases** generated against it live in `docs/designs/` ([`README.md`](README.md)); this file records *which system* they must conform to. If your build needs the tokens locally, mirror them in and treat the mirror as generated — the source is the design system, not the copy.

## Enforcement

`AGENTS.md` requires that all UI is built to a canvas generated in the bound project, and that implementations reuse the design system's components and tokens — no off-system colors, spacing, radii, or components. A significant design-system decision (adopting one, sharing one across repos, a token contract) is worth an [ADR](../architecture/decisions/).
