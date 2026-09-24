# LinkedIn Scorecard

## Product Requirements Document

**Status:** Build kickoff  
**Working title:** LinkedIn Scorecard  
**Primary build target:** Phase 1 file-based MVP  
**Audience:** Product, design, engineering, Grok, and Cursor  
**Last updated:** 23 September 2026

---

## 1. Product summary

LinkedIn Scorecard analyzes data a person exports from their own LinkedIn account and turns it into an evidence-based assessment of their professional presence.

It should help the user answer four questions:

1. How healthy and effective is my LinkedIn presence?
2. What does my profile and activity currently suggest I am known for?
3. How closely does that match what I want to be known for?
4. What are the few highest-value things I should change next?

The core experience is:

> Upload LinkedIn data → inspect and analyze it privately → receive a clear scorecard → understand what to improve

The score attracts attention. The product's real value is the diagnosis, evidence, and prioritized guidance behind it.

---

## 2. Product thesis

LinkedIn contains a rich history of a person's professional identity, network, publishing, and participation, but gives users little help interpreting the combined picture.

Most existing LinkedIn scoring and coaching products rely on public-profile scraping, generic advice, self-reported information, or opaque scoring. This product should be differentiated by using data the user owns and exports directly from LinkedIn.

The product should measure whether the user's LinkedIn presence contributes to a coherent, credible, and increasingly visible professional reputation. It must not simply reward spending more time on LinkedIn.

---

## 3. Product principles

### Evidence before advice

Every important score, insight, and recommendation must be traceable to specific data.

### Outcomes over activity

Posting, reacting, or connecting more is not automatically better. Meaningful professional signals should matter more than raw volume.

### Honest uncertainty

If the available files do not support a conclusion, show that the result is unavailable or low-confidence. Never invent missing metrics.

### Privacy as product behavior

Only supported files should be processed. Private messages, contact details, job applications, security information, and other irrelevant data must be ignored.

### Interpretation over dashboards

Users should not have to interpret a wall of charts. The product should explain what matters and what to do next.

### Restrained professional tone

The product should feel credible, analytical, calm, and useful. Avoid influencer language, vanity-metric obsession, gamification, confetti, exaggerated AI claims, or fake precision.

---

## 4. Target users

The initial target is a professional who intentionally cares about their reputation on LinkedIn and has enough history to analyze.

Examples:

- executives and senior professionals
- consultants and independent experts
- founders
- job seekers
- product, design, engineering, and technology leaders
- creators focused on professional topics
- people repositioning themselves into a new field

The MVP should work for less-active users too, but it should clearly explain when there is not enough data for a reliable conclusion.

---

## 5. Core jobs to be done

When I am trying to build or reposition my professional reputation, I want to understand what my existing LinkedIn presence actually communicates, so I can make better decisions about my profile, content, and relationships.

When I invest time in LinkedIn, I want to know which behaviors and themes are genuinely contributing to my goals, so I do not mistake activity for impact.

When I receive a score or recommendation, I want to see the evidence behind it, so I can decide whether I trust and act on it.

---

## 6. Phase 1 scope

Phase 1 is a global, file-based MVP with no dependency on LinkedIn API approval.

### Required input

- A ZIP archive produced by LinkedIn's Download Your Data feature

### Optional inputs

- LinkedIn Post Analytics XLSX
- LinkedIn Audience Analytics XLSX

The optional analytics files improve visibility and performance analysis. The product must remain useful without them.

### Required MVP capabilities

- public web application
- no account required for the first analysis
- drag-and-drop or file-picker upload
- safe client-side ZIP inspection and parsing where practical
- explicit supported-file whitelist
- resilient handling of missing, renamed, or additional files
- normalized internal data model
- deterministic metrics
- initial configurable scoring model
- per-dimension confidence or data-coverage state
- semantic content analysis through a replaceable AI adapter
- evidence-backed insights and recommendations
- vertically scrolling scorecard/report
- clear privacy explanation

### Explicitly out of scope

- LinkedIn scraping
- posting or scheduling to LinkedIn
- post generation as a primary feature
- social or community features
- CRM functionality
- agency/client dashboards
- browser extension
- mobile app
- teams and collaboration
- continuous monitoring
- complex authentication or billing
- competitive benchmarking without a defensible dataset
- claims about LinkedIn's ranking algorithm

---

## 7. Privacy and data handling

LinkedIn archives can contain sensitive information that is unnecessary for this product. The parser must use an allowlist, not ingest the entire archive.

### Supported archive files

