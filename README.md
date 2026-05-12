# plan-tomorrow — DEPRECATED

> **This plugin has been folded into [`daily-brief`](https://github.com/BrightWayAI/daily-brief) as of 2026-05-12 (daily-brief v0.2.0).**

The `/plan-tomorrow` command and its `/setup-plan` config interview now live inside the daily-brief plugin. Daily-brief is the single home for the daily ops loop:

- `/brief` — today's working surface (Cowork artifact)
- `/process-brief` — route textarea annotations to drafts, task updates, meeting talking points
- `/plan-tomorrow` — calendar-first planning of the next business day
- `/setup-brief`, `/setup-plan` — config

## Migration

**Existing users:** no migration required.

- `/plan-tomorrow` continues to read your existing `<config-root>/plugins/plan-tomorrow.user-context.md` unchanged. The file lives at the same path; only the plugin source moved.
- After your next Cowork restart, the marketplace will pull `daily-brief v0.2.0` which provides the `/plan-tomorrow` command. Your existing plan-tomorrow plugin install can be removed (or left in place — it'll just be redundant).

**New users:** install `daily-brief` from the [Nucleus](https://github.com/BrightWayAI/nucleus) marketplace. Do not install this plugin.

## Why the fold

Daily-brief and plan-tomorrow shared ~90% of their data sources (calendar, CRM, cortex memory, inbox). Two plugins for one ops loop added decision cost ("which do I run?") without adding capability. Folding them keeps both verbs but reduces the marketplace catalog.

## Archive

This repository is archived (read-only) on GitHub. The source code and history remain accessible. See [daily-brief](https://github.com/BrightWayAI/daily-brief) for the active home of these commands.
