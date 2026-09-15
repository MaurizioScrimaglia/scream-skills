# Scream Audit Report Template

This document defines the canonical report structure for `scream-audit`.

The report must be written in English and should be as detailed as the available evidence supports.

The canonical output format is Markdown.

When the execution environment supports document or PDF generation, a professionally formatted PDF may also be produced. The PDF must preserve the same content, depth, findings, evidence, and conclusions as the Markdown report.

The report must never invent findings, evidence, root causes, scores, or conclusions merely to appear comprehensive.

---

# Classification System

## Finding Severity

Use one of the following:

- `CRITICAL`
- `HIGH`
- `MEDIUM`
- `LOW`
- `INFORMATIONAL`

Severity represents the risk posed by the finding.

It should consider likelihood together with relevant forms of impact, including:

- User impact
- Business impact
- Technical impact
- Security impact
- Privacy impact
- Operational impact
- Compliance impact

Severity and remediation priority are separate concepts.

---

## Confidence

Use one of:

- `HIGH`
- `MEDIUM`
- `LOW`

Confidence represents the strength of the evidence supporting the conclusion.

Examples:

- `HIGH`: directly reproduced, observed, measured, or strongly demonstrated by code or configuration.
- `MEDIUM`: supported by substantial evidence but not fully verified.
- `LOW`: plausible concern requiring additional verification.

Confidence must not influence severity directly.

---

## Remediation Priority

Use one of:

- `IMMEDIATE`
- `SHORT-TERM`
- `PLANNED`
- `ADVISORY`

Priority represents how urgently remediation should occur.

### IMMEDIATE

Requires urgent attention because of production risk, severe business impact, significant user impact, or other time-sensitive exposure.

### SHORT-TERM

Should be corrected soon because it represents significant risk, degradation, or accumulated exposure.

### PLANNED

Should be included in normal planning because it materially improves quality, reliability, maintainability, or product health.

### ADVISORY

Best-practice improvement, future opportunity, or non-urgent recommendation.

---

## Area Status

Use one of:

- `STRONG`
- `ACCEPTABLE`
- `NEEDS IMPROVEMENT`
- `MATERIAL GAPS`
- `CRITICAL GAPS`
- `NOT ASSESSED`
- `NOT APPLICABLE`

### NOT ASSESSED

Use when the area is relevant but the available evidence is insufficient.

Always explain why it could not be assessed.

### NOT APPLICABLE

Use only when the area is genuinely irrelevant to the audited application.

Always explain why it does not apply.

---

## Production Readiness

Use one of:

- `READY`
- `READY WITH CONDITIONS`
- `NOT READY`
- `NOT DETERMINED`

Do not assign production readiness when available evidence is insufficient.

Use `NOT DETERMINED` and explain what additional evidence would be required.

---

# Application Audit Report

## 1. Executive Summary

Provide a concise but substantive assessment for executives, engineering leaders, product leaders, founders, or other stakeholders who may not read the entire report.

### Overall Assessment

**Overall Risk Rating:** `<CRITICAL | HIGH | MEDIUM | LOW | INFORMATIONAL>`

**Production Readiness:** `<READY | READY WITH CONDITIONS | NOT READY | NOT DETERMINED>`

**Audit Confidence:** `<HIGH | MEDIUM | LOW>`

### Findings by Severity

| Severity | Count |
|---|---:|
| Critical | `<n>` |
| High | `<n>` |
| Medium | `<n>` |
| Low | `<n>` |
| Informational | `<n>` |

### Executive Assessment

`<Provide an evidence-based assessment of the application's current quality, risk profile, maturity, major weaknesses, major strengths, and readiness. Explain the practical meaning of the audit results.>`

### Key Risks

1. `<Material risk>`
2. `<Material risk>`
3. `<Material risk>`

Include only risks that materially affect the overall assessment.

Do not force a fixed number of risks.

### Key Strengths

1. `<Evidence-backed strength>`
2. `<Evidence-backed strength>`
3. `<Evidence-backed strength>`

Do not include generic praise.

### Recommended Immediate Actions

1. `<Action>`
2. `<Action>`
3. `<Action>`

If no immediate action is required, state this explicitly.

### Major Audit Limitations

`<Summarize limitations that materially affect confidence in the audit conclusions.>`

---

## 2. Audit Scope

### Target

**Application / Product:** `<name>`

