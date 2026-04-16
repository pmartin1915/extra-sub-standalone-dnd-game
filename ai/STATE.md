# STATE -- extra-sub-standalone-dnd-game

## Current Context

Freshly scaffolded on 2026-04-16. No code yet. The first dispatch cycles should:
1. Read CLAUDE.md and ROADMAP.md to understand the charter
2. Research D&D-style game mechanics and balance systems
3. Design the core combat and character systems
4. Begin implementation with dice rolling and ability scores

## What's Done

- [x] Scaffold created: CLAUDE.md, DISPATCH.md, ai/STATE.md, ROADMAP.md

## What's Next

- [ ] Design core mechanics: dice system, ability scores, AC, attack resolution
- [ ] Design character creation flow
- [ ] Create project structure (package.json, tsconfig)
- [ ] Implement dice roller and modifier system

## Bridge to Worldbuilder

- Sister project: `extra-sub-standalone-worldbuilder`
- Worldbuilder creates the setting; this game uses it
- For now: use placeholder setting, design lore adapter interface
- When worldbuilder has lore ready, integrate via the adapter
