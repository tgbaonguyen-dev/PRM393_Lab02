# Sổ Chi Tiêu — PRM393 Lab 2

Sổ Chi Tiêu is an Android-first personal expense tracker for Vietnamese students living away from home. It helps users record small daily expenses, understand monthly and category budgets, recover safely from mistakes, and export a monthly PDF report.

## Target persona

The primary persona is **Nguyễn Minh**, 21, a third-year student in Ho Chi Minh City. Minh receives a monthly allowance and irregular part-time income, frequently records expenses one-handed, sometimes has weak mobile data, and expects each session to take less than one minute.

Supporting personas and research assumptions are documented in [docs/en/research/personas](docs/en/research/personas/README.md) and [docs/vi/research/personas](docs/vi/research/personas/README.md).

## Three primary flows

1. **FL-01 — Add an expense:** Home or Transactions → Add Expense → Saving → updated figures, with validation and retry recovery.
2. **FL-02 — Delete and restore:** Transactions → Transaction Detail → confirmation → Deleted With Undo → deleted or restored.
3. **FL-03 — Review budget and export PDF:** Budgets → Category Budget → Insights → Export → Processing → Generated, with empty and failed states.

See [English user flows](docs/en/ux/user-flows.md) or [Vietnamese user flows](docs/vi/ux/user-flows.md).

## Figma

- [PRM323 Lab 2 — Expense Tracker](https://www.figma.com/design/o0Y3nMC1Du2It20MpmyvnP/PRM323-Lab-2-%E2%80%93-Expense-Tracker--Copy-?m=auto)
- Final UI frame: `360 × 800 dp`
- Required pages: `01 User Flow`, `02 Wireframe`, `03 Final UI`, `04 Design System`, `05 Components`, `06 Prototype`
- Before submission, verify the link in a private browsing window with view access.

## Deliverable map

| Deliverable | Location |
| --- | --- |
| Lab 2 checklist | [docs/en/requirements/lab2.md](docs/en/requirements/lab2.md) |
| Product requirements | [docs/en/requirements/expense-tracker-srs.md](docs/en/requirements/expense-tracker-srs.md) |
| Personas and problem context | [docs/en/research/personas](docs/en/research/personas/README.md) |
| Information architecture | [docs/en/ux/information-architecture.md](docs/en/ux/information-architecture.md) |
| Three user flows | [docs/en/ux/user-flows.md](docs/en/ux/user-flows.md) |
| Design system specification | [docs/design/design.md](docs/design/design.md) |
| Screen specification | [docs/design/screen-spec.md](docs/design/screen-spec.md) |
| Design decisions and accessibility audit | [docs/design/design-decisions.md](docs/design/design-decisions.md) |
| AI prompt and refinement log | [docs/logs/prompt-logs.md](docs/logs/prompt-logs.md) |
| Flutter handoff | [handoff/flutter-handoff.md](handoff/flutter-handoff.md) |

Vietnamese and English requirement/UX documents use matching directory structures. The Vietnamese documents are canonical when the two languages conflict.

## AI tools

| Tool | Purpose |
| --- | --- |
| Google Stitch | Initial UI generation and three targeted refinement rounds |
| ChatGPT / Codex | Requirement analysis, UX critique, documentation, Figma consistency review, and prototype audit |
| Figma AI | Component, screen, and prototype assistance inside Figma |

Exact prompts, before/after evidence, findings, and decisions are recorded in [docs/logs/prompt-logs.md](docs/logs/prompt-logs.md).

## Scope

- Lab 2 contains UX analysis, UI design, prototype, design system, and implementation handoff only.
- Flutter and backend implementation are deferred to Lab 3.
- Receipt OCR, bank synchronization, social features, AI coaching, debt management, and investing are outside the MVP.

