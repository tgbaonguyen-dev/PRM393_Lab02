# PRM323 Lab 2 Requirements

> Vietnamese source: [`../../vi/requirements/lab2.md`](../../vi/requirements/lab2.md).

This document is the normalized checklist derived from the Lab 2 brief. If any conflict exists, the original assignment and the lecturer's direct instructions take precedence.

## 1. Required scope

- Design a mobile application that solves a real problem for a specific user group.
- Include at least 8 distinct screens. Dialogs and state variants do not count as separate screens.
- Include at least 3 complete user flows, each with a clear starting point, goal, and end state.
- Each flow must include a happy path and at least one alternative branch.
- Include at least one error or recovery branch.
- Do not write Flutter code in Lab 2.

## 2. Required process

Complete the work in this order:

1. Analyze: persona, problem statement, and success criterion.
2. Analyze: information architecture and user flow.
3. Define: color, typography, spacing, tone, and component rules.
4. Generate: create the initial UI with Google Stitch.
5. Critique: complete at least 3 iterations, each addressing a distinct and specific issue.
6. Refine: create wireframes and Final UI in Figma.
7. Systemize: create tokens and component variants.
8. Prototype: connect 3 flows from start to finish.
9. Handoff: write Flutter specifications detailed enough for another person to implement.

## 3. Evidence of AI use

- Save the exact Google Stitch prompt and screenshots of its initial result.
- Complete at least 3 refinement rounds; record the issue, prompt, before/after images, and decision for each round.
- Ask AI to critique the design using Nielsen heuristics, accessibility, and the persona.
- The critique must contain at least 5 findings tied to specific screens.
- For every important suggestion, record `Accept`, `Modify`, or `Reject` with a reason.
- Declare every AI tool used and its purpose.

Do not reconstruct the log after the work is finished. Update it during the process and link it to real evidence.

## 4. Required Figma structure

The Figma file must contain exactly six pages in this order:

1. `01 User Flow`
2. `02 Wireframe`
3. `03 Final UI`
4. `04 Design System`
5. `05 Components`
6. `06 Prototype`

Final UI uses `360 x 800 dp` frames. Place state variants next to the corresponding screen.

## 5. Design system and components

Tokens must be defined with Figma Variables or Styles and used by components:

- Color
- Typography
- Spacing
- Radius
- Elevation

Minimum component set:

| Component | Required states |
| --- | --- |
| Button | Default, pressed, disabled, loading |
| Text field | Default, focused, filled, error, disabled |
| Card | Default, pressed when interactive |
| Navigation | Selected state for every destination |
| App bar | Default with an action |
| Dialog | Confirm and cancel/error |
| Loading | Screen-level pattern |
| Empty | Icon/illustration, message, action |
| Error | Message, understandable cause, retry action |

Every component must use Auto Layout, variants, and semantic tokens. Screens must use component instances without detaching them.

## 6. Accessibility and responsive behavior

- Contrast: `4.5:1` for normal text; `3:1` for large text and UI controls.
- Minimum touch target: `48 x 48 dp`.
- Minimum body text size: `14 sp`.
- Do not communicate information through color alone.
- Check layouts at widths of `360 dp` and `412 dp`.
- Handoff must describe behavior at widths of `600 dp` and above.
- Record actual results in `design/design-decisions.md`.

## 7. Prototype

- All three flows must be clickable from start to finish and have a starting point.
- Back returns to the correct source without creating dead ends.
- Include at least one dialog overlay.
- Include at least one loading-to-result transition.

## 8. Flutter handoff

Every screen must specify:

1. Layout.
2. Components and variants.
3. States.
4. User interactions and validation.
5. Navigation and Back behavior.
6. Important UI constraints.

Also include token-to-Flutter and component-to-widget mapping tables.

## 9. Submission checklist

- [ ] The repository opens in a private browsing window.
- [ ] The Figma link opens with view permission.
- [ ] README includes the topic, persona, Figma link, AI tools, and deliverable map.
- [ ] Final UI contains at least 8 distinct screens.
- [ ] All 3 flows and the flow-to-screen table are present.
- [ ] An error or recovery branch is present.
- [ ] All 6 Figma pages exist in the correct order.
- [ ] Required components and states are complete.
- [ ] The accessibility checklist contains real evidence.
- [ ] The prototype has no dead ends.
- [ ] Handoff contains all six required items for every screen.
- [ ] The AI log contains exact prompts and before/after images.
