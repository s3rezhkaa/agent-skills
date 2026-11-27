---
name: kiss
description: >-
  Keep code elementary, flat, and readable top-to-bottom with plain A1 English names and zero over-engineering.
  Use when writing, refactoring, or simplifying code in any language so a beginner or non-developer can follow
  every name and the full flow without decoding abstractions.
---

# KISS (Keep It Simple, Stupid)

Write code that reads like a plain story from top to bottom. Anyone with basic A1-A2 English and no background in the codebase should understand every name and the full flow without guessing.

**Applies to every language:** Java, Python, TypeScript/React, C#, SQL, shell scripts, and anything else. Only the casing convention changes (`camelCase`, `PascalCase`, `snake_case`), never the naming clarity.

**Core rule: write code ONLY from the simplest constructs.** Plain names, plain `if` and `for`, short functions, nothing clever. When a rule below doesn't cover a case, choose the simplest construct that works. The sections below are examples of this rule, not a complete list.

## 1. Plain A1-A2 English Names

A name says **what** the thing is or does in everyday words. If a name needs a verbal explanation or a dictionary, rename it.

- **Use everyday A1-A2 words, not fancy words or jargon:** prefer `load` over `fetch`, `delete` or `cancel` over `revoke`, `open` or `waiting` over `pending`, `old` over `expired`, `send` over `submit`, `left` over `remaining`, `check` over `validate`, `settings` over `configuration`. Keep a technical or business term only when the product itself uses that exact word (like `campaign`, `workspace`, `invoice`).
- **Classes, types, and components = clear role + subject.** Avoid empty nouns like `Manager`, `Helper`, `Processor`, `Handler`, `Data`, `Widget`, `Popup`, `Box`.
  - Java: `InvitationManager` -> `WorkspaceInviteEmailSender`, `TokenProcessor` -> `OldLoginTokenCleaner`
  - Python: `ReportHandler` -> `SearchQueryReportLoader`, `BudgetData` -> `DailyBudgetSummary`
  - React / TS: `InvitePopup` -> `WorkspaceInviteWindow`, `StatsWidget` -> `DailySpendChart`
- **Functions / methods = action + subject (+ condition or result).** Never bare nouns (`summary`, `report`, `orderItem`) or vague verbs (`process`, `handle`, `execute`, `doWork`, `run2`, `compute`). Use one consistent verb across sibling operations in the same module or type (`load...`, `save...`, `build...`).
  - Java: `getInvites(id)` -> `findOpenInvitesForWorkspace(workspaceId)`, `cleanup(userId)` -> `deleteAllLoginTokensForUser(userId)`
  - Python: `fetch_data(cid)` -> `load_new_search_queries(campaign_id)`, `compute(rows)` -> `sum_daily_spend(report_rows)`
  - React / TS: `handleSubmit(d)` -> `sendWorkspaceInvite(email, role)`, `formatVal(v)` -> `formatPriceWithoutCents(amount)`
- **Variables and constants = exact contents.** Never `data`, `result`, `res`, `tmp`, `item`, `obj`, `x`, `list`, `flag`, `loading`, `err`, or vague container words like `container` or `holder`.
  - Java: `inv`, `cnt`, `list` -> `openInvite`, `triesLeft`, `activeWorkspaceIds`
  - Python: `res`, `timeout`, `flag` -> `failed_report_rows`, `wait_seconds`, `is_already_saved`
  - React / TS: `selected`, `loading`, `err` -> `selectedCampaignIds`, `isSavingInvite`, `formErrorText`
- **Rename modules, types, and files when scope grows:** if a file or type was named after one original case and now handles a second distinct one, rename it to match its real job instead of leaving a stale name behind.
- **IDs name their owner:** `projectId`, `campaign_id`, `userId` (never bare `id`, `pk`, `ref`).
- **Booleans read as yes/no questions:** `isDone`, `has_images`, `canEdit`, `shouldRetry`.
- **No abbreviations or shortened words:** `settings`, `campaign`, `message` (never `cfg`, `cmpgn`, `ctx`, `mgr`, `msg`). Standard terms like `url`, `api`, `json`, `html`, `id` inside `userId` are fine.
- **Plurals for collections, units when they matter:** `campaigns`, `user_ids`, `wait_seconds` (never `campaignList` or bare `timeout`).
- **Distinct names for distinct behaviors:** `build_query_for_a` / `build_query_for_b`, not one generic `build_query` hiding different cases.

## 2. Top-to-Bottom Linear Flow

- **Validate first, return early.** Check bad inputs and edge cases at the top of the function and return or throw immediately so the main path stays flat at shallow indentation.
- **Read in story order.** Organize each file/class from high-level to detail: constants and state -> setup/constructor -> public operations -> private helpers.
- **One file, one job.** Name the file after what is inside (`order_receipt_service.py`, `ProjectHealthCard.tsx`). Avoid dumping unrelated helpers into `utils/`, `common/`, or `helpers/`.

## 3. Boring Control Flow Over Clever Code

- **Prefer plain `if / else` and `for` loops.** Avoid nested ternaries, long stream/LINQ/comprehension chains, `map().flatMap().orElse()`, or clever one-liners.
- **Obvious beats short.** A clear 10-line `if / for` block is always better than a 2-line puzzle.
- **Show every variant explicitly.** Handle each case in a visible `if / elif / else` or `switch` branch and fail loudly on unknown values instead of hiding cases in a generic fallback.

## 4. Small Functions (~30 Lines)

- When a function grows past ~30 lines or combines distinct steps, extract private helpers named after each step (`validateWorkspaceAccess`, `build_summary_rows`) so the main method reads like a short table of contents.
- Do not extract 1-2 obvious lines into a pointless one-caller wrapper.

## 5. Simplest Solution First (No Over-Engineering)

- **Pick the simplest working way.** If 200 lines can be 50 clear lines, write 50.
- **No speculative abstractions.** No interfaces for a single implementation, no factories, patterns, or options nobody asked for. Share code only when a second real caller needs it.
- **Clean up after your change.** Remove imports and variables your edit made unused, and delete replaced internal wrappers in the same change.
- **Explicit visibility, no unnecessary restrictions.** State clearly whether each type, function, or member is public/exported or internal/private instead of relying on implicit language defaults. Do not add extra inheritance-locking or sealing modifiers (`final` / `sealed`) to ordinary types unless preventing extension actually protects a real invariant.
