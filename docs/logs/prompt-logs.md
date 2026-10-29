# AI Prompt and Design Refinement Log

This log records the prompts, evidence, evaluation decisions, and AI tools used for the Expense Tracker design. It follows the evidence requirements in [`docs/en/requirements/lab2.md`](../en/requirements/lab2.md#3-evidence-of-ai-use).

> Evidence note: the original screenshots are preserved in Git commit [`ac5c2e6`](https://github.com/tgbaonguyen-dev/PRM393_Lab02/tree/ac5c2e6/assets/stitch). Each evidence link below points to that immutable commit so the recorded before/after results can be verified.

## 1. AI tools declaration

| Tool | Purpose | Date used | Verifiable evidence |
| --- | --- | --- | --- |
| ChatGPT / Codex | Analyze the Lab 2 brief, define the product scope, review UX, and document design decisions | 2026-10-06 onward | Repository documentation and this log |
| Google Stitch | Generate the initial UI and three targeted refinement rounds | 2026-10-10 to 2026-10-11 | [Stitch evidence directory](https://github.com/tgbaonguyen-dev/PRM393_Lab02/tree/ac5c2e6/assets/stitch) |
| Figma AI | Build and refine reusable components, screens, and prototype structures | 2026-10-09 onward | Figma pages `03 Final UI`, `04 Design System`, `05 Components`, and `06 Prototype` |

## 2. Initial Google Stitch generation

### Objective

Generate the initial screens for the primary task: adding an expense and immediately seeing its effect on the monthly budget.

### Exact prompt

```text
Design a 3-screen Android mobile app flow (360 x 800 dp) for a Vietnamese personal expense tracker. All UI text must be in Vietnamese.

Persona: Nguyễn Minh, 21, third-year university student living away from home in Ho Chi Minh City. He receives 5,000,000 VND monthly allowance plus irregular part-time internship income. He uses a mid-range Android phone, mostly with one hand, often on weak mobile data, and opens the app for under a minute at a time.

Task: Minh has just paid for a small expense and wants to record it in a few taps and immediately see how it affects his monthly budget. Success criterion: add an expense and see the budget updated in under 20 seconds.

Screens:
1. Home Dashboard: app bar, total spent this month, remaining monthly budget with a budget status (icon + text label + progress bar), top categories, 5 recent transactions, an extended FAB "Thêm khoản chi", and bottom navigation with 4 destinations: Home, Giao dịch, Ngân sách, Hồ sơ.
2. Add Expense: fields for amount (VND, numeric keyboard), category, date, merchant, and note (max 200 characters), plus a sticky "Lưu khoản chi" button. Show a clear inline validation error state when amount is 0.
3. Transaction Detail: amount, category, merchant, date, note, a primary "Chỉnh sửa" action, and a secondary destructive "Xóa" action.

Constraints: one clear primary action per screen; body text at least 14sp; touch targets at least 48x48dp; amounts with high contrast; status never conveyed by color alone; errors shown next to the field and entered data is kept; calm, non-judgmental tone; no extra features (no receipt OCR, bank sync, social, AI coach, debt tracking, or investing).

Style: calm, clear, trustworthy. Primary #146C5A, on-primary #FFFFFF, background #F7F9F8, surface #FFFFFF, text primary #17211E, text secondary #52605C, outline #73817D, error #BA1A1A, warning #9A5B00, success #197A49. Font Inter. Corner radius 12-16dp, content padding 16dp. Material 3 inspired.
```

### Result and evidence

- Generated screens: Home Dashboard, Add Expense, and Transaction Detail.
- [Initial Home](https://github.com/tgbaonguyen-dev/PRM393_Lab02/blob/ac5c2e6/assets/stitch/initial-home.png)
- [Initial Add Expense](https://github.com/tgbaonguyen-dev/PRM393_Lab02/blob/ac5c2e6/assets/stitch/initial-add-expense.png)
- [Initial Transaction Detail](https://github.com/tgbaonguyen-dev/PRM393_Lab02/blob/ac5c2e6/assets/stitch/initial-transaction-detail.png)

## 3. Refinement round 1 — Visual hierarchy

### Specific issue

The Home budget card contained too many competing elements. The remaining budget—the value Minh needs to understand quickly—did not have a clear visual priority.

### Exact prompt

```text
Revise only the Home Dashboard screen to improve visual hierarchy. Keep the Add Expense and Transaction Detail screens unchanged.

Problem: the top budget card has too many competing elements (a "65% chi tiêu" chip, total spent, remaining budget, monthly limit, a status row, a progress bar with 50/80/100% markers, and a daily suggestion box). The remaining budget, which answers Minh's main question, has the same small size as the monthly limit.

Changes: keep total spent this month as the largest number. Make "Còn lại" the clear second level, larger than the monthly limit. Merge the "65% chi tiêu" chip into the single budget status row (icon + text label + percentage) and remove the duplicate chip. Keep one progress bar and remove the 50/80/100% markers. Keep the daily suggestion as one short line of secondary text. Keep body text at least 14sp and touch targets at least 48x48dp. Do not add new features.
```

### Before and after evidence

- [Before](https://github.com/tgbaonguyen-dev/PRM393_Lab02/blob/ac5c2e6/assets/stitch/iteration-1-before.png)
- [After](https://github.com/tgbaonguyen-dev/PRM393_Lab02/blob/ac5c2e6/assets/stitch/iteration-1-after.png)

### Decision — Modify

Retain the clearer hierarchy: total spending first, remaining budget second, one labeled status row, and one progress bar. Rebuild it with the project Financial Card and Budget Progress components instead of copying Stitch literally. Correct clipped text and keep body text at least 14sp. This supports a persona who opens the app for less than one minute and needs the budget status at a glance.

## 4. Refinement round 2 — Error recovery

### Specific issue

The initial Add Expense screen only covered invalid input. It lacked a submitting state and a recoverable network-error state, despite the persona frequently using weak mobile data.

### Exact prompt

```text
Revise only the Add Expense screen to improve error recovery. Keep the Home Dashboard and Transaction Detail screens unchanged.

Problem: the screen only shows an inline validation error for amount = 0. It has no state for saving in progress or for a network failure, even though Minh often has weak mobile data.

Changes: create two additional states of the Add Expense screen with all entered data kept in the fields.
1. Submitting: the "Lưu khoản chi" button shows a loading indicator with the label "Đang lưu..." and is disabled, keeping the same width and height.
2. Network error: an error banner near the top of the form with an icon and the text "Không thể lưu khoản chi. Kết nối mạng bị gián đoạn. Dữ liệu bạn nhập vẫn được giữ." and a "Thử lại" button. The fields stay editable.
Keep body text at least 14sp and touch targets at least 48x48dp. Status must not rely on color alone. Do not add new features.
```

### Before and after evidence

- [Before](https://github.com/tgbaonguyen-dev/PRM393_Lab02/blob/ac5c2e6/assets/stitch/iteration-2-before.png)
- [After — Submitting](https://github.com/tgbaonguyen-dev/PRM393_Lab02/blob/ac5c2e6/assets/stitch/iteration-2-after-submitting.png)
- [After — Network error](https://github.com/tgbaonguyen-dev/PRM393_Lab02/blob/ac5c2e6/assets/stitch/iteration-2-after-network-error.png)

### Decision — Modify

Keep the loading label, understandable error cause, preserved form data, and Retry action. Change the amount from `0` to a valid value in the submitting and network-error states because invalid input must never reach submission. Use the primary color for Retry rather than red; red remains reserved for errors and destructive actions.

## 5. Refinement round 3 — Accessibility and budget status

### Specific issue

Only the safe budget state existed. Warning and over-budget states were missing, creating a risk that status would later be communicated using color alone. The initial warning text color on its light container also measured below the required 4.5:1 ratio for normal text.

### Exact prompt

```text
Revise only the Home Dashboard screen and add two new states of its budget status. Keep the Add Expense and Transaction Detail screens unchanged.

Problem: the screen only shows the "on track" budget status. The warning state (90% of budget used) and the over-budget state (120% of budget used) are not designed, even though they are where color-only signaling and low contrast are most likely.

Changes: create two additional versions of the Home Dashboard.
1. Warning at 90%: status row with a warning icon, the label "Sắp vượt ngân sách", the percentage, and the progress bar. Use warning #9A5B00 for text and icon on a light warning container #FFE2B8. Add one short calm line with a concrete next step, for example how much can still be spent per day.
2. Over budget at 120%: status row with an error icon, the label "Vượt ngân sách", the amount over the limit, and a full progress bar. Use error #BA1A1A on #FFDAD6. Add one short calm, non-judgmental line with a next step.
Status must never rely on color alone: always icon + text label. Keep body text at least 14sp and touch targets at least 48x48dp. Do not add new features.
```

### Before and after evidence

- [Before](https://github.com/tgbaonguyen-dev/PRM393_Lab02/blob/ac5c2e6/assets/stitch/iteration-3-before.png)
- [After — Warning](https://github.com/tgbaonguyen-dev/PRM393_Lab02/blob/ac5c2e6/assets/stitch/iteration-3-after-warning.png)
- [After — Over budget](https://github.com/tgbaonguyen-dev/PRM393_Lab02/blob/ac5c2e6/assets/stitch/iteration-3-after-over-budget.png)

### Decision — Modify

Keep the icon, explicit status label, percentage, progress bar, and calm next step. Use the darker primary text token for the warning label to satisfy contrast; reserve the warning color for the icon and progress indicator. Do not copy category percentages from the generated variants because they were not recalculated consistently with the changed total.

## 6. AI critique

### Exact critique prompt

```text
You are a UX reviewer. Review the attached 3 mobile screens (Home Dashboard, Add Expense, Transaction Detail) of a Vietnamese expense tracker for this persona: Nguyễn Minh, 21, student in Ho Chi Minh City, one-handed use, weak mobile data, uses the app for under a minute. Evaluate against Nielsen's 10 usability heuristics, and also check accessibility (contrast 4.5:1, touch targets 48x48dp, body text 14sp, no color-only status).

Return at least 8 findings. For each finding give: screen, specific issue, severity (high/medium/low), the violated heuristic, and a concrete recommendation. Do not invent features outside this scope: personal expense tracking, budgets, insights, and PDF export.
```

### Critique findings and project decisions

The AI returned nine findings. The table records the important findings, their screen context, and the team's explicit `Accept`, `Modify`, or `Reject` decision.

| # | Screen | AI finding | Severity / basis | Decision | Reason and resulting design action |
| --- | --- | --- | --- | --- | --- |
| 1 | Transaction Detail | Delete lacks confirmation | High · H5 Error prevention | **Accept** | Use a confirmation bottom sheet/dialog followed by Snackbar Undo. |
| 2 | Add Expense; Transaction Detail | Top-left Back is difficult for one-handed use; add a swipe gesture | High · H7 Flexibility | **Reject** | Android already provides system Back; the visible Back control remains necessary for prototype clarity. A custom swipe gesture is outside the Figma prototype scope. |
| 3 | Add Expense → result | Missing immediate feedback after saving | High · H1 Visibility of system status | **Modify** | Show feedback on the resulting transaction/home state while preserving the specified navigation destination. |
| 4 | Home; Transaction Detail | Secondary text may not meet 4.5:1 contrast | Medium · WCAG AA / H8 | **Modify** | Do not trust the AI's estimated ratio. Measure the actual token and use `color/textSecondary` only where it passes; use primary text otherwise. |
| 5 | Add Expense | Custom keypad and quick-amount chips are too close | Medium · H5 / 48dp target | **Modify** | Use the Android numeric keyboard rather than a custom keypad. Any retained quick action must have a 48dp target and at least 8dp spacing. |
| 6 | Add Expense | Merchant and note fields have weak input affordance | Medium · H6 Recognition | **Accept** | Use the shared Text Field component with label, outline, placeholder, focus, filled, error, and disabled states. |
| 7 | Home | FAB may cover the final transaction | Medium · H7/H8 | **Accept** | Keep sufficient bottom content padding and use a compact circular FAB consistently above the navigation bar. |
| 8 | Home | Category cards lack a category-limit reference | Low · H6 Recognition | **Modify** | Show spent, limit, and remaining values only on budget/category screens where they support the task without crowding Home. |
| 9 | Add Expense — Network Error | Add an offline outbox and automatic synchronization | Medium · H9 Error recovery | **Reject** | Offline synchronization adds system behavior outside Lab 2 scope. Preserve entered data and provide Retry instead. |

### Critique limitations

- The AI reviewed screenshots, not the complete interaction specification; all findings were checked against the project flows before adoption.
- Numerical estimates such as contrast ratios and spacing were treated as hypotheses until measured in Figma.
- Recommendations that expanded the product scope were rejected rather than silently added.

## 7. Final traceability checklist

- [x] Exact initial Google Stitch prompt recorded.
- [x] Initial generated screens linked.
- [x] Three distinct refinement rounds recorded.
- [x] Each refinement includes a specific issue, exact prompt, before/after evidence, and decision.
- [x] Critique explicitly covers Nielsen heuristics, accessibility, and the Nguyễn Minh persona.
- [x] At least five screen-specific findings are recorded.
- [x] Important recommendations have `Accept`, `Modify`, or `Reject` decisions with reasons.
- [x] Every AI tool and purpose is declared.
- [x] Evidence links resolve to immutable repository history rather than reconstructed screenshots.

## 8. Submission references

- [Lab 2 evidence requirements](../en/requirements/lab2.md#3-evidence-of-ai-use)
- [English user flows](../en/ux/user-flows.md)
- [Vietnamese user flows](../vi/ux/user-flows.md)
- [Design specification](../design/design.md)
