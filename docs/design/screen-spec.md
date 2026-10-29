# Screen Specification

Screen IDs follow the [Information Architecture](../en/ux/information-architecture.md). Dialogs, Snackbars, loading, empty, success, and error variants are states or overlays and do not count as additional screens.

## AU-01 — Login

- **Purpose:** Authenticate with Google and enter the application shell.
- **Content:** Brand mark, product value statement, Google action, and privacy notice.
- **Primary action:** `Tiếp tục với Google`.
- **States:** Idle, authenticating, authentication error, and offline.
- **Navigation:** Success replaces Login with HM-01; system Back exits.
- **Constraints:** No password fields; action target is at least 48dp; content remains centered and scrollable with large text.

## HM-01 — Home

- **Purpose:** Answer how much was spent, what remains, and what needs attention in the selected period.
- **Content:** Period, spending/remaining summary, budget progress, category attention card, recent transactions, notification action, FAB, and navigation.
- **Primary action:** Open TX-02 to add an expense.
- **States:** Loading, empty, populated, error, no monthly plan, and updated after save.
- **Navigation:** TX-02, TX-03, BG-02, IN-01, NT-01, or another root tab.
- **Constraints:** Show at most five recent rows; values must reconcile; list content clears the FAB and navigation.

## TX-01 — Transactions

- **Purpose:** Find, filter, sort, and review transactions.
- **Content:** Period, search, category filters, grouped rows, FAB, Snackbar Undo, and navigation.
- **Primary action:** Open a transaction or add a new expense.
- **States:** Loading, empty, filtered empty, populated, error, deleted with Undo, and restored.
- **Navigation:** TX-02 or TX-03; Back preserves query, filters, sort, and list position.
- **Constraints:** Search and filters remain visible; long merchant names use two lines; pending Undo is not hidden by the FAB.

## TX-02 — Add Expense

- **Purpose:** Record an expense quickly without losing entered data.
- **Content:** Amount, category, occurredAt/date, merchant, note, and sticky save action.
- **Validation:** Amount is required and greater than zero; category/date are required; merchant ≤80 and note ≤200 characters.
- **States:** Default, focused, validation error, saving, and save failed.
- **Navigation:** Success returns to the real source and updates the correct period; Back with changes opens discard confirmation.
- **Constraints:** Use numeric keyboard for amount; disable repeated submission; preserve every value after validation or network failure.

## TX-03 — Transaction Detail

- **Purpose:** Review one transaction and start edit or delete actions.
- **Content:** Amount, category, date/time, merchant, note, allocation result, edit, and delete.
- **Primary action:** Edit via TX-04; delete is destructive and secondary.
- **States:** Loading, populated, error, delete confirmation overlay, and deleting.
- **Navigation:** Back returns to the source list; successful delete returns to TX-01 with persistent Undo.
- **Constraints:** Confirmation names amount/category/date and impact; destructive action remains visually separated at the bottom.

## TX-04 — Edit Expense

- **Purpose:** Update an existing transaction using the same field model as TX-02.
- **Content:** Prefilled amount, category, date, merchant, note, and sticky save action.
- **Validation:** Same rules as TX-02; changed period/category triggers recalculation.
- **States:** Default, focused, validation error, saving, and save failed.
- **Navigation:** Success returns to TX-03; Back with changes opens discard confirmation.
- **Constraints:** Keep field order, labels, icons, button position, and error behavior consistent with TX-02.

## BG-01 — Budgets

- **Purpose:** Present the monthly plan, allocation totals, and category status.
- **Content:** Period, monthly limit, spent/remaining, allocated/unallocated, category rows, and navigation.
- **Primary action:** Create or edit the monthly plan through BG-03.
- **States:** No plan, safe, warning, exceeded, loading, and error.
- **Navigation:** BG-02, BG-03, or another root tab.
- **Constraints:** Progress may clamp visually at 100%, but the text must show the real percentage and overage.

## BG-02 — Budget Detail

- **Purpose:** Explain the spending status of one category.
- **Content:** Category progress, limit, spent, remaining/overage, period, source transactions, and analysis action.
- **Primary action:** Open IN-01; edit allocation opens BG-04.
- **States:** Safe, warning, exceeded, loading, error, and no source data.
- **Navigation:** IN-01, BG-04, or filtered TX-01; Back returns to the actual source.
- **Constraints:** Source transactions reconcile with the displayed spent amount; status uses icon, text, and color.

## BG-03 — Monthly Plan

- **Purpose:** Create or update the total monthly spending limit.
- **Content:** Period, limit amount, current spending context, and fixed save action.
- **Validation:** Limit is required and greater than zero; reducing below allocations requires a clear explanation.
- **States:** Default, focused, validation error, saving, and save failed.
- **Navigation:** Success returns to the opening HM-01/BG-01 period; category allocation remains accessible from BG-01/BG-02.
- **Constraints:** Currency uses Vietnamese grouping; save action matches BG-04 position and dimensions.

## BG-04 — Category Budget Form

- **Purpose:** Create or edit a category sub-cap within the monthly limit.
- **Content:** Category, period, amount, allocation summary, warning threshold, and fixed save action.
- **Validation:** Amount is greater than zero, does not exceed available allocation, and does not duplicate category/period.
- **States:** Default, focused, validation error, allocation exceeded, duplicate, saving, and save failed.
- **Navigation:** Success returns to BG-02/BG-01 with recalculated allocated and unallocated totals.
- **Constraints:** Field layout, amount formatting, and save action are consistent with BG-03.

## IN-01 — Insights

- **Purpose:** Explain how spending is distributed during a period.
- **Content:** Period selector, total, category visualization, equivalent text summary, and source transactions.
- **Primary action:** Open EX-01.
- **States:** Loading, empty/insufficient data, populated, and error.
- **Navigation:** EX-01 or filtered TX-01; Back returns to BG-02.
- **Constraints:** Chart has a semantic label and text alternative; no meaning relies only on color.

## EX-01 — Export Report

- **Purpose:** Generate and open a period PDF report.
- **Content:** Period, included sections, financial summary, file row, status message, and fixed action.
- **Primary action:** Generate PDF or open the generated PDF.
- **States:** Ready, processing, failed, generated, and no data.
- **Navigation:** Back returns to IN-01 or PF-01 based on the source; No Data can open TX-02.
- **Constraints:** Prevent duplicate generation; preserve the selected period on failure; actions remain at a consistent bottom position.

## NT-01 — Notification Center

- **Purpose:** Review budget warnings and system notifications.
- **Content:** Read/unread rows, category/period context, timestamps, and mark-all-read action.
- **Primary action:** Open the notification target.
- **States:** Loading, empty, populated, and error.
- **Navigation:** Budget warning opens the correct BG-02 context; Back returns to Home/Profile source.
- **Constraints:** Read state uses text/semantics as well as color; timestamps remain readable.

## PF-01 — Profile

- **Purpose:** Display account information and secondary destinations.
- **Content:** Avatar, name, email, currency, notifications, export reports, and sign out.
- **Primary action:** Open a selected setting/destination; sign out is destructive.
- **States:** Default, offline, sign-out confirmation, and signing out.
- **Navigation:** NT-01, EX-01, or AU-01 after sign out.
- **Constraints:** Email truncates safely; sign out clears the stack; navigation remains fixed and consistent.

