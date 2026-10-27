# Expense Tracker users

> [Bản tiếng Việt](../../../vi/research/personas/README.md). This is a translation of the canonical Vietnamese personas. Update the Vietnamese version first, then synchronize this translation.

## Target users

Expense Tracker is intended for students aged 18 to 24 who live away from their families and manage their own living expenses. They mainly use Android phones, make many small purchases during the day, and do not want a complicated financial tool.

Their money may come from a monthly family allowance, part-time work, or both. They need to know how much they have spent, how much remains, and how a new expense will affect the rest of the month.

## Problem statement

Students living away from home need a quick and understandable way to record daily expenses and track category limits. When records are incomplete, they often notice overspending only near the end of the month.

## The three proto-personas

### Nguyễn Minh

Minh usually records an expense soon after payment. The entry form needs to be short, provide clear feedback, and retain data when the connection fails.

Details: [P01, the in-the-moment recorder](P.01.md).

### Trần Thảo

Thảo checks the budget before a purchase that needs consideration. The remaining amount, reason for a warning, and source transactions matter most.

Details: [P02, the before-spending checker](P.02.md).

### Lê Huy

Huy reviews transactions weekly or at month-end. Huy needs quick search and correction, confirmation before deletion, and a way to recover from mistakes.

Details: [P03, the reviewer and corrector](P.03.md).

These profiles are proto-personas based on the product scope and assumptions about user behavior. They have not been validated through interviews or observation.

## Success criteria

- A user adds an expense and sees the updated budget in under 20 seconds.
- From Home, a user identifies the category at risk of exceeding its budget in under 10 seconds.
- A user can correct a transaction or recover from an accidental deletion without losing control of the data. Deletion requires confirmation and supports Undo.
- A user selects a month, generates a PDF report, and opens it after processing succeeds.

These criteria will guide the scenarios, user flows, and test plan in the next steps.
