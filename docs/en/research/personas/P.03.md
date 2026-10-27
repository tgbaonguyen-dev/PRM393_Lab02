# P03: Lê Huy, the reviewer and corrector

> Bản tiếng Việt: [P03: Lê Huy](../../../vi/research/personas/P.03.md).
>
> Status: Proto-persona. This profile is based on the product scope and assumptions about user behavior. It has not been validated through user research.

[Back to the persona overview](README.md).

**Role:** Secondary persona  
**Age:** 22  
**Context:** Final-year student living away from family, earning part-time income, and reviewing expenses weekly or at month-end  
**Primary device:** Android phone  
**Financial knowledge:** Intermediate

## Story

Huy does not record every expense immediately. At the end of a week or month, Huy opens Expense Tracker and compares it with e-wallet and bank histories. Accurate transactions make the spending total and budget trustworthy.

A transaction may have the wrong amount, use the wrong category, or appear twice. Huy wants to correct it without losing the current filter or place in the list. Before deletion, the app needs to identify exactly what will disappear. If Huy confirms by mistake, Undo needs to remain available until he restores the transaction or explicitly dismisses the message, including after reopening the app. The monthly report becomes useful once the figures reconcile.

## Behaviors

- Reviews transactions in batches, usually at the weekend or month-end.
- Searches by merchant, date, or category.
- Filters and sorts the list to compare it with another source.
- Corrects an amount, category, date, or note when it is wrong.
- Checks spending and budgets after each edit or deletion.
- Reviews the monthly report once the data appears complete.
- Uses Undo as soon as an accidental deletion is noticed.

## Goals

- Find the correct transaction in a long list.
- Correct data without creating a new transaction or changing unrelated fields.
- Understand the effect before confirming deletion.
- Recover quickly from an accidental deletion.
- Keep Home, Budgets, and Insights consistent.
- Open a monthly report that can be checked against the transaction list.

## Needs

- Search, category filters, and sorting by date or amount.
- Transaction Detail with amount, category, date, merchant, and note.
- An edit form that retains current values and changes only edited fields.
- A delete dialog that identifies the transaction and its impact.
- A visible Undo snackbar with an accessible action.
- A PDF with a summary, category breakdown, and transaction list.
- Back navigation that returns to the actual source and preserves filters.

## Pain points

- Long transaction lists without useful search or filtering.
- Similar transactions lack enough information to tell them apart.
- Totals do not update correctly after editing.
- Delete acts immediately without confirmation.
- An accidental deletion cannot be recovered.
- Back loses filters or returns to the wrong screen.
- Reports do not state the period or included content clearly.

## Motivations

- Trust that the figures match actual spending.
- Find duplicate or misclassified transactions.
- Keep a clear monthly summary for review or storage.

## Constraints

- May need to compare several data sources.
- Some transactions look similar in the list.
- Reviews usually happen at the weekend or month-end.
- Edit, cancel, and delete actions must be easy to distinguish.
- One incorrect action must not damage data that has already been checked.

## JTBD

> When my total spending does not match my expectation, I want to find and correct the relevant transaction so that I can trust the budget and monthly report.

## Primary scenario

At month-end, Huy opens Transaction List and filters by Food. One expense appears twice. Huy opens Transaction Detail and selects Delete. The confirmation dialog identifies the transaction that will be removed. After confirmation, the list and budget are recalculated, and a snackbar offers Undo. Huy checks the result and explicitly dismisses the snackbar to complete the deletion. Once the figures reconcile, Huy reviews Insights and opens the PDF report.

## Success criteria

- Finds the transaction using search, filtering, or sorting.
- Edit changes only the selected data and updates totals accurately.
- Cancel does not delete data.
- Undo restores the correct transaction once and recalculates the budget.
- The report shows the correct month, summary, category breakdown, and transaction list.
- Back returns to the actual source without losing context.

## Design implications

- Transaction List needs clear search, category filters, and sorting.
- Transaction rows include enough information to distinguish similar expenses.
- Edit Expense reuses the form with the current values filled in.
- Delete always opens a confirmation dialog and offers Undo after success.
- Transaction changes update Dashboard, Budget, and Insights together.
- Export Report has default, processing, ready, and failed states.