**URL:** `<URL if available>`

**Repository:** `<repository if available>`

**Version / Commit:** `<version, branch, tag, or commit if available>`

**Environment:** `<production | staging | development | local | unknown>`

**Audit Date:** `<date>`

### Audit Objective

`<Explain what the audit was intended to evaluate or determine.>`

### Evidence Available

Document the evidence available during the audit.

Examples:

- Running application
- Source repository
- Application documentation
- Architecture documentation
- API specifications
- Automated test suite
- CI/CD configuration
- Infrastructure configuration
- Logs
- Monitoring data
- Error tracking
- Analytics
- Design files
- Database schemas
- Configuration files
- Existing tickets or incident reports
- Other relevant evidence

### Areas Assessed

`<List the areas actually assessed.>`

### Areas Not Assessed

For every relevant area that could not be assessed:

**Area:** `<area>`

**Status:** `NOT ASSESSED`

**Reason:** `<Explain what evidence or access was unavailable.>`

### Areas Not Applicable

For every area genuinely irrelevant to the application:

**Area:** `<area>`

**Status:** `NOT APPLICABLE`

**Reason:** `<Explain why the area does not apply.>`

### Assumptions

List unresolved assumptions that materially influenced the audit.

`<Assumption and rationale>`

### Limitations

Describe relevant limitations such as:

- Access limitations
- Environment limitations
- Missing source code
- Missing infrastructure access
- Authentication limitations
- Missing business context
- Missing analytics
- Tooling limitations
- Time limitations
- Inability to execute specific flows
- Other scope restrictions

---

## 3. Application Overview

Demonstrate an understanding of the application before evaluating it.

### Purpose

`<Explain what the application does and what problem it solves.>`

### Primary Users

`<Describe the main users and usage contexts.>`

### Critical User Journeys

1. `<Journey>`
2. `<Journey>`
3. `<Journey>`

Identify journeys whose failure would materially affect users or the business.

### Main Components

`<Describe relevant frontend, backend, APIs, services, workers, mobile clients, databases, storage systems, queues, or other components when known.>`

### Architecture Summary

`<Summarize the observable or documented architecture. If insufficient evidence exists, state that architecture was not assessed.>`

### External Services and Integrations

`<List material third-party services and integrations.>`

### Relevant Data Flows

`<Describe important data movement when relevant to functionality, privacy, security, reliability, or data integrity.>`

### Business-Critical Flows

`<Identify flows whose failure could materially affect customers, revenue, trust, operations, compliance, or business continuity.>`

---

## 4. Quality Assessment Overview

Provide a concise area-by-area assessment.

Only include areas relevant to the application.

Relevant but unverifiable areas must remain visible as `NOT ASSESSED`.

| Area | Status | Confidence | Summary |
|---|---|---|---|
| Functionality | `<status>` | `<confidence>` | `<summary>` |
| Reliability | `<status>` | `<confidence>` | `<summary>` |
| UX / UI | `<status>` | `<confidence>` | `<summary>` |
| Accessibility | `<status>` | `<confidence>` | `<summary>` |
| Performance | `<status>` | `<confidence>` | `<summary>` |
| Security | `<status>` | `<confidence>` | `<summary>` |
| Privacy | `<status>` | `<confidence>` | `<summary>` |
| Architecture | `<status>` | `<confidence>` | `<summary>` |
| Code Quality | `<status>` | `<confidence>` | `<summary>` |
| Maintainability | `<status>` | `<confidence>` | `<summary>` |
| Testing | `<status>` | `<confidence>` | `<summary>` |
| CI/CD | `<status>` | `<confidence>` | `<summary>` |
| Observability | `<status>` | `<confidence>` | `<summary>` |
| Documentation | `<status>` | `<confidence>` | `<summary>` |
| Developer Experience | `<status>` | `<confidence>` | `<summary>` |
| `<Context-specific area>` | `<status>` | `<confidence>` | `<summary>` |

Do not assign arbitrary numerical quality scores.

A numerical score may only be used when an explicit, defined, and appropriate scoring methodology is part of the audit scope.

---

## 5. Key Strengths

Document meaningful positive findings separately from problems and recommendations.

Do not invent strengths to balance negative findings.

### Strength S-01: `<Title>`

**Area:** `<area>`

**Confidence:** `<HIGH | MEDIUM | LOW>`

#### Observation

`<Explain what is implemented or working particularly well.>`

