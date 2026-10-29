# Design Decisions and Accessibility Evidence

This document records the current design decisions and distinguishes verified evidence from items that still require a measured Figma check. It must not be used to claim unperformed accessibility testing.

## 1. Design decisions

| # | Decision | Reason | Basis |
| --- | --- | --- | --- |
| 1 | Use four peer destinations: Home, Transactions, Budgets, and Profile | Frequent destinations remain one tap away while preserving separate histories | Persona; recognition rather than recall |
| 2 | Add Expense is a contextual primary action, not a navigation destination | It is a short task rather than a persistent information area | Material navigation; task hierarchy |
| 3 | Keep Add/Edit Expense on one screen | Reduces steps and supports the under-20-second success criterion | P01; efficiency of use |
| 4 | Preserve form values and show field-level validation | Users can correct input without repeating work | H5 Error prevention; H9 recovery |
| 5 | Show Saving and Save Failed without replacing the form | Weak-network recovery remains understandable and editable | P01; H1 system status |
| 6 | Require confirmation and persistent Undo for deletion | Prevents accidental loss while providing immediate recovery | H3 user control; H5 prevention |
| 7 | Communicate budget state with icon, text, percentage, and progress | Status remains understandable without relying on color | WCAG; NFR-02 |
| 8 | Use calm, non-judgmental warning copy | Financial warnings should support action rather than create guilt | Persona; content tone |
| 9 | Keep chart information available as text | Users can understand allocation without interpreting color or geometry alone | Accessibility; H6 recognition |
| 10 | Keep OCR, bank sync, offline outbox, debt, and investing outside Lab 2 | These features add implementation states without supporting the required flows | KISS; Lab 2 scope |

## 2. Current measured evidence

| Check | Requirement | Current result | Evidence/status |
| --- | --- | --- | --- |
| Final UI frame size | `360 × 800 dp` | **Pass:** 26 submitted screen/state frames are `360 × 800` | Figma audit, `03 Final UI`, 2026-10-29 |
| Final UI font family | Consistent project typography | **Pass:** 677 text nodes / 682 text segments use Be Vietnam Pro | Figma audit, `03 Final UI`, 2026-10-29 |
| Distinct screens | At least 8 | **Pass:** IA defines 14 distinct screens | [Information Architecture](../en/ux/information-architecture.md#3-screen-catalogue) |
| Three flow starts | Three complete flows | **Pass:** FL-01, FL-02, and FL-03 have prototype starting points | Figma audit, `06 Prototype`, 2026-10-29 |
| Missing prototype destinations | None | **Pass:** no reaction points to a missing frame | Figma audit, `06 Prototype`, 2026-10-29 |
| Loading-to-result transition | At least one | **Pass:** EX-01 Processing uses After Delay → Generated | Figma audit, `06 Prototype`, 2026-10-29 |
| Normal text contrast | `≥ 4.5:1` | **Not yet measured on final frames** | Required before submission |
| Large text/UI contrast | `≥ 3:1` | **Not yet measured on final frames** | Required before submission |
| Touch targets | `≥ 48 × 48 dp` | **Not yet measured across every interactive control** | Required before submission |
| Minimum body text | `≥ 14 sp` | **Partial:** design rule exists; some supporting labels intentionally use smaller styles and require review | [Design System](design.md#typography) |
| Color independence | Do not use color alone | **Partial:** core budget/error states use icon and text; audit every final state | Figma review required |
| Width `412 dp` | No clipping or lost action | **Missing:** no 412dp evidence frame exists | Must be added before submission |
| Large text/reflow | No important content loss | **Not yet tested** | Must be tested before submission |

## 3. Responsive behavior

- **360dp:** single-column layout, 16dp horizontal content padding, fixed bottom navigation, and scroll content clearing the FAB/navigation inset.
- **412dp:** remain single column; allow cards and fields to expand without scaling typography or controls arbitrarily.
- **600dp and above:** center content in a container with a maximum width of 600dp. Dialogs and forms may use a narrower maximum width of 480dp.
- Amounts wrap before actions or labels are clipped. Long merchant names use a two-line ellipsis.
- Keyboard and system insets must not cover the focused field or primary action.

## 4. Open audit actions

- Create representative `412dp` frames for Home, Add Expense, Transactions, Budget, and Export.
- Measure normal text, large text, controls, and warning/error containers with a contrast tool.
- Verify every interactive target is at least `48 × 48dp`.
- Test the longest Vietnamese labels and 200% text scaling.
- Capture screenshots or Figma node links and replace all **Not yet measured** statuses with results.

