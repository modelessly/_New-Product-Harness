# Design Principles

Use this file to define the product's interaction and visual direction. Replace placeholders with product-specific guidance before heavy UI work begins.

## UI Foundation — Choose At Kickoff

No system is selected by default. Ask which foundation to use: **Modeless**, **shadcn/ui**, **native platform controls**, **another/custom system**, **recommend based on the product**, or **not applicable**.

- Selected foundation: `[unresolved / selection]`
- Authoritative documentation or local reference: `[URL or path; required before using an unfamiliar system]`
- Version / revision, when applicable: `[version]`
- Why it fits the platform and core workflow: `[reason]`
- Constraints or intentional deviations: `[details or none]`

Resolve the selection before substantial UI work. If asked to recommend, explain the fit and tradeoffs before resolving the choice. Do not invent Modeless conventions when its source is unavailable. Record technical implications in `ARCHITECTURE.md` and durable rationale in `DECISIONS.md`.

The UI foundation supplies primitives and conventions; define the product's visual identity and interaction direction below. For products without a GUI, mark visual sections not applicable.

## Emotional Tone

The product should feel:

- `[tone]`
- `[tone]`
- `[tone]`

The product should avoid feeling:

- `[anti-tone]`
- `[anti-tone]`
- `[anti-tone]`

## Interaction Philosophy

Define the preferred interaction posture:

- `[Example: fast actions over configuration]`
- `[Example: low friction over completeness]`
- `[Example: direct manipulation over hidden automation]`

The user should never feel:

- `[frustration to avoid]`
- `[frustration to avoid]`
- `[frustration to avoid]`

## Visual Direction

Inspired by:

- `[reference]`
- `[reference]`
- `[reference]`

But visually:

- `[visual quality]`
- `[visual quality]`
- `[visual quality]`

Avoid:

- `[visual anti-pattern]`
- `[visual anti-pattern]`
- `[visual anti-pattern]`

## Motion

Motion should feel:

- `[quality]`
- `[quality]`

Avoid:

- `[motion anti-pattern]`
- `[motion anti-pattern]`

## Layout

Prioritize:

- clear hierarchy
- generous touch or click targets
- readable content
- obvious primary action
- minimal chrome around the core workflow

## Accessibility

At minimum, support:

- readable type sizes
- sufficient contrast
- keyboard navigation where relevant
- screen reader labels for important controls
- clear focus, loading, empty, and error states

## UI Verification

For meaningful UI changes, inspect the actual rendered core workflow at relevant viewport or device sizes. Check keyboard/focus behavior, readable contrast, labels, reduced motion where relevant, and empty/loading/error states. Record observations or screenshot paths in the task handoff. If visual tools are unavailable, state that limitation and provide exact manual checks; do not claim visual verification.
