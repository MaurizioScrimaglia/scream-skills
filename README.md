# Scream Skills

Reusable, tool-agnostic skills for AI agents.

Scream Skills is a growing collection of reusable agent skills designed to perform specialized tasks consistently, with clear workflows, constraints, and output contracts.

The goal is simple: define useful capabilities once, then reuse them across compatible AI agents without tying the underlying logic to a specific model, vendor, or platform.

## Available Skills

| Skill | Category | Description |
|---|---|---|
| [scream-audit](skills/quality/scream-audit/SKILL.md) | Quality | Performs a comprehensive, evidence-based audit of a software application, website, service, or repository and produces a detailed professional assessment with findings, risks, strengths, and remediation priorities. |

More skills will be added as they are designed and validated.

## Install

### Discover available skills

```bash
npx skills add MaurizioScrimaglia/scream-skills --list
```

### Install interactively

```bash
npx skills add MaurizioScrimaglia/scream-skills
```

### Install a specific skill

```bash
npx skills add MaurizioScrimaglia/scream-skills --skill scream-audit
```

Installation behavior and the final skill location may depend on the AI agent or development environment being used.

## Using a Skill

After installation, ask your compatible agent to use the installed skill for the relevant task.

For example:

```text
Use scream-audit to audit this application.
```

The exact invocation mechanism may vary by agent. The skill itself remains the source of truth for how the task should be performed.

## Repository Structure

Skills are grouped by category only when a category is actually needed.

```text
scream-skills/
├── skills/
│   └── quality/
│       └── scream-audit/
│           ├── SKILL.md
│           └── references/
│               └── report-template.md
├── LICENSE
└── README.md
```

Each skill has its own directory.

The main `SKILL.md` defines the skill's behavior, workflow, constraints, and decision logic.

Supporting material can live under `references/` when the skill requires additional templates, methodologies, or documentation.

## Design Principles

### Tool agnostic

Core skill behavior should not depend on a specific AI model, vendor, browser, coding agent, connector, or external tool unless that dependency is intrinsic to the skill.

### Evidence over speculation

Skills should prefer observable facts and available evidence over assumptions.

When something cannot be verified, the skill should say so explicitly.

### Reusable by design

A skill should solve a repeatable problem rather than encode instructions for a single one-off task.

### Predictable outputs

When appropriate, skills should define clear output contracts so that repeated executions remain consistent and useful.

### Minimal assumptions

Skills should infer what they can from available context and ask questions only when missing information materially affects the result.

### No unnecessary vendor lock-in

Platform-specific integrations may exist, but reusable reasoning and domain logic should remain separate whenever possible.

## Skill Structure

A typical skill looks like:

```text
skill-name/
├── SKILL.md
└── references/
    └── optional-supporting-file.md
```

`SKILL.md` is the primary definition of the skill.

It should describe:

- what the skill does
- when it should be used
- how it should reason about the task
- what evidence or context it needs
- what constraints it must respect
- what output it should produce

## Categories

Categories are created only when needed.

A new skill should first be placed in an existing category when that category accurately describes its primary purpose.

A new category should be introduced only when existing categories would be misleading.

Current categories:

- `quality`

## License

This repository is licensed under the [MIT License](LICENSE).
