---
name: grill-design
description: Design pages, blocks, and components inside a real frontend app. Use for new UI, redesigns, and design interviews. Reuse existing project components, agree on the design one question at a time, then build and verify three interactive variants.
---

# Grill Design

Create a screen that helps the user do their job and feels native to the existing application. Reuse the real app shell, UI components, design tokens, and data states.

## 1. Read and look before asking

1. Read the project's frontend style guide, design tokens, and existing UI rules if present.
2. Inspect existing screens, routes, and shared UI components in the codebase. Check what components already support before proposing a new one.
3. If the project keeps UI reference screenshots or a Storybook/component catalog, inspect the closest screens for layout, spacing, and interaction patterns.
4. Name the reference screens or components, what patterns they contribute, and which existing components the new page or block will reuse.

## 2. Interview one question at a time

Interview the user about the design until you share a clear brief. Walk down each branch of the design tree, resolving dependent decisions one by one. For each question, state your recommended answer.

- Ask one question at a time.
- If a question can be answered by reading the codebase, inspect the code instead of asking.
- Give each question enough context to stand on its own and explain what the answer changes.
- Start from the user's goal, then cover content, actions, permissions, and edge states (empty, loading, error).
- Keep agreed choices and revisit dependent ones if an answer changes. End the interview once you agree on the brief and on what the variants should explore.

## 3. Build one interactive review artifact

- For a new page, block, or element, show three distinct design variants. For a redesign, show the current interface as a baseline alongside the three proposed variants.
- Render the variants in one interactive preview inside the real app (using the real app shell, components, tokens, and translations if applicable). For a block or element, place it in a realistic page context.
- Give every variant working controls for themes (light/dark if supported) and viewport presets (desktop and mobile), while keeping the layout continuously responsive across widths.
- Use the same realistic local demo data and filled starting state across the baseline and variants. Make controls interactive (tabs, filters, cards, drawers) so the user can test the flow.
- Summarize what each variant does differently, give a clear recommendation with a reason, and let the user pick or combine parts before finalizing.

## 4. Verify in a real browser

1. Open the finished preview in a browser and exercise its variant, theme, and viewport controls.
2. Check the baseline and each variant at key widths (320, 375, 768, 1024, and 1440 px) and test every interactive action shown.
3. Resize across those widths and check for clipped labels, overlapping elements, horizontal page overflow, or unreachable controls.
4. Wait for charts or async visual elements to finish rendering before capturing screenshots, and inspect the screenshots yourself before handing over. Share the checked widths, themes, and any blockers found.
