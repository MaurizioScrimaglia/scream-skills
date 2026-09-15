---
name: scream-audit
description: Perform a comprehensive, evidence-based audit of a software application, website, service, or repository. Adapt the audit to the available evidence, identify real quality and risk issues, recognize strengths, prioritize remediation, and produce a detailed professional report in English. Use when asked to audit, assess, review, evaluate, inspect, or determine the quality, health, risks, or production readiness of a software product.
---

# Scream Audit

Perform a comprehensive, evidence-based audit of a software application.

The audited target may be:

- a running website or web application
- a software repository
- an API or backend service
- a mobile or desktop application
- a combination of source code and a running application
- supporting documentation, infrastructure, CI/CD, tests, analytics, or observability data

The audit must adapt to the target and to the evidence actually available.

The objective is not to produce the longest possible list of issues.

The objective is to produce the most accurate, useful, and defensible assessment supported by the available evidence.

## Core Principles

1. Evidence takes precedence over speculation.
2. Never invent findings to make the audit appear comprehensive.
3. Never invent reproduction steps, expected behavior, root causes, business impact, or technical details.
4. Explicitly distinguish facts, observations, assumptions, hypotheses, risks, and recommendations.
5. Recognize strong implementation where evidence supports it.
6. Do not recommend changing something that is already strong without a clear reason.
7. An area that cannot be verified must be marked `NOT ASSESSED`.
8. An area that genuinely does not apply must be marked `NOT APPLICABLE`.
9. A short audit with a few well-supported findings is better than a long audit containing speculative findings.
10. Do not sacrifice relevant evidence or useful analysis merely to keep the report short.
11. The depth of the audit must scale with the complexity of the application and the quality of the available evidence.
12. Use `references/report-template.md` as the canonical reporting contract.

## Step 1: Understand the Target

Before beginning the audit, determine what is being audited.

Identify, where possible:

- application or product purpose
- primary users
- business-critical flows
- environment
- application type
- available source code
- available running application
- APIs
- architecture
- automated tests
- delivery pipelines
- infrastructure
- documentation
- analytics
- observability
- known constraints

Infer this information from available evidence whenever possible.

Do not ask the user questions that can be answered by inspecting the available application, repository, documentation, or other provided context.

## Step 2: Resolve Material Context Gaps

Ask the user focused questions only when missing information would materially affect:

- audit scope
- interpretation of observed behavior
- severity
- remediation priority
- production readiness
- safety of the audit
- ability to exercise critical flows

Typical material questions may include:

- Is this production, staging, development, or another environment?
- Who are the primary users?
- Which flows are considered business-critical?
- Is production readiness part of the assessment?
- Are any areas intentionally out of scope?
- Are test accounts or credentials available?
- Are there known constraints that affect expected behavior?
- Is active or potentially destructive testing explicitly authorized?

Ask only the minimum number of questions necessary.

Do not turn the beginning of the audit into a questionnaire.

If a question is useful but not required to continue, proceed with the audit and document the unresolved assumption.

If the missing context makes a meaningful assessment impossible or an action unsafe, stop that portion of the audit and explain what is required.

## Step 3: Determine Available Evidence

Build an internal inventory of the evidence available.

Possible evidence includes:

- live application behavior
- source code
- repository structure
- commit or version information
- configuration
- automated tests
- CI/CD pipelines
- API specifications
- network behavior
- application logs
- monitoring
- error tracking
- analytics
- architecture documentation
- product documentation
- database schemas
- infrastructure configuration
- design files
- tickets or incident reports
- user-provided business context

Never imply access to evidence that is not actually available.

## Step 4: Define the Audit Surface

Select audit areas according to the application type and available evidence.

### Core Areas

Assess when relevant and evidence permits:

- Functionality
- Reliability
- UX / UI
- Accessibility
- Performance

### Evidence-Dependent Areas

Assess only when sufficient evidence is available:

- Security
- Privacy
- Architecture
- Code Quality
- Maintainability
- Testing Strategy
- CI/CD and Delivery
- Observability and Operations
- Documentation
- Developer Experience

### Context-Specific Areas

Add when materially relevant:

- SEO
- Analytics and Tracking
- Payments
- Internationalization
- Localization
- Browser Compatibility
- Mobile Compatibility
- Third-Party Integrations
- Data Integrity
- Backward Compatibility
- Compliance
- Resilience
- Migration Safety
- API Design
- Data Quality
- Search
- Authentication Flows
- E-commerce Flows
- Content Management

This list is not exhaustive.

Add another audit area when the application context clearly requires it.

Do not create irrelevant sections merely because they exist in the report template.

## Step 5: Build an Application Model

Before judging the application, understand it.

Identify where possible:

- purpose
- major capabilities
- critical user journeys
- major components
- external dependencies
- integrations
- relevant data flows
- failure boundaries
- business-critical paths
- architecture
- delivery model

Use this model to determine where failures would matter most.

Do not evaluate isolated implementation details without considering their role in the wider system.

## Step 6: Perform the Audit

Use the tools available in the current environment to inspect the target.

The skill must remain tool-agnostic.

Do not assume that any particular browser, shell, repository connector, testing framework, agent, MCP server, or vendor-specific tool exists.

Prefer direct evidence whenever possible.

Examples:

- reproduce behavior instead of inferring it
- inspect implementation instead of guessing architecture
- inspect tests instead of assuming coverage
- inspect pipeline configuration instead of assuming delivery controls
- measure observable performance instead of relying on subjective impressions
- trace relevant code paths when possible
- compare documentation against actual behavior
- validate important error and edge conditions

When access permits, analyze interactions between areas rather than treating each area independently.

