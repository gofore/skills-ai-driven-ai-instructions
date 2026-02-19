## Step 1: Understand AI Instruction Files

Welcome to the "AI Instructions" lab! In this step, you'll learn about the importance of AI instruction files and how they work.

### 📖 Theory: The "Instructions" of Code

An AI instruction file acts as the persistent memory or "Instructions" for AI agents (like Claude Code, Cursor, or Copilot). Instead of repeating your tech stack, architectural preferences, and testing commands in every chat session, you define them once in a system-level file.

### Why use Instruction Files?
1. **Consistency:** Ensure the AI always uses the same naming conventions (e.g., PascalCase for components).
2. **Efficiency:** Save tokens and time by not repeating context.
3. **Safety:** Define boundaries (which files to avoid) and critical checks.
4. **Onboarding:** A new AI agent (or human) can quickly understand how to work with the codebase.

| Tool | Primary Filename | Purpose |
| --- | --- | --- |
| **Cursor** | `.cursor/rules/*.mdc` | Modular rules for specific file patterns (Modern). |
| **Claude Code** | `CLAUDE.md` | General instructions, commands, and project style. |
| **GitHub Copilot** | `.github/copilot-instructions.md` | Repo-wide coding standards for Copilot Chat. |
| **Universal Agent** | `AGENTS.md` | An emerging open standard for any agentic tool. |

## 🔍 Anatomy of an Instructions File

### 1. Role & Persona (Optional)
This defines the AI's "identity" and level of expertise. It sets the tone and expectation for all responses.

*   **Seniority:** "Act as a Senior Lead Full-stack Engineer with 10+ years of experience in TypeScript and React."
*   **Expertise:** "You specialize in high-performance, accessible, and maintainable code."
*   **Tone:** "Professional, direct, and slightly skeptical of over-engineering."

### 2. Code Style & Syntax Prefixes
This is the most impactful section. It prevents the AI from suggesting code that you’ll just have to refactor immediately.

*   **Language Specs:** "Use TypeScript for all logic; avoid `any` at all costs."
*   **Formatting:** "Use functional components with Arrow functions. No function keywords for React components."
*   **Library Preferences:** "Use Tailwind CSS for styling. Do not use inline styles or CSS modules."
*   **Modernity:** "Use the latest Next.js App Router patterns, not the Pages router."

### 2. Architectural Decisions
AI often defaults to the "simplest" solution, which might break your project's structure.

*   **Data Fetching:** "Always use Zustand for global state and TanStack Query for server state."
*   **Error Handling:** "Wrap all API calls in a standard Result type `{ data, error }` rather than throwing exceptions."
*   **Validation:** "Use Zod for all schema validation."

### 3. Communication & Output Rules
Tell Copilot how to talk to you. This saves time and reduces "chatty" noise.

*   **Verbosity:** "Be concise. Do not explain basic concepts unless I ask. Just provide the code and a brief explanation of the logic."
*   **Testing:** "Whenever you generate a new function, automatically provide a Vitest unit test for it."
*   **Comments:** "Do not add comments that state the obvious (e.g., // set the name). Only comment on complex business logic."

### What should NOT be included?
*   **Secrets/API Keys:** Never put sensitive data in these files.
*   **Large Data Samples:** Don't paste 1000 lines of JSON; describe the schema instead.
*   **Transient Info:** Avoid information that changes daily (like specific bug IDs).
*   **Generic Advice:** Avoid "write clean code." Be specific: "Follow SOLID principles, specifically Dependency Inversion."

### Distinguishing Instructions from Other Documentation
It's crucial to avoid duplicating content between your AI instructions and other project files like `README.md` or `CONTRIBUTING.md`. Redundancy leads to confusion and maintenance overhead when rules drift apart. The key is to remember the unique audience and purpose of each file.

| File | Audience | Purpose |
|---|---|---|
| `README.md` | **External Humans** (Users, Visitors) | **The "Storefront"**: What the project is, why it's useful, and how to get it running. |
| `CONTRIBUTING.md` | **Internal Humans** (Developers) | **The "Employee Handbook"**: How to contribute, coding philosophy, process, and setup. |
| `AGENTS.md` | **AI Agents** | **The "Kitchen Manual"**: Strict, machine-readable rules on *how to build*, what tools to use, and what patterns to follow. |

**Example: Describing the Tech Stack**

*   **In `README.md`:** A simple, human-readable list.
    > Our project is built with React, TypeScript, and Tailwind CSS.
*   **In `AGENTS.md`:** A set of strict, actionable directives for the AI.
    > - Use React functional components with arrow functions.
    > - All new code must be in TypeScript; do not use `any`.
    > - Use Tailwind CSS utility classes for all styling; do not write separate `.css` files.

Your AI instructions should be a set of *guardrails*, not a project encyclopedia. When in doubt, instruct the AI to reference the human-readable file (`README.md`, `CONTRIBUTING.md`) for context, rather than duplicating the content.

---

## 🤖 Prompting for Instructions

You can use an LLM to help generate these chapters. Here are some effective prompts:

**For Role & Persona:**
> "Based on our project's tech stack and goals, suggest a 'Role' description for an AI agent. We want someone who is obsessed with performance and accessibility."

**For Code Style:**
> "Analyze my `src/` directory and summarize the naming conventions and architectural patterns used. Format this into a 'Code Style' section for an AI instruction file. Ensure you cover Arrow functions vs function keywords and styling preferences."

**For Architectural Decisions:**
> "Review my data fetching and error handling patterns. Generate an 'Architectural Decisions' section that enforces the use of TanStack Query and Result types for API calls."

**For the complete file:**
> "Create a `AGENTS.md` for this project. Include a Tech Stack section based on my dependencies, and a Code Style section that enforces functional programming with arrow functions, Tailwind CSS, and Zod for validation."

### ⌨️ Activity: Create Your `AGENTS.md` File

Your task is to create an `AGENTS.md` file for a new project. This file will serve as the "source of truth" for all AI assistants.

1.  Create a new file named `AGENTS.md` in the root of this repository.
2.  Use your favorite AI assistant (like Claude, Cursor, or Copilot) to generate the content for this file. Use the following prompt:

    > "Generate an `AGENTS.md` file for a new project. It must include our tech stack (TypeScript, Node, React) and our preference for functional components. The file should include sections for: Role, Tech Stack, Code Style, Architectural Decisions, and Communication."

3.  Commit and push the new `AGENTS.md` file to your repository.

Once you've pushed the file, a GitHub Actions workflow will automatically check your work.
