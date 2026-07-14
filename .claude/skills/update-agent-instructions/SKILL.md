---
name: update-agent-instructions
description: Use this when the user wants to update or refresh the AI agent instructions for the companion app docs — the `.github/copilot-instructions.md` file and the companion-docs-* skills.
---

# Update agent instructions

Update the AI agent instructions for the companion app documentation. There are two layers, and they must stay consistent with each other:

- `.github/copilot-instructions.md` — the always-on baseline, symlinked to `CLAUDE.md` and `GEMINI.md`, so it is read by Copilot, Claude Code, and Gemini.
- `.claude/skills/companion-docs-*` — the detailed, on-demand skills that Claude Code loads by context.

Review both against these current Home Assistant style-guide sources:

- [General style guide](https://developers.home-assistant.io/docs/documenting/general-style-guide)
- [Documentation standards](https://developers.home-assistant.io/docs/documenting/standards)
- [YAML style guide](https://developers.home-assistant.io/docs/documenting/yaml-style-guide)
- The [Microsoft Writing Style Guide](https://learn.microsoft.com/style-guide/welcome/)

Also cross-check the equivalent files in the main website repo for structure and naming, adapting rather than copying (that repo is Jekyll/Liquid; this one is Docusaurus/MDX):

- `https://github.com/home-assistant/home-assistant.io/tree/current/.claude/skills`
- `https://github.com/home-assistant/home-assistant.io/blob/current/.github/copilot-instructions.md`

## Rules

- Preserve the existing structure and wording where possible.
- Prefer small, reviewable edits over broad rewrites.
- Remove exact duplicates. Merge overlapping guidance only when the meaning is the same or one source clearly supersedes the other.
- If existing instructions conflict with the referenced style guides, update them to match the style guides.
- Keep `.github/copilot-instructions.md` and the `companion-docs-*` skills consistent. When you change a rule in one, update the other so they do not drift.
- Keep guidance adapted to this repository: Docusaurus/MDX, companion apps (iOS and Android), no integration pages, no blog.
- Summarize guidance into actionable instructions. Do not copy large examples, templates, or explanatory text unless needed.
- Do not make wrapping-only or other arbitrary style edits.
- Do not edit the `CLAUDE.md` or `GEMINI.md` symlinks. Editing `.github/copilot-instructions.md` updates all three.

If any remote source cannot be fetched, stop and report the missing source instead of guessing.

After editing, provide a short summary of the changes made.
