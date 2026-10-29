# Flutter Handoff — Expense Tracker

This is an implementation contract for Lab 3. Lab 2 contains no Flutter source code.

## 1. Global implementation rules

- Build an Android-first Flutter application with Material 3.
- Keep business rules and asynchronous work outside widgets; views render typed state and dispatch typed events.
- Use semantic theme tokens. Do not hard-code color, spacing, radius, elevation, or text styles inside screens.
- Use integer VND amounts; never calculate currency from formatted strings or floating-point display values.
- Preserve entered form data after validation and recoverable service failures.
- Prevent duplicate submissions while Saving or Processing.
- Back returns to the actual source and preserves period, query, filter, sort, and scroll context.
- Scroll content must clear the system inset, fixed bottom action, FAB, Snackbar, and NavigationBar.

## 2. Token-to-Flutter mapping

| Design token | Flutter target |
| --- | --- |
| `color/primary` | `ColorScheme.primary` |
| `color/onPrimary` | `ColorScheme.onPrimary` |
| `color/primaryContainer` | `ColorScheme.primaryContainer` |
| `color/background` | Application scaffold background |
| `color/surface` | `ColorScheme.surface` |
| `color/surfaceVariant` | `ColorScheme.surfaceContainer` |
| `color/textPrimary` | `ColorScheme.onSurface` |
| `color/textSecondary` | `ColorScheme.onSurfaceVariant` |
| `color/outline` | `ColorScheme.outline` |
| `color/error` | `ColorScheme.error` |
| `color/success` | `AppColors.success` semantic extension |
| `color/warning` | `AppColors.warning` semantic extension |
| `type/*` | `TextTheme` roles using Be Vietnam Pro |
| `space/*` | Explicit `AppSpacing` constants |
| `radius/*` | Explicit `AppRadius` constants |
| `elevation/card` | Card surface/elevation token |
| `elevation/floating` | FAB/Snackbar elevation token |

## 3. Component-to-widget mapping

| Figma component | Flutter implementation |
| --- | --- |
| Button | Typed wrapper over `FilledButton`; default, pressed, disabled, loading |
| Text Field | Typed wrapper over `TextFormField`; default, focused, filled, error, disabled |
| Card | Stateless semantic card with default and pressed variants |
| Navigation | `NavigationBar` with four destinations and independent tab histories |
| App Bar | `AppBar` with standard Back and optional action |
| Dialog | `AlertDialog` or modal bottom sheet with confirm/cancel/error variants |
| Loading State | Screen-specific skeleton/progress pattern |
| Empty State | Reusable icon, title, explanation, and CTA widget |
| Error State | Reusable cause, recovery instruction, and Retry widget |
| Transaction Row | Typed row with semantic amount, merchant, category, and date |
| Budget Progress | Progress indicator plus icon, label, percentage, and value summary |
| Snackbar Undo | App-shell `SnackBar` with persistent pending-delete state and Undo action |
| FAB | Compact `FloatingActionButton` with accessible label `Thêm khoản chi` |

## 4. Screen implementation contract

Each screen below specifies layout, components, states, interactions/validation, navigation/Back, and constraints.

### AU-01 Login

1. **Layout:** `Scaffold → SafeArea → Center → SingleChildScrollView → Column`.
2. **Components:** Brand block, body copy, Google button, privacy text.
3. **States:** Idle, authenticating, auth error, offline.
4. **Interactions:** Disable repeated sign-in; Retry preserves the screen; no password input.
5. **Navigation/Back:** Success replaces Login with the App Shell at HM-01; system Back exits.
6. **Constraints:** CTA ≥48dp; content remains visible at large text sizes.

### HM-01 Home