The import layer should recognize these files case-insensitively and tolerate minor naming variations:

- `Connections.csv`
- `Invitations.csv`
- `Shares.csv`
- `Comments_*.csv`
- `Reactions.csv`
- `InstantReposts.csv`
- `Recommendations_Received.csv`
- `Endorsement_Received_Info.csv`
- `Profile.csv`
- `Profile Summary.csv`
- `Positions.csv`
- `Skills.csv`
- `Publications.csv`
- `Patents.csv`
- `Member_Follows_*.csv`
- `Company Follows.csv`
- `Rich_Media.csv`
- article HTML files nested under an `Articles` directory

Potential later additions:

- `Recommendations_Given.csv`
- `Events.csv`
- `Education.csv`
- `Languages.csv`

### Explicitly ignored files and categories

- `messages.csv` and all private-message data
- email addresses
- phone and WhatsApp numbers
- imported contacts
- login history
- security challenges
- job applications and saved job data
- receipts
- advertising targeting and click history
- any unknown file not on the allowlist

### Required privacy behavior

- Inspect and preprocess the archive in the browser where feasible.
- Do not upload raw ZIP contents to an application server in the initial milestone.
- Do not log raw rows, post bodies, names, profile URLs, or other personal data.
- Display which supported files were found, used, missing, or ignored.
- Make data retention behavior explicit.
- If AI analysis later requires sending selected text to a model, require clear disclosure and send only the minimum necessary content through a server-side adapter. Never expose provider keys in the client.

Preferred trust statement:

> We only analyze the LinkedIn files needed to create your scorecard. Private messages, contact information, job applications, and security data are ignored.

### Import safety requirements

- Reject unreasonable archive and uncompressed sizes.
- Limit file count and per-file size.
- Protect against ZIP bombs and path traversal.
- Treat all imported content as untrusted data.
- Sanitize rendered HTML and never execute archive content.
- Parse CSV robustly, including BOMs, quoted newlines, empty fields, and encoding errors.
- Unknown files and malformed optional files must not crash the whole import.

---

## 8. User journey

### 8.1 Landing

The landing page explains the value in plain language.

Working headline:

> Understand what your LinkedIn presence actually says about you.

Supporting copy:

> Upload your LinkedIn data to see how effectively you are building your professional reputation, what you are becoming known for, and what to improve next.

Primary action:

> Analyze my LinkedIn

Privacy should be visible before upload.

### 8.2 Upload and inspection

The user drops a LinkedIn ZIP into the browser. The product:

1. validates the file
2. inspects the archive
3. identifies supported files
4. ignores unsupported and sensitive files
5. parses valid inputs
6. reports import coverage and recoverable issues

Optional analytics exports can be added before or after the archive.

### 8.3 Goal setting

Ask:

> What do you want to be known for professionally?

The user supplies up to three concise themes, such as:

- AI
- product development
- design leadership

This step can be skipped. If skipped, the product may describe observed positioning but must not produce a Reputation Alignment score.

### 8.4 Analysis

Show brief, honest progress states such as:

- inspecting archive
- parsing supported data
- calculating activity and network metrics
- identifying professional themes
- preparing scorecard

Do not imply that unsupported data is being analyzed.

### 8.5 Results

The result is a single vertically scrolling report. The top of the report must immediately answer:

- How am I doing?
- What is my strongest signal?
- What is my biggest opportunity?
- What should I do next?

---

## 9. Core outputs

### 9.1 LinkedIn Score

An overall score from 0 to 100 representing the health and effectiveness of the user's LinkedIn professional presence.

The overall score must be derived from available scored dimensions only. Missing dimensions must not silently count as zero.

Initial dimensions:

#### Network

The development, relevance, and composition of the professional network.

Potential signals:

- connection count, capped to reduce size bias
- connection growth and recency
- company and role diversity
- concentration in a few employers or functions
- seniority distribution where defensibly inferred
- inbound and outbound invitation patterns where derivable

#### Authority

Evidence that other professionals recognize the user's expertise.

Potential signals:

- recommendations received, with recency
- endorsements received, treated as weaker than recommendations
- articles, publications, and patents
- depth and specificity of expertise
- sustained professional presence

#### Content

The health and coherence of publishing behavior.

Potential signals:

- original post count and recency
- publishing consistency
- active months rather than raw volume alone
- original-to-repost mix
- long-form publishing
- thematic clarity and concentration

#### Participation

Evidence that the user contributes to professional conversation rather than only broadcasting.

