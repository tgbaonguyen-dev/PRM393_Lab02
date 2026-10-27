# P02: Trần Thảo, the before-spending checker

> Bản tiếng Việt: [P02: Trần Thảo](../../../vi/research/personas/P.02.md).
>
> Status: Proto-persona. This profile is based on the product scope and assumptions about user behavior. It has not been validated through user research.

[Back to the persona overview](README.md).

**Role:** Secondary persona  
**Age:** 20  
**Context:** Second-year student renting away from home and managing a fixed monthly living allowance  
**Primary device:** Android phone  
**Financial knowledge:** Basic to intermediate

## Story

Thảo divides the monthly allowance among food, rent, transport, and study costs. Detailed accounting is unnecessary. Thảo needs to know which category is being spent faster than planned and how a new purchase will affect the rest of the month.

Some apps show a spending total or a percentage chart, leaving Thảo to calculate the remaining amount. A red or yellow warning is also hard to interpret when it gives no reason. Thảo needs the remaining amount, the budget status, and the transactions behind the figure.

## Behaviors

- Checks Home before an unusual or meaningful purchase.
- Pays more attention to the remaining amount than to a spending total by itself.
- Compares the remaining budget with the number of days left in the month.
- Opens Budget Detail when a category shows a warning.
- Reviews source transactions to understand the figures.
- Changes a limit only when the plan or circumstances have changed.
- Reviews Insights around the middle or end of the month.

## Goals

- Notice a category requiring attention quickly.
- Know how much remains available in each category.
- Understand why a budget is safe, near its limit, or exceeded.
- Adjust spending before the money runs out.
- Have enough information to keep or change a limit deliberately.

## Needs

- Remaining amount, percentage used, and limit shown together.
- Warnings that use an icon, label, and figures, with color as a supporting cue.
- Budget Detail that explains the cause and lists related transactions.
- Insights with a legend and a written summary equivalent to the chart.
- Neutral warning language that does not blame the user.
- Accurate percentage and remaining amount after a limit changes.

## Pain points

- Total spending appears without showing how much remains.
- Percentages lack an amount or time context.
- Warnings provide no cause or next step.
- Color is the only way to identify a status.
- Charts do not help with a decision.
- Aggregate figures cannot be traced to their transactions.
- The wording makes an exceeded budget feel like a personal failure.

## Motivations

- Make the living allowance last until the end of the month.
- Spend with more confidence when the remaining limits are clear.
- Notice risk before very little money remains.

## Constraints

- Monthly funds are limited and difficult to replace unexpectedly.
- There is little time for long financial reports.
- Information must be understandable on a small screen within seconds.
- Status must remain clear outdoors and for users who have difficulty distinguishing colors.

## JTBD

> When I am considering a new expense, I want to know which budget is nearly exhausted and how much remains so that I can decide whether the expense fits my plan.

## Primary scenario

Before going out for a meal with friends, Thảo opens Home and sees that Food has used 84.5% of its budget. The "Near Budget Limit" label appears with the remaining amount, an icon, and a progress bar. In Budget Detail, Thảo reviews the related transactions and notices several restaurant expenses during the week. Thảo keeps the existing limit and decides to spend less on eating out during the remaining days.

## Success criteria

- Identifies the at-risk category from Home in under 10 seconds.
- States the remaining amount and understands the warning.
- Opens the source transactions for the category.
- Interprets the figures without a calculator or another application.
- Recognizes the status without depending on color.

## Design implications

- Home prioritizes the remaining amount and categories requiring attention.
- Budget cards show spent, limit, remaining, percentage, and status.
- Warning and exceeded states combine icon, text, figures, and color.
- Budget Detail links to filtered transactions and Insights.
- Every chart has an equivalent written summary.
- Content uses neutral language and gives a concrete next step.
