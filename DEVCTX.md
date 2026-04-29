# devctx

This repo uses the [devctx protocol](https://github.com/mzaid101/devctx) —
an agent-agnostic, repo-resident AI context layer.

## Rules for AI agents

1. **Read `.aictx/CURRENT.md` first** — max-compressed live project state (≤200 tokens).
2. **Write `.aictx/HANDOFF.md` before ending your session** — semi-compressed capsule for the next agent/session.

These two rules are mandatory. Everything else is optional.

## Context map

| Path | Purpose | Compression |
|------|---------|-------------|
| `.aictx/CURRENT.md` | Live project state | Max — ≤200 tokens, machine-first |
| `.aictx/HANDOFF.md` | Session capsule | Semi — human-readable summary |
| `.aictx/decisions/` | Architecture decision records | Full — rarely read |
| `.aictx/threads/` | Per-ticket compressed chat summaries | Medium |
| `.aictx/open/` | Blockers and unresolved questions | Full |

## Writing HANDOFF.md

At session end, overwrite `.aictx/HANDOFF.md` with:
Session Handoff — YYYY-MM-DD
What happened
<what was worked on, decisions made, code changed>

State left in
<branch, file state, test status, anything broken>

Next session should
<ordered list of next actions>
Dont touch
<files/areas that are fragile or in-progress>

Keep it honest and terse. The next agent will read this before anything else.