Potential signals:

- comments
- reactions
- reposts
- activity regularity
- balance between participation and publishing

Raw volume should have diminishing returns.

#### Visibility

Evidence that content reaches and matters to other people.

This dimension must be unavailable unless supported analytics data exists.

Potential analytics signals:

- impressions and members reached
- out-of-network reach
- reactions received
- comments received
- reposts received
- saves
- sends
- follower growth

Reposts, saves, and sends should generally carry more weight than lightweight reactions. The exact weights must remain configurable and testable.

### 9.2 Reputation Alignment

If the user supplies desired themes, calculate a separate alignment result showing how strongly their observed LinkedIn presence reinforces those themes.

Analyze:

- headline and profile summary
- positions and skills
- posts and articles
- comments where useful
- network composition only when a defensible relationship exists

Output:

- alignment percentage or clearly labeled band
- concise explanation
- observed supporting and conflicting signals
- profile-versus-content mismatch when present

The explanation matters more than apparent numerical precision.

### 9.3 Immediate diagnosis

Directly below the main scores, show:

- **Strongest signal:** the most credible positive pattern
- **Biggest opportunity:** the most consequential weakness or mismatch
- **Next move:** one concrete action supported by the data

### 9.4 Content intelligence

Derive semantically coherent themes from posts and articles.

Distinguish among:

- what the user talks about
- what performs best, when analytics exist
- what reinforces the user's desired reputation

Do not rely on keyword counting alone.

Example:

> AI and product development: 31%  
> Design leadership: 24%  
> Enterprise UX: 18%  
> Digital transformation: 15%  
> Other: 12%

### 9.5 Network intelligence

Potential outputs:

- connection growth timeline
- top companies and roles
- professional concentrations
- diversity across companies and functions
- network changes over time
- goal-aware gaps

Network composition is contextual. Do not label a concentration good or bad without reference to the user's stated professional goals.

### 9.6 Authority signals

Summarize evidence such as:

- recommendations received and recency
- endorsed skills
- long-form articles
- publications and patents
- years of visible professional history

### 9.7 Historical patterns

Use longitudinal data to identify patterns such as:

- consistent publishing versus bursts
- increasing or declining activity
- balance between original publishing and participation
- periods of network growth
- changes in professional themes

### 9.8 Prioritized actions

Provide no more than three recommendations.

Each recommendation must include:

- **Action:** what the user should consider doing
- **Evidence:** which observations caused the recommendation
- **Intended impact:** which score, signal, or positioning goal it addresses

Avoid generic LinkedIn advice and claims about LinkedIn's algorithm.

---

## 10. Explainability and confidence

Every score dimension needs a details view or `Why am I seeing this?` interaction.

Each scored dimension should expose:

- score
- data coverage or confidence
- metrics used
- short rationale
- important missing inputs

Suggested coverage states:

- High coverage
- Partial coverage
- Limited coverage
- Not enough data

Confidence describes data coverage, not certainty that the scoring philosophy is objectively correct.

---

## 11. Scoring model requirements

The initial scoring model is a configurable versioned model, not a permanent truth.

### Required rules

- Keep import, metrics, scoring, interpretation, and presentation separate.
- Store weights and thresholds in configuration, not UI components.
- Use diminishing-return transforms for volume-based signals.
- Normalize relative to meaningful caps or within-user history until credible population benchmarks exist.
- Never claim peer percentile rankings without a valid comparison dataset.
- Do not treat missing data as poor performance.
- Calculate dimension coverage separately from dimension score.
- Version every scoring model so future rescoring is reproducible.
- Return score contributions and reasons, not only final numbers.

### MVP scoring stance

Version 0 may be heuristic, but it must be transparent, deterministic, testable, and labeled as an initial model. AI may explain a score but must not freely choose it.

---

## 12. Information architecture and interface

The scorecard should behave like an editorial report rather than an enterprise analytics dashboard.

Recommended order:

1. Overall LinkedIn Score and data-coverage summary
2. Reputation Alignment, if the user supplied a goal
3. Strongest signal, biggest opportunity, and next move
4. Dimension scores with explainability
5. What you are currently known for
6. Content analysis
7. Network analysis
8. Authority signals
9. Historical activity patterns
10. Three recommended actions

### Visual direction

- editorial and analytical
- restrained neutral palette with one purposeful accent color
- strong typography and generous spacing
- clear hierarchy, compact data displays, and readable explanations
- desktop-first but responsive down to mobile
- accessible color contrast and keyboard navigation
- no radar chart as the primary score explanation
- no decorative charts that do not help interpretation

