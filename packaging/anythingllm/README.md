# Superpowers → AnythingLLM package

A port of the portable-core superpowers skills for use in [AnythingLLM](https://anythingllm.com/), which has no equivalent of Claude Code's SessionStart hook or `Skill` tool. It reproduces the "always-on dispatcher + load-on-demand" behavior using AnythingLLM's native mechanisms.

## What's here

| File | Role |
|------|------|
| `SYSTEM-PROMPT.md` | The dispatcher — paste into a workspace's **Chat Settings → Prompt**. Always-on. Carries the "check for a relevant skill before you act" discipline + the skill catalog. |
| `00-INDEX.md` | The skill catalog as a document — **upload and pin** it so the catalog stays in context every turn. |
| `skills/*.md` | The six methodology skill bodies, pulled in on demand via RAG. |
| `IMPORT.md` | Step-by-step setup (create workspace → paste prompt → upload + embed → pin index → test). |

## Scope

Includes the six **portable** methodology skills: `brainstorming`, `test-driven-development`, `systematic-debugging`, `verification-before-completion`, `writing-plans`, `writing-skills`.

The Claude-Code-workflow-specific skills (`using-git-worktrees`, `dispatching-parallel-agents`, `subagent-driven-development`, `executing-plans`, `requesting-code-review`, `receiving-code-review`, `finishing-a-development-branch`) are intentionally omitted — they depend on subagents, worktrees, and multi-session orchestration that AnythingLLM doesn't have.

## Notes

- Each skill body carries a small banner telling the model to adapt/ignore Claude Code tooling references (`Skill` tool, `TodoWrite`, subagents) since AnythingLLM lacks them.
- Small local models follow system-prompt discipline less reliably than hosted Claude — see `IMPORT.md` for tuning levers (pin specific skill bodies, shorten the dispatcher).
- Tool-heavy MCP servers can overflow a small local model's context in agent mode; enable MCP servers selectively per task.

See [`IMPORT.md`](IMPORT.md) to set it up.
