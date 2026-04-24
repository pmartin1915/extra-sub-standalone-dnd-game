# research results

**Date:** 2026-04-24 (UTC)
**Project:** sandbox-dnd-game
**As of:** Commit corresponding to the provided file states.

## Research Report: sandbox-dnd-game

### 1. Executive Summary

The `sandbox-dnd-game` project is in its initial scaffolding phase. The charter (`CLAUDE.md`) and high-level plan (`ROADMAP.md`) are well-defined and provide a clear vision. The project's goal is to create a playable, text-based D&D-style game with a unique "teaching toggle" feature.

As of 2026-04-24, no application code or project structure (`package.json`, `tsconfig.json`) exists. The project is poised to begin Phase 1 (Core Mechanics Design) and Phase 2 (Engine Foundation). This report identifies immediate next steps, opportunities to improve the development process, and a forward-looking analysis of testing and documentation needs.

### 2. Current State Analysis

*   **Project Status:** Pre-implementation. The project was scaffolded on 2026-04-16 and consists only of planning and charter documents.
*   **Core Objective:** Build a D&D-style game in TypeScript/Node.js, focusing on balanced mechanics and an optional, educational "teaching toggle" to explain dice rolls and rules.
*   **Roadmap Progress:** The project has not yet started Phase 1 ("Core Mechanics Design"). All checklist items in `ROADMAP.md` are unticked.
*   **Next Steps (per `ai/STATE.md`):** The immediate tasks are to design the core game mechanics and establish the technical project structure.
*   **Automation:** The `DISPATCH.md` file provides a clear framework for autonomous tasks like research, test generation, and documentation, which should accelerate development once the foundation is in place.

### 3. Opportunities and Recommendations

While the project is well-planned, the following actions can improve execution and ensure a robust, maintainable codebase.

#### 3.1. Project Initialization (Immediate Priority)

The most critical next step is to create the project's technical foundation. This unblocks all future coding tasks.

*   **Recommendation:**
    1.  Create a `package.json` file, defining the project name, version, and scripts (e.g., `build`, `test`, `start`).
    2.  Add core development dependencies like `typescript`, `ts-node`, and a testing framework (e.g., `jest` or `vitest`).
    3.  Create a `tsconfig.json` file with strict settings to ensure code quality.
    4.  Establish a basic directory structure, e.g., `src/` for source code and `tests/` for tests.

#### 3.2. Data-Driven Game Mechanics

To facilitate balancing and content expansion, game data should be externalized from the code.

*   **Opportunity:** The charter already anticipates integrating JSON data from the `worldbuilder` project. This principle should be adopted internally from the start for game mechanics.
*   **Recommendation:** Define game entities like monster stats, class abilities, and item properties in structured data files (e.g., JSON or YAML) within a `data/` directory. The game engine should load this data at runtime. This prevents hardcoding values and makes future tuning significantly easier.

#### 3.3. Formalize Design Documentation

The roadmap schedules "Document mechanics in a design doc" at the end of Phase 1. This process should be concurrent with design, not sequential.

*   **Opportunity:** A living design document created *during* the research and design phase will serve as the blueprint for implementation in Phase 2.
*   **Recommendation:** Create a `design/` directory. Begin populating `design/CORE_MECHANICS.md` immediately as decisions are made regarding dice, ability scores, and combat rules. This aligns with the `explore` and `research` tasks in `DISPATCH.md`.

#### 3.4. Define Core Interfaces Early

A strong, interface-driven architecture will make the system more modular and testable.

*   **Opportunity:** Before implementing concrete classes in Phase 2, define the core interfaces they will implement.
*   **Recommendation:** In the `src/interfaces/` directory, create initial TypeScript interface definitions for key concepts like `ICharacter`, `IAbility`, `IItem`, and the `ILoreAdapter` mentioned in the charter.

### 4. Missing Tests Analysis

No code exists, so no tests are missing. However, a comprehensive testing strategy should be planned now to guide development. The roadmap's call for "Unit tests for all combat math" is a good start, but can be expanded.

**Recommended Test Coverage by Phase:**

*   **Phase 2 (Engine Foundation):**
    *   **Dice Roller:** Test various notations (e.g., `d20`, `2d6+4`) and ensure results are statistically sound and within expected ranges.
    *   **Ability Score Modifiers:** Verify correct modifier calculation for any given ability score (e.g., 10 -> +0, 15 -> +2).
    *   **Combat Resolution:** Unit tests for attack rolls against AC (hit, miss, critical hit) and damage calculations.
    *   **Teaching Toggle:** Tests to confirm that output formatting changes correctly when the toggle is enabled/disabled.

*   **Phase 3 (Character & Combat):**
    *   **Character Creation:** Test the entire character generation flow to ensure stats are valid and starting packages (HP, equipment) are assigned correctly.
    *   **Turn Order:** Verify that initiative rolls correctly sort combatants.
    *   **Saving Throws & Conditions:** Test that saving throws succeed/fail correctly against a DC and that status conditions (e.g., "Blinded") apply their mechanical effects.

*   **Phase 4 (Progression & Content):**
    *   **Leveling System:** Test that characters gain the correct HP, abilities, and other benefits upon leveling up.
    *   **Inventory/Equipment:** Test that equipping/unequipping items correctly modifies character stats (e.g., AC, attack bonuses).

### 5. Documentation Gap Analysis

The project's high-level documentation is currently a strength. The following are recommendations for future documentation to maintain clarity as complexity grows.

*   **Gap:** No dedicated design document.
    *   **Recommendation:** As noted in 3.3, create a `design/` directory and begin documenting core mechanics immediately. This is the most significant current gap.

*   **Future Gap:** Lack of code-level documentation standards.
    *   **Recommendation:** Establish a standard for TSDoc comments on all public classes, methods, and interfaces. This will be critical for long-term maintainability. The `docs-gen` task in `DISPATCH.md` can be leveraged to enforce this.

*   **Future Gap:** No architectural overview.
    *   **Recommendation:** After Phase 2 is complete, create an `ARCHITECTURE.md` file. It should provide a high-level diagram and description of the main components (`CombatEngine`, `CharacterModel`, `GameLoop`, etc.) and their interactions. This will be invaluable for onboarding context for future development cycles.