---

## 13. Technical architecture

The existing product harness conventions take precedence. If the harness does not prescribe a stack, use a modern TypeScript web application with React.

Conceptual pipeline:

```text
Import adapters
  → normalized domain model
  → deterministic metrics
  → configurable scoring model
  → AI interpretation adapter
  → evidence-backed report model
  → scorecard UI
```

### Architectural boundaries

#### Import

Understands external LinkedIn ZIP, CSV, HTML, and XLSX formats.

#### Normalize

Maps version-variable external formats into stable internal types.

#### Analyze

Calculates deterministic metrics and structured observations.

#### Score

Applies versioned weights, caps, transforms, and data-coverage rules.

#### Interpret

Uses structured evidence to derive themes and explain findings. AI output must conform to a schema and reference evidence IDs.

#### Present

Renders a report model without containing scoring logic.

### Suggested normalized entities

- `Profile`
- `Position`
- `Skill`
- `Connection`
- `Invitation`
- `Post`
- `Article`
- `Comment`
- `Reaction`
- `Repost`
- `Recommendation`
- `Endorsement`
- `Publication`
- `Patent`
- `AudienceSnapshot`
- `PostPerformance`
- `ImportManifest`
- `MetricObservation`
- `ScoreContribution`
- `ScoreDimension`
- `Insight`
- `RecommendedAction`

Every normalized record should retain source provenance without retaining more raw data than necessary.

### AI boundary

Use conventional code for:

- counts
- dates and intervals
- growth and consistency
- distributions
- ratios
- scoring transforms
- file validation

Use AI selectively for:

- semantic topic clustering
- theme labeling
- observed professional positioning
- desired-versus-observed alignment
- natural-language explanations
- evidence-backed recommendation wording

The application must remain testable without a live AI provider. Provide an adapter interface and deterministic fixture or stub.

---

## 14. Import and normalized-data requirements

The import result must include:

- archive metadata
- supported files found
- supported files parsed
- supported files missing
- unsupported files ignored
- warnings and recoverable errors
- row counts by source
- date range by source where applicable
- normalized entity counts
- parser/schema version

File matching must not assume the exact suffix in files such as `Comments_2982836.csv` or `Member_Follows_2982836.csv`.

Header mapping should be explicit, versionable, and tolerant of missing optional columns. Unknown columns should be ignored but reported for development diagnostics.

---

## 15. First implementation milestone

The first milestone proves that real LinkedIn archive data can be safely and reliably transformed into useful structured information.

### Build in Milestone 1

1. Application shell and restrained visual foundation
2. Landing/upload experience
3. Local ZIP inspection with safety limits
4. Supported-file detection and allowlist
5. Parsers for the initial core files:
   - `Profile.csv`
   - `Profile Summary.csv`
   - `Positions.csv`
   - `Skills.csv`
   - `Connections.csv`
   - `Shares.csv`
   - `Comments_*.csv`
   - `Reactions.csv`
   - `Recommendations_Received.csv`
   - `Endorsement_Received_Info.csv`
6. Normalized internal representation
7. Import report/debug view
8. Basic deterministic metrics:
   - date range
   - connection total and growth by month/year
   - post total, original/repost classification where possible, and cadence
   - active publishing months and longest gaps
   - comment and reaction counts over time
   - recommendation and endorsement totals/recency
   - profile/position/skill coverage
9. Synthetic, privacy-safe fixture archive
10. Unit tests for parsers and metrics
11. End-to-end happy-path upload test

### Do not build in Milestone 1

- final overall score
- production AI integration
- polished full dashboard
- authentication, persistence, payments, or subscriptions
- speculative analytics

### Milestone 1 output

A developer-visible analysis report that demonstrates:

> This archive was parsed safely, these records were extracted, these deterministic facts were calculated, and these limitations were detected.

---

## 16. MVP milestones after ingestion

### Milestone 2: Deterministic scorecard foundation

- score model v0 and configuration
- data coverage/confidence model
- Network, Authority, Content, and Participation dimensions
- unavailable Visibility state
- explainability details and score contributions
- first user-facing scorecard layout

### Milestone 3: Content and positioning intelligence

- AI provider adapter
- semantic topic clusters
- observed professional positioning
- desired reputation input
- Reputation Alignment
- evidence-linked explanations
- deterministic fallback when AI is unavailable

### Milestone 4: Action layer and optional analytics