For example:

- a UI issue may originate in backend state handling
- a reliability issue may expose insufficient observability
- a testing gap may increase delivery risk
- an architectural decision may create recurring performance problems
- several findings may share one root cause

## Step 7: Exercise Critical Flows

Prioritize flows according to user and business importance.

For each critical flow, assess where relevant:

- happy path
- validation
- error behavior
- edge cases
- state transitions
- recovery behavior
- consistency
- responsiveness
- accessibility
- performance
- data integrity
- integration behavior

Do not perform destructive, irreversible, exploitative, or production-impacting actions unless the user has explicitly authorized them and the environment permits them safely.

Security assessment within a general Scream Audit should remain non-destructive by default.

Do not claim that a general Scream Audit replaces a dedicated penetration test, compliance audit, or formal security engagement.

## Step 8: Maintain Evidence Traceability

Every significant conclusion should be traceable to evidence whenever possible.

Evidence may include:

- file paths
- code locations
- URLs
- screens
- requests and responses
- console behavior
- logs
- test results
- commands
- configuration
- documentation
- measurements
- reproducible observations

Maintain enough detail during the audit to populate the Appendix and Detailed Findings sections of the report.

Do not overload the final report with irrelevant raw data.

## Step 9: Identify Strengths

Explicitly identify implementation that is notably strong.

A strength must be:

- specific
- supported by evidence
- relevant to application quality or risk
- useful to preserve

Do not add generic praise.

A strong area may legitimately require no remediation.

Say so explicitly.

## Step 10: Identify Findings

Create a finding only when evidence supports an actual problem, material weakness, or sufficiently supported risk.

Do not turn every possible improvement into a finding.

Keep separate:

- confirmed findings
- application-level risks
- strengths
- strategic improvements
- assumptions
- areas not assessed
- areas not applicable

Each finding should explain not only what is wrong, but why it matters.

## Step 11: Classify Findings

Use the classification system defined in `references/report-template.md`.

For each finding determine:

- Severity
- Confidence
- Remediation Priority
- Likelihood
- Impact

Severity and remediation priority are independent.

Do not mechanically map:

- Critical to Immediate
- High to Short-Term
- Medium to Planned
- Low to Advisory

Use application and business context.

When business context is unavailable, state this limitation instead of fabricating business impact.

## Step 12: Analyze Root Cause Carefully

Only use `Root Cause` when the available evidence confirms the cause.

Otherwise use:

`Root Cause Hypothesis`

A hypothesis must remain explicitly uncertain.

When multiple findings appear to share a cause, investigate the relationship before recommending separate remediations.

Prefer remediation of underlying causes over repeated treatment of symptoms when evidence supports that conclusion.

## Step 13: Determine Area Assessments

For each relevant audit area, assign one of the statuses defined in the report template:

- `STRONG`
- `ACCEPTABLE`
- `NEEDS IMPROVEMENT`
- `MATERIAL GAPS`
- `CRITICAL GAPS`
- `NOT ASSESSED`
- `NOT APPLICABLE`

Area status must reflect the evidence collected across that area.

Do not infer an area status from a single minor finding.

Do not hide severe issues behind an average assessment.

## Step 14: Assess Overall Risk and Readiness

Determine the overall risk rating using the full audit context.

Consider:

- severity of findings
- likelihood
- user impact
- business impact
- systemic risks
- critical-flow reliability
- security and privacy exposure
- operational maturity
- unresolved uncertainty
- evidence quality

Determine production readiness only when sufficient evidence exists.

Use:

- `READY`
- `READY WITH CONDITIONS`
- `NOT READY`
- `NOT DETERMINED`

Do not infer production readiness merely because no critical findings were discovered.

Absence of evidence is not evidence of readiness.

## Step 15: Build the Remediation Strategy

Do not produce a flat backlog of issues.

Create a remediation roadmap that considers:

- urgency
- severity
- shared root causes
- dependencies
- execution order
- business impact
- remediation risk
- opportunities to resolve multiple findings together

Separate:

- Immediate remediation
- Short-term remediation
- Planned work
- Advisory recommendations
- Quick wins
- Strategic improvements

Do not invent implementation effort.

If effort cannot reasonably be estimated, use `UNKNOWN`.

## Step 16: Produce the Report

Produce the final audit in English.

Follow `references/report-template.md`.

The canonical output is Markdown.

The report should be detailed enough to support:

- executive decision-making
- engineering remediation
- product prioritization
- risk discussion
- follow-up verification

The report does not need to include empty sections that are irrelevant to the target.

Relevant areas that could not be assessed must remain visible and explain why.

## Step 17: Produce Additional Formats When Supported

If the current environment supports document or PDF creation, also produce a professionally formatted PDF when appropriate.

The Markdown report remains the canonical content source.

The PDF must not:

- simplify the findings
- omit evidence
- change classifications
- reduce analysis depth
- introduce conclusions absent from the Markdown report

If PDF generation is unavailable, return the Markdown report without treating this as an audit limitation.

## Step 18: Final Quality Check

Before delivering the report, verify:

- every finding is supported by evidence
- no finding exists only to make the report longer
- severity and priority are independently justified
- uncertainty is explicitly stated
- confirmed root causes and hypotheses are not mixed
- strengths are evidence-backed
- relevant unassessed areas are visible
- irrelevant areas are not artificially included
- recommendations are actionable
- findings and recommendations are traceable
- production readiness is justified by sufficient evidence
- the report follows the canonical template
- the report is internally consistent
- the executive summary accurately reflects the detailed findings

If the detailed evidence contradicts the executive summary, correct the executive summary.

Evidence always wins.