1. **Layout:** `Scaffold` with AppBar, refreshable `CustomScrollView`, fixed navigation, and FAB.
2. **Components:** Financial summary, budget progress, category card, transaction rows, state patterns.
3. **States:** Loading, empty, populated, error, no plan, updated after save.
4. **Interactions:** Change period, refresh, open category/transaction, add expense, open notifications.
5. **Navigation/Back:** Root Home tab; opens TX-02/TX-03/BG-02/IN-01/NT-01.
6. **Constraints:** Maximum five recent rows; totals reconcile; last row clears FAB/navigation.

### TX-01 Transactions

1. **Layout:** `Scaffold → AppBar → search/filter column → Expanded(ListView)` with FAB/navigation.
2. **Components:** Search field, chips, sort, grouped transaction rows, Snackbar Undo.
3. **States:** Loading, empty, filtered empty, populated, error, deleted, restored.
4. **Interactions:** Debounced search, filter/sort, open row, add expense, Undo/close deletion.
5. **Navigation/Back:** Root Transactions tab; preserve filter/sort/scroll when returning.
6. **Constraints:** Pending Undo stays visible across tab changes and survives process recreation.

### TX-02 Add Expense

1. **Layout:** `Scaffold → AppBar → Form → SingleChildScrollView`; fixed bottom submit area.
2. **Components:** Amount, category, date, merchant, note, Save button, validation/error banner.
3. **States:** Editing, validation error, saving, save failed.
4. **Interactions:** Amount `>0`; required category/date; merchant ≤80; note ≤200; submit exactly once.
5. **Navigation/Back:** Success returns to source and correct period; dirty Back opens discard dialog.
6. **Constraints:** Numeric keyboard; keyboard does not cover focus/CTA; preserve all values on failure.

### TX-03 Transaction Detail

1. **Layout:** `Scaffold → AppBar → SingleChildScrollView`; destructive action anchored after content.
2. **Components:** Amount header, detail rows, allocation result, Edit, Delete, confirmation overlay.
3. **States:** Loading, populated, error, confirming deletion, deleting.
4. **Interactions:** Edit opens TX-04; Delete confirms amount/category/date; success creates PendingDelete.
5. **Navigation/Back:** Back returns to the source list; delete returns to TX-01 with Undo.
6. **Constraints:** Dialog is an overlay; destructive action is separated and never the default focus.

### TX-04 Edit Expense

1. **Layout:** Same structure and field order as TX-02 with prefilled values.
2. **Components:** Shared TX-02 fields and fixed Save action.
3. **States:** Editing, validation error, saving, save failed.
4. **Interactions:** Same validation; changed date/category recalculates all affected periods/budgets.
5. **Navigation/Back:** Success returns to TX-03; dirty Back requests discard confirmation.
6. **Constraints:** Do not create a second independent form implementation.

### BG-01 Budgets

1. **Layout:** `Scaffold → AppBar → RefreshIndicator → ListView` with fixed navigation.
2. **Components:** Monthly summary, allocation summary, category rows, state patterns.
3. **States:** No plan, safe, warning, exceeded, loading, error.
4. **Interactions:** Change period, open category, create/edit monthly limit.
5. **Navigation/Back:** Root Budget tab; opens BG-02 or BG-03.
6. **Constraints:** Display real percentage/overage even when visual progress clamps at 100%.

### BG-02 Budget Detail

1. **Layout:** `Scaffold → AppBar → CustomScrollView` with summary and source transactions.
2. **Components:** Budget progress, value summary, status explanation, source rows, actions.
3. **States:** Loading, safe, warning, exceeded, error, no source data.
4. **Interactions:** Open insights, filtered transactions, or category-limit editor.
5. **Navigation/Back:** Return to Home/Budgets/Notifications according to source, preserving period.
6. **Constraints:** Transaction sum equals spent amount; status is not color-only.

### BG-03 Monthly Plan