- prioritized recommendations
- Post Analytics XLSX adapter
- Audience Analytics XLSX adapter
- Visibility score
- content-theme-to-performance comparisons
- completed responsive report

### Milestone 5: Validation build

- privacy and security review
- performance testing on large archives
- usability testing
- scoring calibration against real consenting users
- export/shareable summary if validated

---

## 17. Acceptance criteria for the Phase 1 MVP

The MVP is acceptable when:

- A user can upload a valid LinkedIn ZIP without extracting it.
- Parsing occurs locally unless the user is explicitly told otherwise.
- Sensitive and unknown files are ignored by design.
- The product identifies found, missing, ignored, and malformed inputs.
- Missing supported files do not cause the import to fail.
- Supported data is normalized independently of UI components.
- Deterministic metrics are covered by tests.
- Scoring is deterministic, versioned, configurable, and explainable.
- Missing analytics causes Visibility to show as unavailable, not zero.
- The user can state up to three desired professional themes.
- AI-generated findings reference structured evidence and can be replaced by a stub.
- The report presents no more than three prioritized recommendations.
- The interface is responsive, keyboard-accessible, and visually credible.
- No raw personal archive data appears in logs.

---

## 18. Success criteria and validation

The first validation question is not whether users agree with every point in the scoring model. It is whether the product reveals something useful and produces credible action.

Qualitative success signals:

> I did not know that about my LinkedIn presence.

> That explains why my profile and content feel disconnected.

> I know what I should change next.

> I would run this again in three months.

Early product metrics:

- percentage of uploads successfully parsed
- percentage of reports reaching a usable coverage threshold
- completion rate from upload to report
- percentage of users opening score explanations
- percentage reporting at least one useful or surprising insight
- intention to return and rerun the analysis

Do not optimize the initial build for sign-ups, virality, or time spent.

---

## 19. Monetization direction

Do not implement monetization in the validation build.

Working future model:

### Free

- overall and category scores
- data-coverage summary
- headline positioning assessment
- one or two important insights

### Paid

- complete diagnosis
- deeper content and network intelligence
- Reputation Alignment
- all recommendations
- historical tracking and rescoring
- repeated analysis
- defensible benchmarking if enough data exists
- ongoing guidance

The free score creates curiosity. The paid product helps the user improve.

---

## 20. Future roadmap

### Phase 2: LinkedIn Data Portability API

Explore LinkedIn's DMA Member Data Portability API for eligible EEA and Swiss users.

Goal:

- authenticated data access
- incremental updates where permitted
- reduced need for repeated manual imports

The file-based importer remains supported.

### Phase 3: LinkedIn Community Management APIs

Apply for appropriate LinkedIn API access.

Potential future capabilities:

- richer post analytics
- live reach and engagement data
- follower growth
- profile analytics
- continuous scorecard updates

Long-term experience:

> Connect LinkedIn → maintain a continuously updated professional reputation scorecard

Do not design Phase 1 around approval for either API.

---

## 21. Risks and open questions

### Product risks

- The score may feel arbitrary without strong explainability.
- Archive data may describe activity better than effectiveness.
- Users may interpret a professional-presence score as personal worth.
- Generic recommendations would quickly destroy trust.

### Data risks

- LinkedIn may change filenames, headers, and export coverage.
- Different users may receive materially different archives.
- Seniority, relevance, and network quality can be difficult to infer reliably.
- Optional analytics formats need validation against real current exports.

### Technical risks

- Large archives may strain browser memory.
- CSVs can contain malformed or multiline data.
- Article HTML must never be trusted or executed.
- Model-based clustering can be expensive, inconsistent, or leak unnecessary data if poorly designed.

### Open decisions

- Final product name
- Exact score weights and transforms
- Whether the primary score remains 0–100 or shifts to bands
- Minimum data threshold for each dimension
- Which content is safe and necessary to send for AI analysis
- Whether the initial AI provider is Grok or another model behind the same adapter
- Retention model once accounts and historical tracking exist

---

## 22. Working product statement

> LinkedIn Scorecard analyzes your LinkedIn data to show how effectively you are building your professional reputation, what you are becoming known for, and what you should improve next.

---

## 23. Instruction to the build team

Treat this PRD as product direction, not permission to invent unsupported capabilities.

Start with the ingestion vertical slice:

> upload → inspect → parse → normalize → calculate deterministic metrics → show an import report

Do not begin with a fictional polished dashboard populated by hard-coded scores. The most important unknown is what useful and defensible conclusions can be reliably derived from actual LinkedIn export data.