#### Evidence

`<Provide concrete evidence supporting the assessment.>`

#### Why It Matters

`<Explain the user, business, technical, operational, security, delivery, or maintainability benefit.>`

#### Assessment

`<Explain whether any change is recommended. If no remediation is needed, say so explicitly.>`

Repeat for every meaningful strength.

---

## 6. Findings Summary

List all confirmed or sufficiently supported findings.

| ID | Severity | Remediation Priority | Confidence | Area | Finding |
|---|---|---|---|---|---|
| F-01 | `<severity>` | `<priority>` | `<confidence>` | `<area>` | `<title>` |
| F-02 | `<severity>` | `<priority>` | `<confidence>` | `<area>` | `<title>` |

Order findings primarily by remediation urgency and severity.

Preserve logical grouping where doing so improves readability.

If no material issues were identified, state this explicitly.

Never invent findings to populate this section.

---

## 7. Detailed Findings

Create one complete subsection for every finding.

### Finding F-01: `<Title>`

**Severity:** `<CRITICAL | HIGH | MEDIUM | LOW | INFORMATIONAL>`

**Remediation Priority:** `<IMMEDIATE | SHORT-TERM | PLANNED | ADVISORY>`

**Confidence:** `<HIGH | MEDIUM | LOW>`

**Area:** `<area>`

**Affected Components:** `<components>`

#### Description

`<Explain the issue precisely, including the conditions under which it occurs.>`

#### Evidence

`<Provide concrete supporting evidence. Reference files, URLs, requests, responses, logs, screenshots, tests, commands, traces, configuration, measurements, or observed behavior when available.>`

#### Observed Behavior

`<Describe what actually happens.>`

#### Expected Behavior

`<Describe what should happen instead.>`

Do not invent expected behavior when product intent cannot reasonably be determined.

#### Reproduction

1. `<Step>`
2. `<Step>`
3. `<Step>`

If the finding originates from static analysis and cannot be directly reproduced, state this instead of fabricating reproduction steps.

#### Likelihood

**Rating:** `<HIGH | MEDIUM | LOW>`

**Rationale:** `<Explain why.>`

#### Impact

**Rating:** `<CRITICAL | HIGH | MEDIUM | LOW>`

**Rationale:** `<Explain why.>`

#### User Impact

`<Explain how users are affected. Use NOT APPLICABLE when appropriate.>`

#### Business Impact

`<Explain relevant revenue, conversion, trust, support burden, operational cost, contractual, regulatory, reputation, or other business consequences. Use NOT ASSESSED if business context is insufficient.>`

#### Technical Impact

`<Explain relevant technical, architectural, reliability, maintainability, data, scalability, or operational consequences.>`

#### Security / Privacy Impact

`<Include when relevant. Otherwise omit.>`

#### Root Cause

`<Include only when confirmed by evidence.>`

#### Root Cause Hypothesis

`<Use when the cause is not confirmed. Clearly preserve the uncertainty.>`

Never present a hypothesis as a confirmed root cause.

#### Risk if Left Unresolved

`<Explain the likely or plausible consequences of taking no action.>`

#### Recommendation

`<Provide a concrete remediation approach appropriate to the available evidence. Avoid generic advice.>`

#### Suggested Validation

`<Explain how to verify that remediation is successful and that relevant regressions were not introduced.>`

#### Dependencies / Blockers

`<List known remediation dependencies, sequencing constraints, external dependencies, or blockers.>`

#### References

`<Reference relevant source files, standards, documentation, URLs, tickets, specifications, or other traceable evidence.>`

Repeat for every finding.

---

## 8. Functionality and Reliability Assessment

**Status:** `<area status>`

**Confidence:** `<confidence>`

### What Was Assessed

Consider relevant areas such as:

- Main user journeys
- Core functionality
- Validation
- Error handling
- State transitions
- Edge cases
- Failure scenarios
- Recovery behavior
- Data consistency
- Reliability
- Resilience
- Broken flows

### What Works Well

`<Evidence-backed strengths.>`

### Issues Identified

`<Reference related finding IDs and explain patterns when relevant.>`

### Risks

`<Material functional or reliability risks.>`

### Recommendations

`<Area-level recommendations not already sufficiently covered by individual findings.>`

### What Could Not Be Assessed

`<Explicitly identify gaps in evidence or coverage.>`

---

