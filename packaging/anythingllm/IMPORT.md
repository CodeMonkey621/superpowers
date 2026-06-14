# Importing Superpowers into AnythingLLM

Package contents:
- `SYSTEM-PROMPT.md` — the dispatcher to paste into the workspace prompt.
- `00-INDEX.md` — the skill catalog; upload **and pin** this one.
- `skills/*.md` — the 6 methodology skill bodies; upload these.

UI labels can vary slightly between AnythingLLM versions; the flow is the same.

## 1. Create (or pick) a workspace
- Left sidebar → **+ New Workspace** → name it e.g. `Superpowers`.

## 2. Paste the dispatcher into the system prompt
- Hover the workspace → click the **gear** (Settings) → **Chat Settings**.
- In **Prompt**, paste everything *below the `---`* in `SYSTEM-PROMPT.md`.
- While you're here, set **Chat mode = `chat`** (not `query`). Query mode only answers from documents and will refuse general coding help.
- **Save**.

## 3. Upload the skill documents
- Back in the workspace, click the **upload / document** icon (paperclip or "Manage Documents").
- In the document modal, **drag in** all of these:
  - `00-INDEX.md`
  - every file in `skills/` (all 6)
- Select the uploaded files → **Move to Workspace** → then click **Save and Embed**.
  - A fresh desktop install uses the built-in AnythingLLM embedder, so this works offline — no API key needed.

## 4. Pin the index
- In the workspace document manager, find `00-INDEX.md` → click its **pin** icon.
- Pinning injects the full catalog into every chat, so the model always knows which skills exist and when to use them. The individual skill bodies stay unpinned — they're pulled in on demand by retrieval.

## 5. Test it
Start a new chat in the workspace and try a prompt that should trigger a skill, e.g.:

> "Let's build a small CLI that renames files by a pattern."

A working setup should respond by **invoking brainstorming** — asking about intent/requirements and proposing approaches *before* writing code, rather than dumping an implementation. Try also:

> "This function returns the wrong total. Fix it."

…which should trigger **systematic-debugging** (reproduce + find root cause) rather than an immediate guess.

## Notes & tuning
- **If the model ignores the skills:** smaller local models follow system-prompt discipline less reliably. Levers: (a) keep `00-INDEX.md` pinned; (b) pin one or two specific skill bodies you care most about (e.g. `test-driven-development.md`) so they're always in context; (c) shorten the system prompt to just the Rule + the catalog table if the model gets distracted by the long version; (d) use a more capable model for the workspace if available.
- **Updating skills:** re-run the packaging step against a newer superpowers version, re-upload changed files, and re-embed. Source lived at `C:\Users\john\.claude\plugins\cache\claude-plugins-official\superpowers\<version>\skills`.
- **Adding the trimmed CC-workflow skills later:** they reference subagents/worktrees/multi-session orchestration that AnythingLLM lacks; they'd need real adaptation, not just a copy.
