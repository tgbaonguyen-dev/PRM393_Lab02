# Expense Tracker project documentation

> Bản tiếng Việt: [../vi/README.md](../vi/README.md).

This directory is the starting point for the project's documentation. The documents follow the project from the course requirements through user research and product specification.

## Reading order

1. [PRM323 Lab 2 requirements](requirements/lab2.md): scope, deliverables, and submission checklist.
2. [Persona overview](research/personas/README.md): target users, problem statement, and three proto-personas.
3. [Expense Tracker SRS](requirements/expense-tracker-srs.md): product scope, business rules, functional and non-functional requirements, data model, and acceptance criteria.
4. [Information Architecture](ux/information-architecture.md): navigation structure, screen catalogue, and relationships between screens.
5. [User Flows](ux/user-flows.md): three primary flows, alternative branches, and recovery behavior.

Each English document links back to its canonical Vietnamese source at the top of the file. The two languages use matching directory trees under `docs/vi/` and `docs/en/`.

## Current structure

```text
docs/
├── vi/
│   ├── README.md
│   ├── requirements/
│   ├── research/personas/
│   └── ux/
└── en/
    ├── README.md
    ├── requirements/
    ├── research/personas/
    └── ux/
```

## Content ownership

| Topic | Source of truth |
| --- | --- |
| Lab conditions and deliverables | `requirements/lab2.md` |
| Application behavior, business rules, and acceptance criteria | `requirements/expense-tracker-srs.md` |
| Personas | `../vi/research/personas/` |
| English translations | The matching files in the current `docs/en/` tree |
| Information architecture and screen catalogue | `ux/information-architecture.md` |
| Three user flows and the flow-to-screen matrix | `ux/user-flows.md` |

The Vietnamese documents are the canonical sources for all bilingual documentation. When content changes, update the Vietnamese source first and then synchronize the English translation. Requirement IDs, flow IDs, screen IDs, enums, fields, and formulas must remain unchanged in translation.

## Documents added as the project progresses

The following documents should be created only when the team reaches the relevant stage and has genuine supporting evidence:

- AI design log and Google Stitch evidence.
- Design specification for tokens, components, states, content tone, and responsive behavior.
- Design decisions and accessibility evidence.
- Screen specification.
- Flutter handoff.

Do not create placeholders or reconstruct logs after the fact merely to fill the directory tree.
