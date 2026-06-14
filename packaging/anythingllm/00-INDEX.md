# Superpowers Skill Index

This workspace carries a set of **methodology skills** — disciplines for how to approach engineering work, ported from the Claude Code "superpowers" plugin. The full text of each is an attached document in this workspace. **Pin this index** so the catalog stays in context; retrieve a skill's own document when you need its full procedure.

> When a skill references Claude Code tooling you don't have (the `Skill` tool, `TodoWrite`, subagents, git worktrees, hooks), adapt the intent or skip that mechanic. The discipline matters, not the tooling.

## Process skills (decide *how* to approach the task — consider these first)

- **brainstorming** — *Use before any creative/build work: features, components, new behavior.* Explore intent, requirements, and design through dialogue, propose 2–3 approaches, and get the design approved **before** implementing. Document: `skills/brainstorming.md`.
- **systematic-debugging** — *Use on any bug, test failure, or unexpected behavior, before proposing a fix.* Reproduce, isolate, find the root cause; don't patch symptoms. Document: `skills/systematic-debugging.md`.

## Implementation skills

- **test-driven-development** — *Use when implementing any feature or bugfix.* Write the failing test first, watch it fail, write minimal code to pass, refactor. Iron law: no production code without a failing test first. Document: `skills/test-driven-development.md`.
- **writing-plans** — *Use when you have a spec or multi-step task, before touching code.* Produce a concrete, ordered implementation plan. Document: `skills/writing-plans.md`.
- **verification-before-completion** — *Use before claiming work is complete, fixed, or passing.* Run the verification command and confirm the output before asserting success. Evidence before assertions. Document: `skills/verification-before-completion.md`.
- **writing-skills** — *Use when creating or editing a reusable methodology/process document.* How to write a skill that's clear, triggerable, and followed. Document: `skills/writing-skills.md`.

## Not included in this package

Six Claude-Code-workflow-specific skills were intentionally left out because they depend on mechanics AnythingLLM doesn't have (subagents, git worktrees, multi-session orchestration): `using-git-worktrees`, `dispatching-parallel-agents`, `subagent-driven-development`, `executing-plans`, `requesting-code-review`, `receiving-code-review`, and `finishing-a-development-branch`. If you ever want them, they can be ported with adaptations.
