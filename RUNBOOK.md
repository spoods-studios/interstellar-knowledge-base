# Runbook — interstellar-knowledge-base

Expert-reviewed educational content — equations, articles, and
translations — backed by a SQLite content store. The educational-platform
half of the product. Currently a **dormant scaffold**: no KB schema,
articles, or content pipeline yet. Activates at **M2.3 (Three-Tier UI +
knowledge base MVP)**, when the SQLite content store comes online with an
initial 20-30 entries.

## Skills available here

| Skill | What it does |
|---|---|
| `/kb-start` | Auto-fires on the first turn of any session here. Reads `vault/context.md` + `vault/conventions.md`, checks `vault/decisions/` for recent entries, surfaces git status and `.planning/STATE.md` (if present), prints a compact briefing. |
| `/kb-end [--discard]` | Session close — appends `vault/learnings/sessions.md`, captures any gray-area decision to `vault/decisions/`, commits (no push). `--discard` skips all writes. |
| `gsd-*` phase-loop ceremonies (`gsd-new-milestone`, `gsd-discuss-phase`, `gsd-plan-phase`, `gsd-execute-phase`, `gsd-verify-work`, `gsd-code-review`) | Seeded once `/bootstrap-repo kb` activates this repo. |

## Lifecycle & gate tier

**Tier t3 — Standard Review** (`gate-tiers.md`). Milestone close needs a
standard `gsd-code-review` run for the schema/pipeline code, plus a plain
checklist review for content (scientific accuracy, entry completeness). No
mandatory multi-vendor grid, no mandatory playtest. Bugs/inaccurate content
still block; cosmetic nits don't.

**Activation flow:** `/bootstrap-repo kb` from a studio session →
`gsd-new-project` fed the PRD/Roadmap sections scoped to this repo →
`gsd-new-milestone` per the org manifest's knowledge-base slice (M2.3).

## What do I do next?

| State | Action |
|---|---|
| Repo still dormant | Nothing to do here — work starts once M2.3 routes through `/bootstrap-repo kb`. |
| Just bootstrapped | Run `gsd-new-milestone` using the manifest's knowledge-base slice. |
| Mid-milestone | Check `.planning/STATE.md`, then run the next phase: `gsd-discuss-phase` → `gsd-plan-phase` → `gsd-execute-phase` → `gsd-verify-work`. |
| Phase complete | Standard review — `gsd-code-review` or a plain content checklist. No playtest gate at this tier. |
| Milestone slice complete | File the review record, then run `/studio-milestone status` in `studio` to write back the slice and get the `Next up:` line. |
| Session ending | `/kb-end` (or `--discard` for a purely exploratory session). |
| Unsure | Read `../studio/RUNBOOK.md`. |

## Org context

- `../studio/RUNBOOK.md` — org-wide skill catalog + current state
- `../studio/vault/project/Milestone Playbook.md` — full open → close → devblog tutorial
- `../studio/vault/project/gate-tiers.md` — full tier definitions (this repo is t3)
- Standing obligations auto-surface at every session start via the SessionStart hook — nothing to run to see them.