## 9. UX and UI Assessment

**Status:** `<area status>`

**Confidence:** `<confidence>`

### What Was Assessed

Consider relevant topics such as:

- Usability
- Navigation
- Interaction clarity
- Visual consistency
- User feedback
- Error states
- Empty states
- Loading states
- Forms
- Content clarity
- Responsive behavior
- Mobile experience
- User friction
- State transitions

### What Works Well

`<Evidence-backed strengths.>`

### Issues Identified

`<Relevant findings and patterns.>`

### Risks

`<Material UX or UI risks.>`

### Recommendations

`<Area-level recommendations.>`

### What Could Not Be Assessed

`<Coverage limitations.>`

---

## 10. Accessibility Assessment

**Status:** `<area status>`

**Confidence:** `<confidence>`

### What Was Assessed

Consider relevant topics such as:

- Keyboard navigation
- Semantic structure
- Focus management
- Form labels
- Screen-reader behavior
- Alternative text
- Color contrast
- Motion
- Interaction accessibility
- Error accessibility
- Relevant accessibility standards

### What Works Well

`<Evidence-backed strengths.>`

### Issues Identified

`<Relevant findings.>`

### Risks

`<Accessibility risks and potential user impact.>`

### Recommendations

`<Area-level recommendations.>`

### What Could Not Be Assessed

`<Coverage limitations.>`

---

## 11. Performance Assessment

**Status:** `<area status>`

**Confidence:** `<confidence>`

### What Was Assessed

Consider relevant topics such as:

- Initial loading
- Rendering
- User-perceived latency
- Network usage
- Asset size
- Caching
- API latency
- Database behavior
- Runtime efficiency
- Resource consumption
- Performance bottlenecks
- Performance under failure conditions

### What Works Well

`<Evidence-backed strengths.>`

### Issues Identified

`<Relevant findings.>`

### Risks

`<Performance risks.>`

### Recommendations

`<Area-level recommendations.>`

### What Could Not Be Assessed

`<Coverage limitations.>`

---

## 12. Security and Privacy Assessment

**Status:** `<area status>`

**Confidence:** `<confidence>`

Assess only what available evidence supports.

### What Was Assessed

Possible areas include:

- Authentication
- Authorization
- Session management
- Input validation
- Data exposure
- Client-side exposure
- Secret management
- Dependency risks
- Transport security
- Sensitive data handling
- Privacy controls
- Common vulnerability patterns
- Access boundaries
- Data retention when observable

### What Works Well

`<Evidence-backed strengths.>`

### Issues Identified

`<Relevant findings.>`

### Risks

`<Security or privacy risks.>`

### Recommendations

`<Area-level recommendations.>`

### What Could Not Be Assessed

`<Explicit limitations.>`

Do not imply that this audit replaces a dedicated penetration test, formal security assessment, or compliance audit unless those activities are explicitly within scope.

---

## 13. Architecture Assessment

**Status:** `<area status>`

**Confidence:** `<confidence>`

### What Was Assessed

Consider relevant topics such as:

- Component boundaries
- Separation of concerns
- Coupling
- Cohesion
- Scalability
- Extensibility
- Failure isolation
- Dependency management
- Architectural consistency
- Data flow
- Service boundaries
- Technical debt
- Architectural complexity

### What Works Well

`<Evidence-backed strengths.>`

### Issues Identified

`<Relevant findings.>`

### Risks

`<Architectural risks.>`

### Recommendations

`<Area-level recommendations.>`

### What Could Not Be Assessed

`<Coverage limitations.>`

---

## 14. Code Quality and Maintainability Assessment

**Status:** `<area status>`

**Confidence:** `<confidence>`

### What Was Assessed

Consider relevant topics such as:

- Readability
- Complexity
- Duplication
- Modularity
- Naming
- Error handling
- Configuration management
- Dependency hygiene
- Dead code
- Consistency
- Change risk
- Maintainability
- Technical debt
- Code ownership clarity

### What Works Well

`<Evidence-backed strengths.>`

### Issues Identified

`<Relevant findings.>`

### Risks

`<Maintainability risks.>`

### Recommendations

`<Area-level recommendations.>`

### What Could Not Be Assessed

`<Coverage limitations.>`

---

## 15. Testing Strategy Assessment

**Status:** `<area status>`

**Confidence:** `<confidence>`

### What Was Assessed

Consider relevant topics such as:

