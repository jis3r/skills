---
name: pr-draft
description: Generate concise pull request descriptions from git diffs, branch changes, issue notes, or implementation summaries. Use this whenever the user asks for a PR description, PR draft, pull request body, merge request text, GitHub PR text, or asks to turn a diff into reviewer-facing notes. Prefer short, author-owned descriptions over polished AI-style prose.
---

# PR Draft

Write PR descriptions that are useful to reviewers and short enough that an author would actually keep them.

## Workflow

1. Inspect the change.
   - Use the base the user gives, e.g. `git diff origin/main`.
   - If no base is given, start with `git diff --stat`, `git diff --name-only`, and targeted diffs.
   - Ignore unrelated dirty files unless they are in the requested diff. If they appear in the diff, call them out briefly.

2. Extract only what matters.
   - Problem: what broke, what was missing, or what capability is being added.
   - Why: the design reason, rollout reason, or constraint that shaped the approach.
   - Changes: concrete technical changes, grouped by behaviour rather than file.
   - Notes: risks, edge cases, compatibility, feature flags, migrations, validation gaps.

3. Draft concisely.
   - Prefer sentence fragments and direct bullets.
   - Do not include a full file-by-file changelog.
   - Do not invent customer context, issue links, or test runs.
   - Do not sound like marketing or a generated release note.
   - Include TODOs only when the author must fill a real gap.

## Default Format

Use this by default:

```markdown
Summary
[One short paragraph or 1-2 bullets.]

What changed
- [change]
- [change]
- [change]

Why
- [reason]
- [reason]

Notes
- [risk, edge case, rollout detail, or validation gap]
- [optional]
```

For bug fixes, use this shorter shape when it reads better:

```markdown
Problem
[1-2 sentences.]

Why this approach
[1-3 sentences.]

Technical changes
- [change]
- [change]

Risks / edge cases
- [risk]
- [edge case]
```

For very small PRs, compress further:

```markdown
[One-sentence summary.]

Changes:
- [change]
- [change]
- [change]
```

Only add `Validation` when the user asks for it, the repo template requires it, or concrete commands are known. Keep it short:

```markdown
Validation
- `[command]`
- Not run: [reason]
```

## Style Rules

Keep it concise:
- 4-8 bullets is usually enough for medium PRs.
- 10-14 bullets is the upper range for large PRs.
- One bullet should usually fit on one line.
- Remove obvious implementation details that reviewers can see in the diff.
- Merge related backend/frontend/type/test changes into one bullet when possible.

Keep it human:
- Use "Adds", "Fixes", "Keeps", "Prevents" sparingly; avoid every bullet starting the same way.
- Avoid "This PR..." except in the summary if it reads naturally.
- Avoid generic claims like "improves UX" unless the exact improvement is named.
- Avoid confident context not present in the diff.

Keep it reviewer-focused:
- Mention feature flags and defaults.
- Mention data migrations/backfills if relevant.
- Mention old data compatibility.
- Mention behaviour that intentionally stays unchanged.
- Mention unrelated changes if they are included in the diff.

## Examples

### Feature

```markdown
Summary
Adds tenant-configurable default assistant settings with tool gates for plugins, knowledge bases, third-party connectors, and web search.

What changed
- add default_assistant capability type on backend and frontend
- add allowed_tools support for default assistants
- validate default-assistant payloads and reject allowed_tools on other capability types
- add admin default-assistant page and dedicated backend routes
- apply default assistant when the user has not picked one in the panel
- gate in-panel tools from default-assistant allowed_tools
- update capability editor, payload builder, API models, and translations
- add tests for default-assistant validation, tool gates, and serialized capability payloads

Why
- replace tenant-specific hardcoded assistant tool disabling
- let admins set default assistant behaviour per workspace or org
- prevent disabled default-assistant tools from leaking through prompts, UI, or the read_file integration
- keep existing assistant behaviour when no default assistant is configured

Notes
- default assistant is managed only through dedicated default-assistant routes
- default assistant never appears in normal capability lists or launch suggestions
- web search still also depends on feature_flags.web_access
```

### Bug Fix

```markdown
Problem
For agents that require file uploads, the Send button was disabled until a file was attached. Pressing Enter still submitted the chat, so users could start the agent without the required file context.

Why this approach
The Send button state was already correct. The broken part was the keyboard path. Enter now follows the same submit rules, with a warning toast when the required file is missing.

Technical changes
- added shared submit state for message, files, and required-file status
- guarded handleSubmit against missing required files
- shows a warning toast when Enter is pressed without required files
- allows file-only submission once a file is attached
- added English and German toast copy

Risks / edge cases
- disabled Send button still cannot be clicked, so warning only appears for Enter
- upload-in-progress still blocks submit
- file-only submit is allowed whenever at least one file is attached
```

### Tiny PR

```markdown
Fixes assistant follow-up threads when the agent requires uploads.

Changes:
- allow follow-up messages when any prior message had attachments
- keep upload-required validation for new threads without documents
- tell the backend that prior attachments still apply to follow-up questions
```
