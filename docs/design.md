# Design Principles

Use this file to define the product's interaction and visual direction. Replace placeholders with product-specific guidance before heavy UI work begins.

## UI Foundation — Choose At Kickoff

No system is selected by default. Ask which UI foundation or component library to use: a named system, native platform controls, a recommendation, or not applicable.

- Selected foundation: `[unresolved / selection]`
- Authoritative documentation or local reference: `[URL or path; required before using an unfamiliar system]`
- Version / revision, when applicable: `[version]`
- Why it fits the platform and core workflow: `[reason]`
- Constraints or intentional deviations: `[details or none]`

Resolve the selection before substantial UI work. This choice is blocking for a product with a GUI. If asked to recommend, explain the fit and tradeoffs before resolving the choice. If the chosen system's source is unavailable, ask for a reference rather than inventing its conventions. Record technical implications in `ARCHITECTURE.md` and durable rationale in `DECISIONS.md`.

The UI foundation supplies primitives and conventions; define the product's visual identity and interaction direction below. For products without a GUI, mark the foundation and the visual sections not applicable.

## Emotional Tone

Emotional goals are authoritative in `PRODUCT.md`. Use the fields below to say how those feelings show up in interaction and visuals. If a feeling needs to change, change it in `PRODUCT.md`.

How the emotional goals show up:

- `[interface behavior or visual choice]`
- `[interface behavior or visual choice]`
- `[interface behavior or visual choice]`

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

For meaningful UI changes, exercise the actual core workflow at relevant viewport or device sizes, including empty, loading, and error states. Check keyboard/focus behavior, readable contrast, labels, and reduced motion where relevant. A single screenshot is not verification. Record what you exercised and what you observed, including screenshot paths when they support that record. If visual tools are unavailable, state that limitation and provide exact manual checks; do not claim visual verification.