- Unit tests
- Integration tests
- End-to-end tests
- Contract tests
- Critical-flow coverage
- Regression protection
- Test reliability
- Test architecture
- Test data strategy
- Negative scenarios
- Edge cases
- CI integration
- Flaky tests
- Signal quality
- Maintainability of tests

Do not treat a raw coverage percentage as sufficient evidence of test quality.

### What Works Well

`<Evidence-backed strengths.>`

### Issues Identified

`<Relevant findings.>`

### Risks

`<Testing and regression risks.>`

### Recommendations

`<Area-level recommendations.>`

### What Could Not Be Assessed

`<Coverage limitations.>`

---

## 16. CI/CD and Delivery Assessment

**Status:** `<area status>`

**Confidence:** `<confidence>`

### What Was Assessed

Consider relevant topics such as:

- Build pipeline
- Automated checks
- Quality gates
- Deployment process
- Release controls
- Environment consistency
- Rollback capability
- Change safety
- Deployment automation
- Branch strategy where relevant
- Release traceability
- Failure handling

### What Works Well

`<Evidence-backed strengths.>`

### Issues Identified

`<Relevant findings.>`

### Risks

`<Delivery risks.>`

### Recommendations

`<Area-level recommendations.>`

### What Could Not Be Assessed

`<Coverage limitations.>`

---

## 17. Observability and Operations Assessment

**Status:** `<area status>`

**Confidence:** `<confidence>`

### What Was Assessed

Consider relevant topics such as:

- Logging
- Monitoring
- Error tracking
- Metrics
- Tracing
- Alerting
- Incident detection
- Operational visibility
- Troubleshooting capability
- Auditability
- Health checks
- Operational runbooks

### What Works Well

`<Evidence-backed strengths.>`

### Issues Identified

`<Relevant findings.>`

### Risks

`<Operational risks.>`

### Recommendations

`<Area-level recommendations.>`

### What Could Not Be Assessed

`<Coverage limitations.>`

---

## 18. Documentation and Developer Experience Assessment

**Status:** `<area status>`

**Confidence:** `<confidence>`

### What Was Assessed

Consider relevant topics such as:

- README quality
- Setup instructions
- Architecture documentation
- API documentation
- Operational documentation
- Local development
- Developer onboarding
- Development ergonomics
- Environment setup
- Maintenance guidance
- Troubleshooting documentation

### What Works Well

`<Evidence-backed strengths.>`

### Issues Identified

`<Relevant findings.>`

### Risks

`<Documentation or developer-experience risks.>`

### Recommendations

`<Area-level recommendations.>`

### What Could Not Be Assessed

`<Coverage limitations.>`

---

## 19. Context-Specific Assessments

Add additional assessment sections only when materially relevant to the audited application.

Possible areas include:

- SEO
- Analytics and tracking
- Payments
- Internationalization
- Localization
- Browser compatibility
- Mobile compatibility
- Third-party integrations
- Data integrity
- Backward compatibility
- Compliance
- Resilience
- Migration safety
- API design
- Data quality
- Search
- Authentication-specific flows
- E-commerce flows
- Content management

For every contextual area use:

**Status:** `<area status>`

**Confidence:** `<confidence>`

### What Was Assessed

`<scope>`

### What Works Well

`<strengths>`

### Issues Identified

`<findings>`

### Risks

`<risks>`

### Recommendations

`<recommendations>`

### What Could Not Be Assessed

`<limitations>`

---

## 20. Risk Register

Summarize application-level risks.

A risk may aggregate multiple findings and should not simply duplicate the findings table.

| Risk | Likelihood | Impact | Rating | Related Findings | Mitigation |
|---|---|---|---|---|---|
| `<risk>` | `<HIGH | MEDIUM | LOW>` | `<CRITICAL | HIGH | MEDIUM | LOW>` | `<rating>` | `<IDs>` | `<mitigation>` |

Explain significant systemic risks below the table when additional context is necessary.

---

## 21. Remediation Roadmap

Organize remediation according to urgency, dependencies, root causes, and logical execution order.

Do not simply repeat the findings list.

### Immediate

**Objective:** Remove business-critical, production-blocking, or otherwise urgent risks.

| Order | Finding / Action | Rationale | Dependencies |
|---:|---|---|---|
| 1 | `<action>` | `<why now>` | `<dependency>` |

If no immediate actions exist, state this explicitly.

