# AgenticOS PMO

Obsidian-native PM workspace + methodology that drives the build of [AgenticOS](https://github.com/SethMK/agenticos). Replaces story-point fiction with **measured calibration** anchored to actual sub-agent token + time runs.

## What it is

A kanban + story decomposition workspace built natively in Obsidian, that an orchestrator (Claude Code session) reads + writes to drive single-story-at-a-time agentic builds.

Not a SaaS, not a hosted tool. A **rule set + file structure + agent contract** that any team can fork into their own Obsidian vault.

## Mental model

The agentic orchestrator runs the work. This vault is the **planning surface** the orchestrator + curator agent read + update.

- `boards/kanban.md` — the live board (5 columns)
- `product/` — PRD, goals, founding plan
- `epics/` — epic-level scope
- `stories/` — 1-3 point story files with structured front-matter
- `ceremonies/standups/` — daily progress notes (auto-written by curator agent)
- `exports/` — sanitised public-facing kanban + sample stories for `/how-it-was-built` view

## Story state machine

```
Backlog → Ready → In Progress → Review → Done
```

Single-story-at-a-time. No parallel work-in-progress. Each transition is logged by the `pm-curator` agent.

## Calibration table

| Bucket | Typical token + time profile |
|---|---|
| **S-inline** | Single-file edit, no QA — ~30-50k tokens, 5-15 min |
| **S-with-QA** | Single-file edit + Playwright — ~80-120k tokens, 20-40 min |
| **M-data** | Data-shape change, multi-file — ~120-180k tokens, 30-60 min |
| **M-frontend** | New component + integration — ~150-220k tokens, 40-70 min |
| **L-single** | Full feature, single agent — ~250-400k tokens, 1-2h |
| **Spike** | Time-boxed research — variable, no commit expected |

Floor observation: ~130k tokens for cold-rebuild + Playwright pass regardless of code surface area. Calibration replaces estimation theatre with measured reality.

## Reusable patterns

The workspace codifies four patterns that generalise to any multi-agent build:

1. **File-ownership contracts** — each sub-agent reads specific files, writes specific outputs, never cross-edits another agent's territory.
2. **Hand-off markers** — explicit STOP at end of each agent's run. Main thread approves before the next agent fires.
3. **Approval gates** — manual review checkpoints for design-dependent or high-confidence outputs.
4. **Verification logs** — every step writes a structured note for downstream agents (creates audit trail + debuggability).

## First-time setup (if you fork the pattern)

Open the vault in Obsidian. Install three community plugins:

- **Kanban** by mgmeyers — required for `boards/kanban.md`
- **Tasks** by schaeser — task queries inside story files
- **Dataview** — table queries over story front-matter

## Code

Code lives in a private repo. This public README documents methodology + agent contract.

Sister repo: [agenticos](https://github.com/SethMK/agenticos) — the actual build this PMO drives.

---

Built by [Marcin Kokott](https://linkedin.com/in/marcinkokott) — Head of Product & Delivery, Vazco.