1. **Layout:** `Scaffold → AppBar → Form`; fixed bottom Save action.
2. **Components:** Period selector, amount field, current-spending context, Save button.
3. **States:** Editing, validation error, saving, save failed.
4. **Interactions:** Limit required and `>0`; explain conflicts with existing allocations.
5. **Navigation/Back:** Success returns to the opening Home/Budget period; dirty Back confirms discard.
6. **Constraints:** Save action matches BG-04; VND formatting is applied after parsing integer input.

### BG-04 Category Budget Form

1. **Layout:** Same form shell and fixed action geometry as BG-03.
2. **Components:** Category, period, amount, threshold, allocation summary, Save button.
3. **States:** Editing, exceeded allocation, duplicate, validation error, saving, save failed.
4. **Interactions:** Amount `>0`; available allocation cannot be exceeded; category/period is unique.
5. **Navigation/Back:** Success returns to BG-02/BG-01 and recalculates allocation totals.
6. **Constraints:** Category selector and threshold provide accessible text values.

### IN-01 Insights

1. **Layout:** `Scaffold → AppBar → SingleChildScrollView → Column`.
2. **Components:** Period, KPI, chart, text summary, source rows, Export action.
3. **States:** Loading, empty/insufficient data, populated, error.
4. **Interactions:** Change period, select category/source, export report.
5. **Navigation/Back:** Opens filtered TX-01 or EX-01; Back returns to BG-02.
6. **Constraints:** Chart includes semantics and equivalent text; no horizontal clipping.

### EX-01 Export Report

1. **Layout:** `Scaffold → AppBar → scrollable content`; fixed bottom action.
2. **Components:** Period, included sections, financial summary, file row, status, primary action.
3. **States:** Ready, processing, failed, generated, no data.
4. **Interactions:** Generate once, Retry with same period, open platform PDF viewer, add expense from No Data.
5. **Navigation/Back:** Returns to IN-01 or PF-01 source; Processing requests confirmation before cancellation.
6. **Constraints:** Failure includes cause/action; generated report includes period and generated timestamp.

### NT-01 Notification Center

1. **Layout:** `Scaffold → AppBar(action) → ListView`.
2. **Components:** Notification rows and loading/empty/error patterns.
3. **States:** Loading, empty, populated, error.
4. **Interactions:** Tap marks read and opens target; mark all read.
5. **Navigation/Back:** Alert opens BG-02 with category/period; Back returns to source.
6. **Constraints:** Unread state has semantic/text indication, not only a colored dot.

### PF-01 Profile

1. **Layout:** `Scaffold → AppBar → ListView` with grouped account/settings/session sections.
2. **Components:** Profile header, settings rows, value rows, sign-out confirmation, navigation.
3. **States:** Default, offline, signing out, sign-out error.
4. **Interactions:** Open notifications/export; confirm sign out.
5. **Navigation/Back:** Root Profile tab; sign out clears session/stack and opens AU-01.
6. **Constraints:** Email truncates safely; destructive sign-out remains visually separated.

## 5. State ownership

| State | Owner |
| --- | --- |
| Selected root tab and each tab's navigation history | App Shell |
| Selected reporting period | Shared period/session state |
| Search, filters, sort, and list position | TX-01 state |
| Add/Edit form values and validation | TX-02/TX-04 form controller |
| PendingDelete and Undo | App Shell, persisted until resolved |
| Budget plan and allocation calculations | Budget domain state |
| PDF generation job and selected period | EX-01 state |

## 6. Formatting and accessibility

- Currency: Vietnamese grouping, for example `1.250.000 đ`.
- Detailed date: `dd/MM/yyyy`; list views may use relative labels with an accessible full date.
- Normal text contrast ≥4.5:1; large text and controls ≥3:1.
- Interactive target ≥48×48dp; body text should normally be ≥14sp.
- Status, read state, warnings, and errors require icon/text/semantics in addition to color.
- At 360dp and 412dp use one column. At ≥600dp center content at max width 600dp; forms/dialogs may use max width 480dp.
- Support system text scaling without hiding values, errors, or primary actions.