### Short-Term

**Objective:** Address significant risks that should be corrected soon but do not require immediate intervention.

`<Prioritized actions>`

### Planned

**Objective:** Improve quality, reliability, maintainability, product health, or operational maturity within the normal planning horizon.

`<Prioritized actions>`

### Advisory

**Objective:** Capture best-practice improvements, future opportunities, and non-urgent enhancements.

`<Prioritized actions>`

### Execution Notes

Include when relevant:

- Shared root causes
- Recommended sequencing
- Dependencies
- Potential conflicts between remediations
- Opportunities to solve multiple findings through one intervention
- Areas requiring further investigation before remediation

---

## 22. Quick Wins

Identify improvements with relatively low implementation effort and meaningful expected value.

| Improvement | Expected Benefit | Estimated Effort | Related Findings |
|---|---|---|---|
| `<improvement>` | `<benefit>` | `<LOW | MEDIUM | HIGH | UNKNOWN>` | `<IDs>` |

Do not invent effort estimates.

Use `UNKNOWN` when available evidence is insufficient.

---

## 23. Strategic Improvements

Capture larger opportunities that are not immediate defects but could materially improve the application over the medium or long term.

### `<Strategic Improvement>`

**Problem / Opportunity:** `<description>`

**Expected Benefit:** `<benefit>`

**Rationale:** `<why it matters>`

**Dependencies:** `<dependencies if known>`

**Suggested Horizon:** `<when it would make sense to address>`

Strategic improvements must remain clearly separated from confirmed defects.

---

## 24. Final Assessment

### Overall Risk Rating

`<Rating and rationale.>`

### Production Readiness

`<Status and rationale, or explain why readiness could not be determined.>`

### Primary Blockers

`<List genuine blockers. If none exist, state this explicitly.>`

### Conditions for Readiness

`<Explain what must change or be demonstrated for the application to be considered ready, when applicable.>`

### Key Strengths

`<Summarize the strongest evidence-backed aspects of the application.>`

### Residual Risks

`<Describe risks that remain after recommended remediation or require further assessment.>`

### Recommended Next Step

`<State the most useful next action following the audit.>`

---

## 25. Appendix

### Evidence Collected

`<List material evidence used during the audit.>`

### Repositories Inspected

`<Repositories, branches, tags, or commits inspected.>`

### Files Inspected

`<Important files and directories reviewed.>`

### URLs / Screens Inspected

`<Pages, routes, screens, or endpoints reviewed.>`

### User Journeys Executed

`<Journeys exercised during the audit.>`

### Tests Executed

`<Automated or manual tests executed.>`

### Commands Executed

`<Relevant commands used during analysis.>`

### Documentation Reviewed

`<Documentation sources reviewed.>`

### Tools Used

`<Tools materially used during the audit.>`

### Unverified Assumptions

`<Assumptions that remain unresolved.>`

### Detailed Limitations

`<Anything that could materially affect interpretation, completeness, confidence, or reproducibility of the audit.>`

---

# Reporting Principles

Every Scream Audit report must follow these principles:

1. Evidence takes precedence over speculation.
2. Never invent problems to make the audit appear comprehensive.
3. Never omit relevant evidence or analysis merely to keep the report short.
4. A short audit containing a few well-supported findings is better than a long audit containing speculative findings.
5. Positive findings must be specific and supported by evidence.
6. Clearly distinguish confirmed findings from risks, strengths, assumptions, improvement opportunities, and areas that could not be assessed.
7. Clearly distinguish confirmed root causes from root-cause hypotheses.
8. Do not assign arbitrary numerical quality scores.
9. Do not treat severity and remediation priority as interchangeable.
10. State uncertainty explicitly.
11. Preserve traceability between conclusions and evidence whenever possible.
12. Do not claim that an area was assessed when sufficient evidence was unavailable.
13. Do not infer production readiness from incomplete evidence.
14. The depth of the report should scale with the complexity of the application and the quality of available evidence.
15. Do not recommend changing something that is already strong without a clear reason.
16. Prefer concrete, actionable recommendations over generic best practices.
17. When evidence contradicts an initial assumption, evidence wins.
18. When additional context would materially change the assessment, identify the missing context explicitly.
19. Findings must describe actual or sufficiently supported problems. Strategic opportunities must remain separate.
20. The report should be detailed enough to support both decision-making and remediation work.
