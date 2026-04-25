# explore results

# Automated Exploration Report: sandbox-dnd-game

**Date:** 2026-04-25 (UTC)
**Project:** `sandbox-dnd-game`
**Report Type:** Initial Codebase & Architecture Exploration

## 1. Executive Summary

This report outlines the structure, architecture, and development plan for the `sandbox-dnd-game` project. As of this date, **no source code exists**. The project is in its initial design and planning phase, defined by a set of clear, well-structured markdown documents (`CLAUDE.md`, `ROADMAP.md`, `ai/STATE.md`).

The project's goal is to create a text-based, Dungeons & Dragons-style role-playing game using TypeScript and Node.js. Two key architectural pillars are evident from the planning documents:

1.  **The "Teaching Toggle":** A core feature that allows the user to switch between a narrative game experience and a verbose mode that explains the underlying game mechanics and math. This will fundamentally influence the design of the game's output and event logging systems.
2.  **The "Lore Adapter":** A planned interface to separate the game engine from the world content (lore, NPCs, locations). This is designed for future integration with a sister project, `extra-sub-standalone-worldbuilder`, and mandates a decoupled architecture from the outset.

Development is planned in a phased approach, starting with core mechanics design, followed by engine implementation, combat systems, and content integration. A significant operational constraint is the prohibition of unapproved `npm install` commands, which will heavily influence dependency choices.

## 2. Architecture & Design Decisions

Based on the project's charter and roadmap, the following architectural decisions and patterns are established or implied:

*   **Technology Stack:**
    *   Language: **TypeScript**
    *   Runtime: **Node.js**
    *   User Interface: **Text-based (Terminal)**

*   **Core Architectural Pattern: Decoupled Engine and Content**
    *   The "Bridge to Worldbuilder" requirement necessitates a clean separation between the game's rules engine and its narrative/world data.
    *   An abstraction layer, referred to as the **"Lore Adapter,"** will be crucial. This interface will define the data structures for world elements (e.g., `Region`, `NPC`, `Faction`, `Quest`) that the game engine will consume.
    *   Initially, this adapter will be fed by placeholder data. This is a sound architectural decision that promotes modularity and testability.

*   **Event-Driven Output for "Teaching Toggle"**
    *   To support the "Teaching Toggle," the game's event system cannot simply generate final output strings.
    *   A recommended pattern is for game actions (e.g., an attack) to generate a structured event object containing all relevant data (e.g., `{ roller: 'Player', target: 'Goblin', roll: 14, modifier: 3, total: 17, targetAC: 15, result: 'hit' }`).
    *   A separate rendering or logging module would then interpret this event object, generating a terse ("You hit the goblin.") or verbose ("You rolled 14 + 3 STR modifier = 17, beating the goblin's AC of 15. You hit!") string based on the toggle's current state.

## 3. Projected Codebase Structure

As no files exist, the following structure is recommended to align with the project's goals:

```
sandbox-dnd-game/
├── ai/
│   ├── DECISIONS.md
│   └── STATE.md
├── design/
│   ├── mechanics.md         # For Phase 1 design documentation
│   └── lore_adapter.md      # Documenting the world data interface
├── src/
│   ├── core/                # Dice, ability scores, fundamental types (e.g., d20.ts)
│   ├── character/           # Character models, creation logic, progression
│   ├── combat/              # Initiative, turn management, action resolution
│   ├── world/
│   │   ├── adapter.ts       # The lore adapter interface definition
│   │   └── placeholders.ts  # Default/placeholder world content
│   ├── io/                  # Terminal input/output handling, renderer for teaching toggle
│   └── main.ts              # Main game loop and entry point
├── tests/                   # Unit tests for mechanics, combat math, etc.
│   ├── core/
│   │   └── d20.test.ts
│   └── combat/
│       └── resolution.test.ts
├── CLAUDE.md
├── DISPATCH.md
├── ROADMAP.md
├── package.json
└── tsconfig.json
```

## 4. Dependencies

*   **Current:** There are no dependencies.
*   **Constraint:** The `DISPATCH.md` file explicitly forbids running `npm install` without manual approval. This is the single most significant technical constraint.
*   **Implications:**
    *   The project must be developed with a "zero-dependency" mindset where possible.
    *   Standard development tools like test runners (Jest, Vitest), linters (ESLint), or terminal styling libraries (`chalk`) cannot be added autonomously.
    *   **Recommendation:** For initial unit tests, leverage Node.js's built-in `assert` module to avoid needing an external test framework. This allows progress on the testing requirement without violating the dependency constraint.

## 5. Findings & Recommendations

### Findings

*   **Clear Vision:** The project has an exceptionally clear and well-documented vision, roadmap, and set of constraints.
*   **Pre-computation Phase:** The project is correctly positioned in a "design first" phase (`ROADMAP.md`, Phase 1), which is critical for a project with complex, interlocking mechanics.
*   **Architectural Foresight:** The plan for a "Lore Adapter" is a mature design choice that will prevent significant refactoring in the future.

### Recommendations

1.  **Establish Project Structure:** The immediate next step should be the creation of `package.json` and `tsconfig.json` to formally initialize the TypeScript project.
2.  **Begin Design Documentation:** Before writing any TypeScript, create `design/mechanics.md` and begin documenting the core rules for dice, ability scores, and combat resolution as outlined in Phase 1 of the roadmap. This fulfills the immediate "What's Next" item in `ai/STATE.md`.
3.  **Define the Lore Adapter Interface:** Concurrently, define the core TypeScript `interface`s for the lore adapter in `src/world/adapter.ts`. This will solidify the data contract early.
4.  **Implement the Dice Roller:** The first piece of implementation should be the dice roller module (`src/core/d20.ts`). It is a small, self-contained unit, perfect for establishing the build and test process. Create a corresponding test file (`tests/core/d20.test.ts`) using the built-in `assert` module.
5.  **Clarify Dependency Policy:** Seek clarification on a policy for adding essential development dependencies (e.g., a test runner like Vitest, or `ts-node` for execution). Proceeding without them is possible but will become inefficient as the project scales.
