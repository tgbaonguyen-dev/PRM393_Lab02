# P01: Nguyễn Minh, the in-the-moment recorder

> Bản tiếng Việt: [P01: Nguyễn Minh](../../../vi/research/personas/P.01.md).
>
> Status: Proto-persona. This profile is based on the product scope and assumptions about user behavior. It has not been validated through user research.

[Back to the persona overview](README.md).

**Role:** Primary persona  
**Age:** 21  
**Context:** Third-year student living away from family and managing a monthly living allowance  
**Primary device:** Android phone  
**Financial knowledge:** Basic

## Story

Minh receives living money at the beginning of each month and earns a little extra from part-time work. Most expenses are small: meals, transport, study supplies, and a few digital services. Minh once used a notes app to track spending, but stopped because each entry took too long and gave no immediate sense of how the budget had changed.

An expense is easy to remember just after payment. By the end of the day, Minh may forget it or recall only an approximate amount. Expense entry therefore needs to work while Minh is walking, waiting in line, or holding the phone with one hand.

## Behaviors

- Records an expense immediately after payment or later that day.
- Prioritizes amount, category, and date. Merchant and note are entered only when the extra context is useful.
- Returns to Home after saving to check the budget.
- Uses bank or e-wallet history to recover forgotten expenses.
- Stops tracking when the form is long, feedback is slow, or an error requires re-entry.
- Uses the application in short sessions.

## Goals

- Record an expense before forgetting it.
- Complete entry quickly without instructions.
- Know whether the transaction is saving, saved, or failed.
- See updated spending and remaining budget immediately.
- Maintain the habit without making it feel like bookkeeping.

## Needs

- A short form with clearly identified required fields.
- A numeric keyboard and readable VND formatting.
- Input that remains available after validation or network failure.
- Retry without duplicate transactions.
- Success feedback confirming the transaction and budget update.
- Back behavior that warns before discarding unsaved data.

## Pain points

- Too many fields make entry slow.
- Required fields and validation errors are unclear.
- A slow save action encourages repeated taps.
- Entered data disappears after a connection failure.
- It is unclear whether the transaction was recorded.
- Missing or duplicate transactions make the total unreliable.

## Motivations

- Understand where the money went.
- Avoid surprises near the end of the month.
- Manage money without learning complex financial concepts.

## Constraints

- Limited time and attention during entry.
- Unstable network connectivity.
- One-handed use on a small screen.
- Little familiarity with accounting terms or advanced financial charts.
- Requires readable content, clear contrast, and sufficiently large touch targets.

## JTBD

> When I have just paid for something, I want to record the expense before I forget so that my remaining budget reflects my actual situation.

## Primary scenario

After paying for lunch, Minh opens Expense Tracker from Home and selects "Add Expense." Minh enters the amount, selects Food, and keeps the default date. The save button shows progress after being pressed. If the connection fails, the values remain in the form so Minh can retry. Once the save succeeds, the new transaction appears and the Food budget changes with it.

## Success criteria

- Adds an expense and sees the updated budget in under 20 seconds.
- Does not re-enter data after validation or network failure.
- Retry does not create a duplicate transaction.
- The new transaction appears once.
- Understands the remaining amount without calculating it manually.

## Design implications

- Add Expense needs to be easy to find on Home and Transactions.
- The form focuses on amount, category, and date. Merchant and note remain optional.
- Validation appears next to the relevant field.
- The submitting state prevents another request while the first is processing.
- A network error explains the cause, retains input, and offers Retry.
- Saving updates the transaction and budget together.
