# research results

**Date:** 2026-04-25 (UTC)
**Project:** sandbox-dnd-game
**As of:** Analysis of initial project scaffold

## Research Report: Project State and Opportunities

### Executive Summary

The `sandbox-dnd-game` project is in its initial, pre-development phase. The project charter (`CLAUDE.md`) and `ROADMAP.md` are well-defined, providing a clear vision and a phased plan. The core concept of a playable D&D-style game with an optional "Teaching Toggle" is strong.

However, no code, tests, or detailed design documents exist yet. The project is a clean slate. The immediate priorities are to establish the technical foundation (project structure, configuration) and begin formalizing the core game mechanics in design documents before implementation. Planning for comprehensive testing and documentation from the outset will be critical for success.

### 1. Current State Analysis

- **Project Phase:** Pre-development. The project was recently scaffolded and contains only planning and charter documents.
- **Codebase:** No source code (`src/`), tests, or build artifacts exist.
- **Progress vs. Roadmap:** The project is at the very beginning of "Phase 1: Core Mechanics Design". None of the roadmap items have been completed.
- **State File (`ai/STATE.md`):** The state file accurately reflects the current situation, correctly identifying that the next steps involve designing core mechanics and creating the project structure (`package.json`, `tsconfig.json`).
- **Strengths:** The project has a clear charter, a well-thought-out roadmap, and a defined automation process (`DISPATCH.md`). The "Teaching Toggle" and the planned integration with the `worldbuilder` project are excellent, forward-thinking features.

### 2. Opportunities for Improvement

1.  **Formalize Core Mechanics Design:** The roadmap lists "Design..." tasks. These should be captured in dedicated design documents before implementation begins. This creates a blueprint for development and ensures consistency.
    - **Recommendation:** Create a `design/` directory. Start with `design/CORE_MECHANICS.md` to detail the dice system, ability scores, modifiers, and combat resolution formulas.

2.  **Define Key Data Structures Early:** Defining the core TypeScript interfaces for concepts like `Character`, `Item`, `Ability`, and `Combatant` will enforce a consistent data model and facilitate modular development.
    - **Recommendation:** Create an initial `src/interfaces/` directory and define placeholder interfaces (e.g., `src/interfaces/character.ts`, `src/interfaces/combat.ts`).

3.  **Specify the Lore Adapter Interface:** The charter wisely suggests designing the `worldbuilder` integration interface early. This should be formalized to guide both projects.
    - **Recommendation:** Create `design/LORE_ADAPTER_SPEC.md`. This document should define the expected JSON schema for lore elements like NPCs, locations, and factions that the game will consume.

### 3. Missing Tests Analysis

As there is no code, there are no tests. This is expected. However, a testing strategy should be established now to guide development.

**Recommendations for Future Test Coverage:**

-   **Unit Tests (High Priority):**
    -   **Dice Roller:** Test various notations (e.g., `d20`, `2d6`, `4d6-L` for "drop lowest"), including valid and invalid inputs, and correct calculation of modifiers.
    -   **Character Model:** Verify that ability score modifiers are calculated correctly from base scores. Test that bonuses from race, class, and equipment are applied properly to stats like AC and HP.
    -   **Combat Logic:** Create pure functions for combat calculations (e.g., `calculateHit(attackRoll, AC)`, `calculateDamage(damageRoll, resistance)`) and test them exhaustively with edge cases (critical hits, misses, vulnerabilities).

-   **Integration Tests:**
    -   **Character Creation:** Test the full flow to ensure a generated character has valid, consistent stats.
    -   **Combat Encounters:** Simulate a full combat round to ensure initiative, turns, attacks, and status effects interact correctly.

-   **Feature-Specific Tests:**
    -   **Teaching Toggle:** This is a critical feature. Tests should assert that the game's output string format changes correctly based on the toggle's state for various game events (attack rolls, saving throws, etc.).

### 4. Documentation Gaps

The project currently lacks any technical or developer-focused documentation.

1.  **Project Setup Guide:** A file is needed to instruct a developer (or an automated agent) on how to set up the development environment, install dependencies, and run the application/tests.
    - **Recommendation:** Create a `SETUP.md` or `CONTRIBUTING.md` file outlining the steps to run `npm install` (once approved), `npm run build`, and `npm test`.

2.  **Architecture Overview:** A high-level document describing the intended software architecture would be valuable.
    - **Recommendation:** Create an `ARCHITECTURE.md` file that outlines the main components (e.g., `GameEngine`, `State`, `Renderer/UI`, `CombatSystem`) and their interactions.

3.  **Code-Level Documentation:** As development begins, a standard for TSDoc/JSDoc comments should be adopted to ensure the codebase is self-documenting.

### 5. Recommended Next Actions

Based on this analysis, the following actions are recommended to move the project forward effectively:

1.  **Create Project Structure:** Initialize a Node.js project by creating `package.json` and `tsconfig.json`. Define basic scripts for building and testing.
2.  **Begin Design Documentation:** Create the `design/` directory and start `design/CORE_MECHANICS.md` to document the dice and combat rules.
3.  **Implement Dice Roller:** Develop the first piece of the engine, the dice roller, as it is a foundational utility for all other mechanics.
4.  **Add Dice Roller Tests:** Immediately create unit tests for the dice roller to establish a test-driven development pattern for the project.
5.  **Define Core Interfaces:** Create the `src/interfaces/` directory and define the initial data structures for characters and combatants.
