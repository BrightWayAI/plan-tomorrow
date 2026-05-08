# plan-tomorrow

Calendar-first daily planning for Claude (Cowork + Claude Code).

You open your calendar tomorrow morning and just start working — no separate plan document to read, no list to decipher. Every block on your calendar tells you what to do, why it matters, and what "done" looks like.

## What it does

- Pulls **CRM tasks** for the target day (delegates to the `pipeline-analyst` agent if installed)
- Pulls **project context** from working memory (`claude-cortex` plugin)
- Scans **Gmail** for unanswered threads and implied action items
- Optionally pulls **outreach contacts** from the weekly outreach plan
- Reads **existing calendar** to find free slots
- Creates **time blocks with rich descriptions** — every block is self-contained context
- Confirms with you before writing to the calendar

The output isn't a doc. It's **calendar events**.

## Install

Recommended: install via the [BrightWayAI marketplace](https://github.com/BrightWayAI/claude-plugins).

Or directly:

```
/plugin marketplace add BrightWayAI/plan-tomorrow
/plugin install plan-tomorrow@plan-tomorrow
```

## First-time setup

Run `/setup-plan`. The interview captures:

- **Identity** — your name, company, role
- **CRM** — which CRM, your owner ID (HubSpot / Salesforce / Pipedrive / etc.)
- **Working hours** — start, end, time zone
- **Calendar conventions** — color for task blocks, emoji conventions, max blocks per day
- **Integrations** — whether you use weekly-outreach (for outreach blocks), claude-cortex (for memory), brightway-core (for pipeline-analyst)

Saved to `references/user-context.md` (gitignored).

## Companion plugins

`plan-tomorrow` is more useful when paired with:

- **claude-cortex** — for working memory access (`/recall`, `/remember`)
- **brightway-core** — provides the `pipeline-analyst` subagent for cleaner CRM scoring
- **weekly-outreach** — provides a weekly outreach queue that plan-tomorrow can pull contacts from

It works without them, but you'll get a thinner plan.

## What's inside

```
.claude-plugin/plugin.json
agents/                     (none — delegates to pipeline-analyst in brightway-core)
commands/
  plan-tomorrow.md          Slash command
  setup-plan.md             Interview
skills/
  plan-tomorrow/SKILL.md    Auto-fires on planning phrases
  setup/SKILL.md            Auto-fires on setup phrases
references/
  user-context.template.md  Structure (committed)
  user-context.md           Your config (gitignored)
```

## License

MIT.
