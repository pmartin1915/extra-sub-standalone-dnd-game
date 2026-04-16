# DISPATCH.md -- extra-sub-standalone-dnd-game

> Claude-owned sandbox. Real D&D game with balanced mechanics and teaching toggle.
> Read CLAUDE.md first.

## Pre-Approved Tasks (No Confirmation Needed)

| Task Keyword | Description | Success Criteria | Delegate To |
|---|---|---|---|
| `explore` | Research D&D mechanics, game engine patterns, balance systems | Notes written to `ai/` | `gemini-2.5-pro` |
| `research` | Deep research on combat math, encounter design, progression curves | Research note in `ai/` | `gemini-2.5-pro` |
| `audit` | Review existing code for bugs, balance issues, quality | Report written to `ai/` | `gemini-2.5-pro` |
| `tests-gen` | Generate test cases for combat math, character creation, dice system | Tests pass | `codestral-latest` |
| `docs-gen` | Generate or improve documentation | Docs written | `mistral-large-latest` |
| `self-audit` | Read STATE.md and assess progress vs roadmap | `ai/AUDIT.md` updated | `gemini-2.5-pro` |
| `roadmap-review` | Evaluate roadmap items, re-scope as needed | ROADMAP.md updated | `gemini-2.5-pro` |

## Requires Confirmation (Never Auto-Execute)

- `deploy` -- no deployment
- `delete` -- no file deletion without Perry's approval
- `install` -- no dependency changes

## Path Firewall

Autonomous work may only read/write files under:
```
c:\Users\perry\DevProjects\sandbox\extra-sub-standalone-dnd-game\**
```

## Opportunistic Lane (Budget Dispatcher)

**Eligible for autonomous execution:** `explore`, `research`, `audit`, `tests-gen`, `docs-gen`, `self-audit`, `roadmap-review`

**Branch naming:** `auto/sandbox-dnd-game-<task>-<YYYYMMDD-HHMMSS>`

**Commit prefix:** `[opportunistic][dispatch.mjs][<model>]`
