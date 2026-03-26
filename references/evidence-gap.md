# Evidence / Assumption / Gap / Blocked Source

## Purpose

Use this file to keep the report honest when evidence is incomplete and to distinguish between:
- what is already supported
- what is inferred
- what still needs another search round
- what now requires human help

## Definitions

### Evidence
Information directly supported by:
- user-provided material
- public or licensed external sources already retrieved
- internal documents already supplied by the human

### Assumption
Reasoned inference that helps the report move forward but is not fully verified.
Write it carefully and label it.

### Gap
A missing input that may still be solvable through another search round.

### Blocked Source
A source or data point that appears material but cannot currently be accessed because of login, paywall, broken interaction, client-only access, internal systems, or human-held documents.

## Required behavior

When a key point lacks support:
- do not fake certainty
- do not blur the weakness into confident prose
- decide whether it is a `Gap` or a `Blocked Source`
- trigger `search-again` for gaps that still look publicly solvable
- trigger `human-assist` for blocked sources

## Standard gap template

```md
### Gap N
- Gap:
- Why it matters:
- Best public path already tried:
- What is needed:
- Impact on current report:
```

## Standard blocked-source template

```md
### Blocked Source N
- Item:
- Why it matters:
- Best public path already tried:
- Access blocker:
- Suggested human action:
- Impact on current report:
```
