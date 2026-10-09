# Scream Skills Agent Guide

This repository contains reusable, tool-agnostic AI agent skills.

The goal is to build a public collection of high-quality skills that solve repeatable problems and can be reused across compatible agents, models, and environments.

Repository:

```text
https://github.com/MaurizioScrimaglia/scream-skills
```

## Primary Objective

Build useful, rigorous, portable, maintainable agent skills.

Optimize for:

- usefulness
- clarity
- portability
- real-world applicability
- evidence-based behavior
- maintainability
- predictable outputs
- actual validation

Do not optimize for the number of skills.

A small collection of strong skills is preferable to a large collection of shallow prompts.

## Reference Implementation

The first validated skill is:

```text
skills/quality/scream-audit/
```

Current structure:

```text
skills/quality/scream-audit/
├── SKILL.md
└── references/
    └── report-template.md
```

`scream-audit` is the reference implementation for the repository's design philosophy.

It has been successfully:

- discovered with `npx skills`
- installed into `.agents/skills`
- recognized by Codex
- executed against a real project
- validated using supporting reference files
- used to produce structured output

Use it as a reference for design quality and workflow.

Do not blindly copy audit-specific logic into unrelated skills.

## Repository Structure

The repository follows this general model:

```text
scream-skills/
├── AGENTS.md
├── README.md
├── LICENSE
└── skills/
    └── <category>/
        └── <skill-name>/
            ├── SKILL.md
            └── references/
                └── optional-supporting-files.md
```

Not every skill needs `references/`.

Start with the smallest structure that fully supports the skill.

A minimal skill may contain only:

```text
<skill-name>/
└── SKILL.md
```

Add other directories only when justified.

Possible supporting directories may include:

```text
references/
scripts/
assets/
```

Do not create infrastructure for hypothetical future needs.

## Categories

Categories are created only when needed.

Current category:

```text
quality
```

When adding a new skill:

1. Check whether it fits an existing category.
2. Reuse an existing category when it accurately represents the skill.
3. Create a new category only when existing categories would be misleading.

Do not pre-create categories for symmetry or future ideas.

## Skill Naming

Skill directory names should be:

- lowercase
- kebab-case
- descriptive
- reasonably short

Prefer the `scream-` prefix when it creates a recognizable family and avoids naming collisions.

Example:

```text
scream-audit
```

Do not force the prefix when it makes the name unnatural or misleading.

## What Qualifies as a Skill

A skill should solve a repeatable problem.

A skill should normally define:

- purpose
- invocation intent
- inputs
- context discovery
- reasoning workflow
- decision logic
- evidence requirements
- uncertainty handling
- constraints
- output expectations
- validation criteria

A skill should not exist merely because a long prompt can be written for something.

Before creating a new skill, ask:

- Is the problem repeatable?
- Would multiple users or projects benefit from it?
- Does it require structured reasoning or workflow?
- Does it benefit from reusable constraints or output contracts?
- Is a skill materially better than a normal prompt?

Challenge ideas that are too narrow, redundant, or better solved without a skill.

## Tool-Agnostic Design

Core behavior should remain independent from specific vendors and tools whenever possible.

Avoid unnecessary dependencies on:

- ChatGPT
- Claude
- Codex
- OpenCode
- Cursor
- GitHub Copilot
- Gemini
- MCP
- a specific browser
- a specific CLI
- a specific connector
- a specific model

A skill may use tools available in its execution environment.

Describe capabilities rather than vendor-specific commands whenever possible.

Prefer:

```text
Inspect the available repository contents.
```

over:

```text
Use GitHub MCP tool X.
```

A vendor-specific dependency is acceptable only when it is intrinsic to the skill.

## SKILL.md

Every skill must contain:

```text
SKILL.md
```

Use YAML frontmatter compatible with the Agent Skills convention.

Minimum expected frontmatter:

```yaml
---
name: skill-name
description: Clear description of what the skill does and when it should be used.
---
```

The `description` is important because compatible agents may use it for discovery and invocation.

The body of `SKILL.md` should define operational behavior for the agent.

It should not become general documentation for humans unless that information helps the agent perform the task.

## Skill Design Principles

### Evidence over speculation

Prefer observable facts and available evidence.

Do not invent information to make an output appear comprehensive.

### Explicit uncertainty

Clearly distinguish where relevant:

- facts
- observations
- assumptions
- hypotheses
- risks
- recommendations
- unknown information
- unavailable evidence

### Minimal assumptions

Infer information when the available evidence is sufficient.

Ask questions only when missing context materially changes the result.

Do not ask questions whose answers can reasonably be discovered.

### Reusable by design

Avoid hardcoding:

- project names
- company names
- user names
- internal systems
- local paths
- private business rules

unless they are clearly examples.

### Predictable output

When consistency matters, define an explicit output contract.

If the output specification becomes substantial, place it under:

```text
references/
```

### Proportional complexity

Do not create unnecessary:

- files
- abstractions
- frameworks
- scripts
- categories
- dependencies
- configuration

### No fake completeness

A shorter, well-supported result is preferable to a large speculative result.

### Preserve strengths

Evaluation-oriented skills should identify strengths as well as weaknesses.

