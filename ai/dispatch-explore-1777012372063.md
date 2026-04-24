# explore results

# Exploration Report: sandbox-dnd-game

**Date:** 2026-04-24 (UTC)
**Project:** `extra-sub-standalone-dnd-game`
**Status:** Project Initialized. No source code present.

## 1. Project Overview

This project, `sandbox-dnd-game`, is a new, unstarted initiative to build a playable, text-based Dungeons & Dragons-style role-playing game. The core charter is to create a genuine game with balanced mechanics, not just a teaching tool.

A key feature is the "Teaching Toggle," an optional mode that explains the underlying math of dice rolls and checks to help new players learn the mechanics.

The project is designed to be developed autonomously by an AI agent, following a structured roadmap. The initial technology stack is specified as TypeScript and Node.js, with a focus on a terminal-based interface before any potential web UI.

## 2. Codebase Structure

As of this report, the project contains no source code. The directory structure consists only of project management and AI state-tracking documents:

```
.
├── CLAUDE.md       (Project charter, scope, and constraints)
├── DISPATCH.md     (Instructions for autonomous AI agents)
├── ROADMAP.md      (Phased development plan)
└── ai/
    └── STATE.md    (Current progress and next steps)
```

The immediate next step, as indicated by `ai/STATE.md`, will be to create the foundational project structure, including `package.json`, `tsconfig.json`, and the `src/` directory for TypeScript source code.

## 3. Key Architectural Decisions & Patterns

Analysis of the project documents reveals several key architectural decisions made at inception:

*   **Decoupled Lore Engine (Adapter Pattern):** The project explicitly plans for a "lore adapter interface." This is a critical decision that decouples the game engine from the world's content. It allows development to proceed with placeholder data while a sister project (`extra-sub-standalone-worldbuilder`) creates the canonical lore. This pattern will make it seamless to "plug in" the real world data later without refactoring the core game logic.

*   **Stateful Output (Strategy/Decorator Pattern):** The "Teaching Toggle" feature implies that all game output related to mechanical resolutions must support two modes: terse (game-focused) and verbose (educational). This will likely be implemented using a Strategy or Decorator pattern, where an `OutputManager` or similar service can be toggled between different output strategies. This needs to be a core consideration in the design of any function that communicates game events to the player.

*   **Text-First Development:** The decision to start with a terminal-based interface simplifies the initial development cycles by deferring the complexities of a graphical user interface. This allows the team to focus entirely on implementing and balancing the core game mechanics.

*   **AI-Driven, Phased Development:** The project is managed via a clear, phased `ROADMAP.md` and state is tracked in `ai/STATE.md`. This structured approach is designed for autonomous or semi-autonomous development, ensuring that foundational work (core mechanics design) is completed before implementation begins.

## 4. Dependencies and Integrations

*   **NPM Dependencies:** There are currently **zero** npm dependencies. The `CLAUDE.md` file contains a strict constraint: `npm install` is not permitted without explicit approval. This indicates the project will start with vanilla Node.js and TypeScript, adding dependencies only when absolutely necessary.

*   **Inter-Project Dependency:** The project has a significant, planned dependency on the `extra-sub-standalone-worldbuilder` project. The `dnd-game` will be the consumer of lore, characters, and world data produced by `worldbuilder`. The success of the lore integration hinges on the early and accurate design of the aforementioned lore adapter interface.

## 5. State and Roadmap Summary

*   **Current State:** The project is in its initial design phase. No code has been written. The immediate goal is to design the core D&D-style mechanics (dice, ability scores, combat resolution).

*   **Roadmap:** The roadmap is divided into five logical phases:
    1.  **Phase 1: Core Mechanics Design:** Defining the rules of the game.
    2.  **Phase 2: Engine Foundation:** Implementing the core rules in code (dice roller, character model, combat math).
    3.  **Phase 3: Character & Combat:** Building out the interactive gameplay loop (character creation, turn order, encounters).
    4.  **Phase 4: Progression & Content:** Adding depth (leveling, inventory, abilities) and the lore adapter.
    5.  **Phase 5: Polish:** Balancing, UI improvements, and documentation.

The project is currently at the very beginning of Phase 1.

## 6. Recommendations

Based on this exploration, the following are the logical next steps:

1.  **Establish Project Structure:** Create `package.json` (to define the project and scripts), `tsconfig.json` (to configure the TypeScript compiler), and a `src/` directory for the source code.
2.  **Begin Mechanics Design:** Create a design document (e.g., `design/CORE_MECHANICS.md`) to formalize the rules for dice, ability scores, and combat resolution, as outlined in Phase 1 of the roadmap. This should be done before writing implementation code.
3.  **Implement Core Utilities:** Once the design is clear, begin implementation with the most fundamental and reusable component: a robust dice roller module within the `src/` directory, complete with unit tests. This aligns with the first task in Phase 2.
