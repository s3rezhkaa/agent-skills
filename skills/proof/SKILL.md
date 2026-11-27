---
name: proof
description: >-
  Require primary evidence for every claim, conclusion, and paragraph in the reply.
  Use when the user asks for "/proof", "prove it", "show evidence", "with proof",
  or demands verified facts backed by code quotes, command outputs, screenshots, or primary web sources.
---

# Proof

Zero trust in memory, guesses, or paraphrased summaries. Every factual claim, conclusion, or paragraph in your response must be backed by a primary artifact observed directly in this session.

## Core Rule

1. **Never answer from memory.** Do not claim how code works, what a command returned, what a UI shows, or what external docs say unless you read or ran it in this session.
2. **Attach proof to each claim.** Put the supporting evidence directly next to the sentence or paragraph it backs, not as a vague list at the end.
3. **Never hide gaps.** If a claim cannot be verified in this session, mark it explicitly as `[UNVERIFIED]` and state what is missing (no runtime access, blocked URL, unrun check). Never blend unverified guesses into verified statements.

## Evidence Required by Topic

### 1. Code, Architecture, and Config
- Give the exact file path and line range (`path/to/file#L10-L25`).
- Read the surrounding function or block first, then include a short **verbatim quote** of the exact lines that prove the behavior.
- For historical reasons ("why was it changed"), cite the commit hash, PR, or design doc and quote the relevant diff or note.

### 2. Runtime Behavior, Bugs, APIs, and Tests
- State the exact command you ran and paste a **fresh, unedited excerpt** of its output (exit code, test counts, HTTP response, DB row, or log line).
- For fixes and bugs, show failing-before and passing-after evidence when reproducible, or name the exact check you ran.

### 3. UI and Visual State
- Capture screenshots of the **exact target state** (after scrolling into view, clicking, triggering the toast/modal/error, or opening the relevant screen).
- **Inspect every screenshot yourself** (open the saved image file) before citing or attaching it, and state concretely what is visible in the frame.

### 4. Web Research, Libraries, Versions, and External Facts
- Link the **primary source** directly (official documentation, GitHub repo/release, RFC, or original author's post), not a secondary blog or redirect summary.
- **Read the target page itself** (via extract/fetch), never rely only on a search snippet.
- Quote the exact sentence, version, API signature, limit, or number from the page. If sources disagree, cite both URLs and state which one you trust and why.

## What Does NOT Count as Proof

- A `grep` or search match without reading the actual code/page context.
- A screenshot you generated or saved without opening and viewing it.
- "It compiles" or "lint passed" as proof that runtime behavior works.
- Stale logs, results from an earlier session, or another agent's unverified claim.
- Extrapolated timings, counts, versions, or API fields you did not directly observe.

## Reply Format

1. **Direct answer first**, in plain language, with inline proof on every claim (`file:line` + quote, command + output, inspected screenshot, or primary URL + quote).
2. **Unverified (only if applicable):** a short separate list of anything you could not verify in this session and why.
