# Flutter Handoff - Expense Tracker

## 1. Global implementation rules

- Android-first Flutter app.
- Dùng Material 3.
- Business logic nằm trong ViewModel; View không gọi Firebase trực tiếp.
- Mọi màn hình dùng semantic theme tokens, không hard-code màu và spacing.
- Nội dung cuộn phải chừa bottom inset cho NavigationBar/FAB.
- Back quay về màn hình nguồn; không mặc định chuyển về Home.
- Async action hiển thị loading và lỗi cụ thể; form giữ dữ liệu khi lỗi.

## 2. Token-to-Flutter mapping

| Design token | Flutter target |
| --- | --- |
| `color.primary` | `ColorScheme.primary` |
| `color.onPrimary` | `ColorScheme.onPrimary` |
| `color.primaryContainer` | `ColorScheme.primaryContainer` |
| `color.background` | `ColorScheme.surface` hoặc app background semantic token |
| `color.surface` | `ColorScheme.surface` |
| `color.surfaceVariant` | `ColorScheme.surfaceContainer` |
| `color.textPrimary` | `ColorScheme.onSurface` |
| `color.textSecondary` | `ColorScheme.onSurfaceVariant` |
| `color.outline` | `ColorScheme.outline` |
| `color.success` | `AppColors.success` |
| `color.warning` | `AppColors.warning` |
| `color.error` | `ColorScheme.error` |
| `type.displaySmall` | `TextTheme.displaySmall` |
| `type.headlineMedium` | `TextTheme.headlineMedium` |
| `type.titleLarge` | `TextTheme.titleLarge` |
| `type.titleMedium` | `TextTheme.titleMedium` |
| `type.bodyLarge` | `TextTheme.bodyLarge` |
| `type.bodyMedium` | `TextTheme.bodyMedium` |
| `type.labelLarge` | `TextTheme.labelLarge` |
| `space.*` | `AppSpacing` named constants |
| `radius.*` | `AppRadius` named constants |

## 3. Component-to-widget mapping

| Figma component | Flutter widget |
| --- | --- |
| Primary Button | `FilledButton` wrapper |
| Secondary Button | `OutlinedButton` wrapper |
| Text Button | `TextButton` wrapper |
| Text Field | `TextFormField` wrapper |
| Amount Field | Typed custom widget composed from `TextFormField` |
| Financial Card | Typed stateless custom widget |
| Transaction Row | Typed stateless custom widget using `ListTile` semantics |
| Budget Progress | Typed custom widget using `LinearProgressIndicator` and status label |
| Bottom Navigation | `NavigationBar` |
| App Bar | `AppBar` |
| FAB | `FloatingActionButton.extended` |
| Confirmation Dialog | `AlertDialog` |
| Snackbar Undo | `SnackBar` with action |
| Loading Skeleton | Reusable skeleton widgets matching content |
| Empty State | Typed custom widget with icon, message and CTA |
| Error State | Typed custom widget with cause and retry callback |

## 4. Screen specifications

### AU-01 Login

1. **Layout:** `Scaffold -> SafeArea -> Center -> SingleChildScrollView -> Column`; horizontal padding `space.6`.
2. **Components:** Brand block, body copy, Google sign-in `FilledButton`, privacy `TextButton`.
3. **States:** Default, authenticating, auth error, offline.
4. **Interactions:** Sign-in disables duplicate taps; error includes retry. No credential fields.
5. **Navigation:** Successful sign-in replaces route with App Shell. Back exits Android activity.
6. **Constraints:** CTA minimum 48 dp; content remains visible with large text.

### HM-01 Home Dashboard

1. **Layout:** `Scaffold -> AppBar + RefreshIndicator -> CustomScrollView`; NavigationBar and FAB fixed.
2. **Components:** Summary card, budget progress cards, category rows, transaction rows, FAB, skeleton/empty/error.
3. **States:** Loading, first-use empty, populated, partial error, offline cache.
4. **Interactions:** Pull refresh; tap card to detail; FAB opens TX-02; notification action opens NT-01.
5. **Navigation:** Root tab; Android Back follows app-shell behavior and then exits.
6. **Constraints:** Maximum five recent rows; amount wraps before clipping; final item clears FAB.

### TX-01 Transaction List

1. **Layout:** `Scaffold -> AppBar -> Column(search/filter) -> Expanded(ListView)`.
2. **Components:** Search field, filter chips, sort action, transaction row, FAB, state patterns.
3. **States:** Loading, empty-first-use, filtered-empty, populated, error, offline.
4. **Interactions:** Search on submitted/debounced input; filter by category; sort by date/amount; tap row.
5. **Navigation:** Root tab; opens TX-02/TX-03. Back closes filter overlay before leaving.
6. **Constraints:** Preserve filter when returning; long merchant uses two-line ellipsis.

### TX-02 Add/Edit Expense

1. **Layout:** `Scaffold -> AppBar -> Form -> SingleChildScrollView -> Column`; sticky bottom submit area.
2. **Components:** Amount field, category selector, date field, merchant field, note field, submit button.
3. **States:** Default, focused, validation error, submitting, network error.
4. **Interactions:** Validate amount `> 0`, category/date required, note max 200; submit once; retain values on failure.
5. **Navigation:** Success replaces/pops to TX-03. Back with unsaved changes opens discard dialog.
6. **Constraints:** Numeric keyboard for amount; keyboard must not cover focused field/CTA; currency fixed to VND.

