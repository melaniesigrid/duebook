# TODOS

## Site

### Add a cross-browser check to the release routine

**What:** Verify the hero mock renders correctly in Safari and Firefox, not just Chromium.

**Why:** The hero card uses CSS techniques that are well supported but not visually verified outside Chromium: `filter: drop-shadow()` on a non-positioned wrapper, a custom property (`--tear-c`) consumed inside a `background` gradient shorthand, and a `::before` zigzag positioned with a negative `inset`. A rendering difference here would land on the first screen of the site.

**Context:** The torn-paper edge under the "Due this week" card was rebuilt on 2026-08-10 (see `.duestack` / `.tear` in `index.html`). Verification at the time was headless Chromium only, at 1280px and 390px. Nothing suggests a problem (these features have been baseline for years) but the hero is the highest-visibility element on the page and nobody has looked at it in another engine.

**Effort:** S
**Priority:** P3
**Depends on:** None

## Completed

### Join the torn paper edge to the due-list card

**What:** The torn-paper strip under the hero "Due this week" card read as a detached band instead of the same sheet of paper.

**Why:** The card kept a 20px bottom border-radius, a bottom border, and its own box-shadow, while the tear was an independent straight-topped strip below it. The rounded corners and the border line cut across the join.

**Context:** Fixed by squaring the card's bottom corners, dropping its bottom border, moving the shadow to a new `.duestack` wrapper as a `drop-shadow` filter so it traces the actual torn outline, and rebuilding `.tear` as two stacked zigzags so the card's hairline border follows the teeth.

**Effort:** S
**Priority:** P2
**Completed:** 2026-08-10
