# Issue Discovery Investigation Template

This document defines the output contract for scream-issue-discovery.

Return Markdown in the conversation.
Do not create a file automatically.

Write the investigation report in the user's language.
Write comment drafts and the confirmed-problem handoff in English.
Keep classification labels unchanged.

Replace placeholders with supported information.
Use UNKNOWN for relevant information that remains unknown.
Do not invent values to complete a section.

Omit irrelevant optional sections.
Keep relevant activities that were not performed visible, with reasons.

## 1. Problem Report and Decision

- Problem Report: <verified title>
- Task GID: <user-provided and checked GID>
- Reference: <verified reference, or unavailable>
- Outcome: <CONFIRMED | NOT CONFIRMED | CLARIFICATION REQUIRED | DUPLICATE | UNABLE TO CONFIRM>
- Confidence: <HIGH | MEDIUM | LOW>
- Evidence assessment: <classification from SKILL.md>
- Reproduction result: <REPRODUCED | NOT REPRODUCED | NOT ATTEMPTED | BLOCKED | INCONCLUSIVE>

### Decision Rationale

<Explain the conclusion with evidence references and its scope.>

### Problem Summary

<Describe the problem without adding unverified information.>

## 2. Behavior and Context

### Reported Behavior

<What the reporter states. Identify the source.>

### Verified Actual Behavior

<What the investigation established, or UNKNOWN.>

### Expected Behavior

<Supported expectation, or UNKNOWN.>

Source: <specification, requirement, documentation, user-provided rule, or verified invariant>

### Reproduction Steps

- Reported steps: <steps from the report, or UNKNOWN>
- Verified steps: <steps actually executed, or none>

### Environment and Version

- Reported environment/version: <verified report context, or UNKNOWN>
- Investigated environment/version: <actual investigation context, or UNKNOWN>
- Material differences: <differences and their implications>

### Affected Area

<Supported product area, service, flow, or component.>

### Impact and Frequency

- Reported impact/frequency: <reporter statements, or UNKNOWN>
- Confirmed impact/frequency: <supported observations, or UNKNOWN>

Do not convert reported counts into confirmed counts.

## 3. Duplicate Analysis

- Selected projects: <verified project references>
- Search coverage: <not performed | partial | performed within selected scope>
- Queries and filters: <material search details>
- Overall classification: <duplicate classification from SKILL.md>
- Limitations: <scope, unavailable search, inaccessible candidates, or other limits>

| Candidate | Classification | Supporting evidence | Differences or unknowns |
|---|---|---|---|
| <verified task reference> | <classification> | <evidence IDs> | <material differences> |

Include only meaningful candidates.
If none were found, state the selected scope and search limitations.
Do not claim that no duplicate exists outside the search.

## 4. Evidence

| ID | Source | Observation | Claim supported or contradicted | Limits |
|---|---|---|---|---|
| E-01 | <verified source> | <relevant observation> | <claim> | <limits> |

Include material supporting and contrary evidence.
Do not reproduce unnecessary sensitive data.

### Code Evidence

- Confirmed repository: <verified repository, or not inspected>
- Inspected reference: <branch, commit, or version, or UNKNOWN>
- Relevant locations: <verified paths and code locations>
- Demonstrated behavior: <code-path explanation with evidence IDs>
- Unverified prerequisites: <remaining gaps, or none>

### Observability Evidence

- Source: <available platform or evidence source>
- Service/environment/time range: <verified scope>
- Relevant findings: <evidence IDs and observations>
- Correlation with the report: <supported relationship or unresolved gap>

If relevant access was unavailable, state that explicitly.

## 5. Reproduction

For each executed attempt:

### Attempt <number>

- Approved scenario: <specific scenario>
- Target/environment/version: <verified context>
- Prerequisites and test data: <safe, relevant details>
- Steps executed: <actual steps>
- Commands or requests: <relevant details without secrets>
- Result: <REPRODUCED | NOT REPRODUCED | INCONCLUSIVE>
- Observation: <actual output or behavior>
- Evidence: <evidence IDs>
- Limitations: <material differences or constraints>

If no attempt occurred, use NOT ATTEMPTED or BLOCKED.
Explain the reason.
Do not present a proposed scenario as an executed attempt.

## 6. Missing Information and Limitations

| Missing information | Why needed | Discovery result | Blocked work | Required question |
|---|---|---|---|---|
| <gap> | <reason> | <result or ambiguity> | <dependent work> | <minimum question> |

Also identify:

- unavailable capabilities
- inaccessible evidence
- version or environment mismatches
- safety restrictions
- search and investigation boundaries
- material unresolved contradictions

## 7. Cause Analysis

### Confirmed Root Cause

<Include only a cause established by evidence, with evidence IDs.>

### Root-Cause Hypotheses

<Optional hypotheses, their supporting evidence, and missing verification.>

Do not present a hypothesis as a confirmed cause.
A confirmed problem can have an unknown root cause.

## 8. Recommended Next Step

<Give the smallest useful next step supported by the outcome.>

For CONFIRMED, recommend a separate bug-creation workflow.
Highlight a likely existing bug before suggesting a new task.
Do not select bug-creation routing or identifiers.

For DUPLICATE, reference the verified candidate.
Do not close, link, or modify tasks.

For blocked or inconclusive outcomes, identify what would permit further investigation.

## 9. Optional Comment Draft

Write the draft in English.
Do not include placeholders in a draft proposed for publication.

- Purpose: <follow-up | confirmation>
- Target: <verified Problem Report title and task GID>
- Publication status: <draft, not published | published with approval | failed | uncertain>

### Complete Comment

<Full proposed comment.>

### Publication Approval

Ask the user to approve both the complete content and publication on the identified target.
Do not interpret approval of the report as approval to publish.

## 10. Confirmed-Problem Handoff

Include this section if and only if the outcome is CONFIRMED.
Write it in English.
It is an output, not an instruction to create a task.

### Suggested Bug Description

#### Source Problem Report

<Verified title, task GID, and reference when available.>

#### Confirmed Problem

<Precisely describe the established behavior and triggering conditions.>

#### Expected Behavior

<Supported expected behavior and its source.>

#### Confirmation Method

<Direct reproduction or deterministic technical evidence, with evidence IDs.>

#### Verified Reproduction Steps

<Only steps actually verified.>

If no runtime reproduction occurred, state:
"No runtime reproduction was performed. Confirmation relies on technical evidence."

If attempts were inconclusive or negative, state their actual results instead.
Do not manufacture a successful reproduction.

#### Environment and Affected Area

<Verified environment, version, flow, service, or component.>
<Mark relevant unknowns explicitly.>

#### Evidence and Technical Findings

<Supported observations and verified references.>

#### Confirmed Impact

<Supported impact, or UNKNOWN.>

#### Confirmed Root Cause

<Established cause, or UNKNOWN.>
<Do not transfer hypotheses as confirmed causes.>

#### Duplicate Analysis

<Verified candidates, classifications, differences, and search scope.>

#### Unresolved Unknowns

<Remaining unknowns and their implications.>

Do not include project GIDs, section GIDs, custom-field configuration, assignments, or other bug-creation routing.