### TX-03 Transaction Detail

1. **Layout:** `Scaffold -> AppBar(actions) -> SingleChildScrollView -> Column`.
2. **Components:** Amount header, detail rows, edit button, delete button, confirmation dialog.
3. **States:** Loading, populated, error, deleting.
4. **Interactions:** Edit opens TX-02; delete confirms; success shows Snackbar Undo.
5. **Navigation:** Back returns to actual source. Undo restores and reopens detail if requested.
6. **Constraints:** Destructive action visually separated; dialog names the transaction and impact.

### BD-01 Budget Dashboard

1. **Layout:** `Scaffold -> AppBar -> RefreshIndicator -> ListView`.
2. **Components:** Month summary, status legend, budget cards, add button, state patterns.
3. **States:** Loading, empty, populated, error, offline.
4. **Interactions:** Change month; open detail; add budget.
5. **Navigation:** Root tab; opens BD-02/BD-03.
6. **Constraints:** Progress clamped visually but actual percentage remains in label; status uses icon/text/color.

### BD-02 Budget Detail

1. **Layout:** `Scaffold -> AppBar -> CustomScrollView` with summary then transaction list.
2. **Components:** Budget progress, status explanation, action cards, transaction rows.
3. **States:** Loading, safe, warning, exceeded, error.
4. **Interactions:** Edit limit; open filtered transactions; open insights.
5. **Navigation:** Back returns to budget list or notification source.
6. **Constraints:** Warning copy is neutral; transaction total must reconcile with displayed spent amount.

### BD-03 Create/Edit Budget

1. **Layout:** `Scaffold -> AppBar -> Form -> SingleChildScrollView`; sticky submit.
2. **Components:** Category selector, amount field, threshold control, month selector, submit button.
3. **States:** Default, validation error, submitting, network error.
4. **Interactions:** Limit `> 0`; threshold 50-100%; duplicate category/month produces explicit error.
5. **Navigation:** Success opens BD-02; Back with changes confirms discard.
6. **Constraints:** Threshold has numeric label; slider is not the only input method.

### IN-01 Insights

1. **Layout:** `Scaffold -> AppBar -> SingleChildScrollView -> Column`.
2. **Components:** Period selector, KPI card, chart with legend, text summary, source rows, export button.
3. **States:** Loading, insufficient data, populated, error.
4. **Interactions:** Change month; select category; open source transactions; export.
5. **Navigation:** Opens TX-01 filtered or EX-01. Back returns to Home.
6. **Constraints:** Chart has semantic label and full text alternative; no horizontal clipping.

### EX-01 Export Report

1. **Layout:** `Scaffold -> AppBar -> SingleChildScrollView -> Column`.
2. **Components:** Month selector, contents card, export button, job progress, report history row.
3. **States:** Default, processing, ready, failed, expired.
4. **Interactions:** Create PDF; retry upload; open ready URL.
5. **Navigation:** Back returns to the source screen; open uses platform viewer/browser.
6. **Constraints:** Disable duplicate export while processing; failure includes actionable reason.

### NT-01 Notification Center

1. **Layout:** `Scaffold -> AppBar(action) -> ListView`.
2. **Components:** Notification row, unread indicator, empty/error/loading patterns.
3. **States:** Loading, empty, populated, error.
4. **Interactions:** Tap marks read and opens target; mark all read.
5. **Navigation:** Budget alert opens BD-02. Back returns to Home/Profile source.
6. **Constraints:** Timestamp is readable; unread state uses label/semantics, not only color.

### ST-01 Profile

1. **Layout:** `Scaffold -> AppBar -> ListView` grouped into account, app demo and session sections.
2. **Components:** Profile header, settings rows, value rows, outlined/destructive buttons, confirmation dialog.
3. **States:** Default, offline, sign-out confirmation.
4. **Interactions:** Open notifications/export; show Remote Config values; trigger Lab 3 demo controls; sign out.
5. **Navigation:** Root tab; sign out clears stack and opens AU-01.
6. **Constraints:** Crash control is clearly labeled test-only and separated from common actions; email truncates safely.

## 5. State ownership

| Screen | Required runtime states |
| --- | --- |
| Login | Idle, loading, error |
| Home | Loading, empty, data, partial error, offline |
| Transaction List | Loading, empty, filtered empty, data, error |
| Add/Edit Expense | Editing, validating, submitting, submit error |
| Transaction Detail | Loading, data, error, deleting |
| Budget Dashboard | Loading, empty, data, error |
| Budget Detail | Loading, safe, warning, exceeded, error |
| Budget Form | Editing, validating, submitting, submit error |
| Insights | Loading, insufficient data, data, error |
| Export | Idle, processing, ready, failed, expired |
| Notifications | Loading, empty, data, error |
| Profile | Data, offline, signing out |

## 6. Content and formatting

- Currency: VND with Vietnamese grouping, for example `1.250.000 đ`.
- Date: `dd/MM/yyyy` in detailed views; relative date may appear in lists with accessible full date.
- Amount and limit use integer minor-unit-safe representation in implementation; UI never calculates with floating-point display strings.
- Merchant max 80 characters; note max 200 characters.
- Error messages state what failed, why when known, and what the user can do.

