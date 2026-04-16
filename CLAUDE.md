# extra-sub-standalone-dnd-game -- CLAUDE.md

This is a **Claude-owned sandbox project** built autonomously by the budget dispatcher.

## Charter

Build a **real, playable D&D game** with proper balanced mechanics. This is NOT a math-teaching app. It is an actual game that feels like a D&D session.

### Core Requirements

- **Real D&D-style mechanics:** d20 rolls, ability scores (STR/DEX/CON/INT/WIS/CHA), AC, saving throws, initiative, hit points, damage rolls
- **Balanced encounters:** actual challenge ratings, encounter difficulty scaling
- **Character creation:** race, class, ability score generation, starting equipment
- **Progression:** experience points, leveling, new abilities
- **Inventory and equipment:** weapons, armor, items with mechanical effects
- **Combat system:** initiative order, attack rolls, damage, conditions, death saves

### Teaching Toggle

An optional mode (**OFF by default**) that, when enabled, shows the math behind what just happened:

- **Toggle ON:** "You rolled 14 + 3 STR modifier = 17, beating the goblin's AC of 15. You hit!"
- **Toggle OFF:** "You hit the goblin."

The toggle should feel like a coach whispering in your ear, not a textbook interrupting the game. When off, the game flows naturally. When on, every roll and check is explained.

**Goal:** Someone who has never played D&D can turn the toggle on and learn how it works by playing. Someone who already knows can turn it off and just enjoy the game.

### Bridge to Worldbuilder

This project is designed to eventually use the world created by `extra-sub-standalone-worldbuilder` as its setting. For now, develop with a placeholder setting. When worldbuilder has produced enough lore, the dnd-game can import it.

- Sister project: `c:\Users\perry\DevProjects\sandbox\extra-sub-standalone-worldbuilder\`
- Integration: lore documents and structured data (JSON) from worldbuilder feed into this game's world, regions, factions, and NPCs
- For now: use generic fantasy placeholder names; design the lore adapter interface early so swapping in real lore is seamless

## Tech Stack

TypeScript, Node.js. Start text-based (terminal). Web UI can come later.

## In Scope

- Game design documents with D&D mechanics
- TypeScript source code under `src/`
- Unit tests for combat math, character creation, encounter balance
- Lore integration interfaces (for future worldbuilder connection)

## Out of Scope (NEVER)

- Editing files outside this sandbox
- Copying D&D copyrighted content verbatim (use D&D-inspired mechanics with original names)
- External API calls or paid services
- `npm install` without Perry's approval

## Hard Path Constraints

Claude may ONLY touch files under:
```
c:\Users\perry\DevProjects\sandbox\extra-sub-standalone-dnd-game\**
```

## State Files

- `ai/STATE.md` -- current context, what's done, what's next
- `ai/DECISIONS.md` -- append-only decision log
- `ROADMAP.md` -- longer-horizon goals and status
