---
name: how
description: "Use for \"how does X work\", code walkthroughs before changing something, and placement / ownership / layering questions (\"where should this live\", \"which package owns this\", \"is this the right layer\"). Explains subsystem architecture, runtime flow, and onboarding mental models."
---

# How

Explore the codebase to answer "how does X work?" questions.

If the scope is ambiguous, state your interpretation and explore. The user can redirect.

## 1. Explain

Spawn one read-only general-purpose subagent that explores and explains in one pass (`Task` with `subagent_type: generalPurpose` and `readonly: true` in Cursor, `Agent` in Claude Code, `task` in OpenCode, `spawn_agent` in Codex, `invoke_subagent` with `TypeName: "research"` in Antigravity). If your harness has no subagent tool, do the exploring and writing yourself. Give it the user's question and this brief:

> You are writing an architectural explanation for a senior engineer. Explore the codebase and write an explanation that a senior engineer unfamiliar with this area could read and walk away with a solid mental model. They should understand the architecture well enough to start working in it confidently. You have read-only access to the codebase.
>
> Write the entire explanation in plain everyday language without jargon or technical terms. Whenever a technical term cannot be avoided, explain what it means in one plain sentence the first time you use it.
>
> When the question involves a runtime flow, request lifecycle, or multi-step process, include:
> - A simple Mermaid flow diagram (`flowchart TD/LR` or `sequenceDiagram`) written in plain words so anyone unfamiliar with this area can follow what happens from start to finish (main path and key error stops, without overloading boxes with jargon or low-level details).
> - A simple step-by-step pseudocode walkthrough of the flow using plain language and flat `if / else` steps, with the real file and function name noted next to each step so the reader can jump straight into the code.
> Skip diagrams and pseudocode only for pure placement or ownership questions (for example, "which package owns this?").

## 2. Present

Present the subagent's output. Light edits for clarity or context from the conversation are fine. Do not substantially rewrite it.