Do not manufacture recommendations when no change is needed.

## New Skill Workflow

When a new skill idea is proposed, do not immediately create files.

Follow this process.

### Phase 1: Define the Problem

Establish:

- what problem the skill solves
- who benefits from it
- expected inputs
- expected outputs
- when it should be used
- when it should not be used
- why it deserves to be a reusable skill

Challenge the idea when necessary.

Do not automatically agree that every idea should become a skill.

### Phase 2: Design the Behavior

Define:

- workflow
- reasoning stages
- context gathering
- evidence model
- decision points
- uncertainty handling
- when user questions are required
- constraints
- safety boundaries where relevant
- failure behavior
- output contract

Keep the behavior tool-agnostic unless a dependency is necessary.

### Phase 3: Choose Repository Placement

Determine the appropriate category.

Use:

```text
skills/<category>/<skill-name>/
```

Reuse an existing category when appropriate.

Create a new category only when necessary.

### Phase 4: Choose File Structure

Start with:

```text
<skill-name>/
└── SKILL.md
```

Add `references/` only when useful.

Add scripts or assets only when they provide a real functional benefit.

### Phase 5: Create SKILL.md

Produce a complete, production-quality `SKILL.md`.

Include only sections that materially help the skill.

Possible sections include:

- Purpose
- Core Principles
- When to Use
- When Not to Use
- Inputs
- Context Discovery
- Workflow
- Evidence Requirements
- Decision Logic
- Classification Methodology
- Constraints
- Output
- Final Quality Check

Do not force every skill into the exact same outline.

### Phase 6: Create References

Use references for substantial supporting material such as:

- output templates
- rubrics
- schemas
- scoring systems
- checklists
- methodologies
- domain reference material

References should support `SKILL.md`, not duplicate it.

### Phase 7: Update README

When a new skill is added, update the root `README.md` only where necessary.

At minimum consider:

- Available Skills
- Categories
- Repository Structure, if materially changed

Do not rewrite unrelated documentation.

### Phase 8: Validate Discovery

Run:

```bash
npx skills add MaurizioScrimaglia/scream-skills --list
```

Confirm that the new skill appears.

### Phase 9: Validate Installation

Install the new skill into a controlled project:

```bash
npx skills add MaurizioScrimaglia/scream-skills --skill <skill-name>
```

Prefer project-local installation for initial testing.

Expected universal location:

```text
.agents/skills/<skill-name>/
```

Verify that all expected files are present.

### Phase 10: Run a Real Test

Execute the skill against a realistic use case.

Use a deliberately minimal initial prompt.

The objective is to test the skill itself rather than compensate for weaknesses with detailed prompting.

Verify that the agent:

- discovers the skill
- follows `SKILL.md`
- reads required references
- respects constraints
- handles missing evidence correctly
- produces the intended output

### Phase 11: Evaluate the Result

Separate problems into:

- skill design problem
- unclear instruction
- implementation mistake
- model limitation
- agent-specific behavior
- environment limitation

Do not immediately redesign a skill because of one isolated execution result.

Prefer multiple realistic tests before introducing significant complexity.

## README Responsibilities

The root README is public documentation for users of the repository.

It should remain accurate about:

- project purpose
- available skills
- installation
- usage
- repository structure
- design principles
- categories
- licensing

Do not claim compatibility or behavior that has not been tested or verified.

## Validation Commands

Discover skills:

```bash
npx skills add MaurizioScrimaglia/scream-skills --list
```

Install a specific skill:

```bash
npx skills add MaurizioScrimaglia/scream-skills --skill <skill-name>
```

Inspect installed files:

```bash
find .agents/skills/<skill-name> -maxdepth 3 -type f -print
```

## Git Workflow

Default branch:

```text
main
```

Before making changes:

```bash
git status
git pull --ff-only
```

After changes:

```bash
git status
git diff
```

Commit changes with a focused commit message.

Examples:

```text
Add scream-audit skill
Add report template for scream-audit
Add Scream Skills agent guide
Update README with scream-foo
```

Avoid mixing unrelated changes in one commit.

## Current Repository State

Current validated skill:

```text
skills/quality/scream-audit/
```

Current category:

```text
quality
```

Current Scream Audit files:

```text
skills/quality/scream-audit/SKILL.md
skills/quality/scream-audit/references/report-template.md
```

License:

```text
MIT
```

## Collaboration Style

Work incrementally.

Do not rush several implementation steps ahead when important design decisions are unresolved.

During skill discovery:

1. understand the idea
2. challenge weak assumptions
3. define scope
4. agree on behavior
5. then create files

Once a decision is settled, be concrete.

When asking the user to create or modify a file, provide:

- exact path
- complete content when appropriate
- recommended commit message

Avoid em dashes in generated prose.

## Long-Term Direction

The long-term goal is for `scream-skills` to become a genuinely useful public collection of portable agent skills across multiple domains.

Possible future domains include:

- quality
- engineering
- reasoning
- research
- productivity
- operations
- product
- writing
- career
- documentation
- analysis

These are examples, not predefined categories.

Create categories only when real skills require them.

Every new skill should earn its place in the repository.
