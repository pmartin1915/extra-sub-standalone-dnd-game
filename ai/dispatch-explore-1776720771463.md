# explore results

### **Project Exploration Report: sandbox-dnd-game**

**Objective:** Analyze the codebase structure, document key patterns, dependencies, and architecture decisions for the "sandbox-dnd-game" project.

**Status:** The project is in its initial scaffolding phase. No source code (`src/`) exists yet. This analysis is based on the project's charter, roadmap, and AI-driven development process files.

---

### **1. Project Summary & Goals**

The project's charter is to build a playable, text-based Dungeons & Dragons-style game using TypeScript and Node.js. The core mission is to create a genuine game experience with balanced mechanics, not just a simple educational tool.

**Key Features:**
*   **Core D&D Mechanics:** Implements d20-based systems for ability scores, attack rolls, saving throws, damage, and character progression.
*   **Teaching Toggle:** A unique, optional mode that explains the underlying math of game events (e.g., "You rolled 14 + 3 STR = 17, beating AC 15") for new players. When off, the game provides standard narrative descriptions.
*   **Future-Proofing for Lore:** Designed to integrate with a sister project (`extra-sub-standalone-worldbuilder`) via a "Lore Adapter" interface, allowing the game's setting to be swapped from a placeholder to a fully developed world.

---

### **2. Codebase & Directory Structure**

The project currently consists of documentation and state management files. The intended structure is as follows:

*   `/**`: Root directory containing high-level project governance documents.
    *   `CLAUDE.md`: The project charter, defining goals, scope, and constraints.
    *   `ROADMAP.md`: A phased development plan, from core mechanics to a polished game.
    *   `DISPATCH.md`: Defines the rules for the AI-driven development process, including pre-approved tasks and constraints.
*   `/ai/**`: A directory for AI state management and decision logging.
    *   `STATE.md`: Tracks the current development context, what's done, and immediate next steps.
    *   `DECISIONS.md` (Implied): An append-only log for architectural decisions.
*   `/src/**` (Planned): This directory will contain all TypeScript source code for the game engine, mechanics, and application logic.
*   `package.json` / `tsconfig.json` (Planned): Standard Node.js/TypeScript project configuration files are planned as the next immediate step.

---

### **3. Key Architectural Decisions & Patterns**

Several key architectural decisions have been made upfront, shaping the project's development.

1.  **Terminal-First Approach:** The initial implementation will be a text-based terminal application. This decouples the core game logic (the "engine") from the user interface, allowing a potential web UI to be added later without rewriting the engine.

2.  **State-Driven Output (Teaching Toggle):** The "Teaching Toggle" necessitates a flexible output system. The game logic must produce a structured result (e.g., `{ roll: 14, modifier: 3, total: 17, target: 15, success: true }`) which can then be rendered into either a verbose, educational string or a terse, narrative one. This pattern separates game mechanics from presentation.

3.  **Adapter Pattern for Lore Integration:** The plan to integrate with the `worldbuilder` project uses the **Adapter Pattern**. A well-defined `LoreAdapter` interface will be created. The initial implementation will use a `PlaceholderLoreAdapter`. Later, a `WorldbuilderLoreAdapter` can be developed to read data from the sister project. This makes the game engine agnostic to the source of its lore, ensuring a seamless future integration.

4.  **Phased Development Model:** The `ROADMAP.md` outlines a clear, multi-phase development strategy. This approach prioritizes building a solid foundation (core mechanics, engine) before adding more complex features (character classes, progression, content).
    *   **Phase 1:** Design
    *   **Phase 2:** Engine Foundation
    *   **Phase 3:** Combat & Character Features
    *   **Phase 4:** Content & Progression
    *   **Phase 5:** Polish

5.  **AI-Driven Development Framework:** The project utilizes a meta-architecture for its own development, defined in `DISPATCH.md` and `ai/STATE.md`. This system automates tasks like research, documentation, and test generation using specific AI models, while enforcing strict constraints (e.g., no unapproved `npm install`).

---

### **4. Dependencies**

*   **External (npm):** Currently, there are **no external dependencies**. The `DISPATCH.md` file explicitly forbids running `npm install` without manual approval, indicating a "zero-dependency" starting point.
*   **Internal (Project):** There is a planned dependency on the `extra-sub-standalone-worldbuilder` project for game lore and setting data. This is a one-way data flow dependency.

---

### **5. Recommendations & Next Steps**

Based on the current state, the immediate priorities are to establish the technical foundation of the project.

1.  **Project Initialization:** Create `package.json` (to define the project and scripts) and `tsconfig.json` (to configure the TypeScript compiler).
2.  **Directory Scaffolding:** Create the `src/` directory and subdirectories for core modules (e.g., `src/core`, `src/mechanics`, `src/character`).
3.  **Implement Core Mechanics:** Begin implementing the foundational elements as per Phase 2 of the roadmap, starting with a robust dice roller module. This is a critical, low-level component that almost all other systems will depend on.
4.  **Define Data Structures:** Design and implement the core TypeScript types and interfaces for `AbilityScores`, `Character`, `DiceRollResult`, etc. This will provide the data model for the rest of the engine.
