# Changelog

All notable changes to plan-tomorrow are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/). Versions match `plugin.json`.

## [0.1.0] — Initial release

### Added
- Calendar-first daily planning slash command (`/plan-tomorrow`) — pulls CRM tasks, working memory context, inbox action items, and existing calendar events; creates new time blocks with full context baked into each block's description.
- Critical rules: never edit existing calendar events (read-only), only create new blocks, always present a confirmation table, don't overpack the day.
- Generic and configurable — captures working hours, time zone, CRM owner ID, calendar conventions (color, emoji map, max blocks per day) via `/setup-plan`.
- Delegates CRM scoring to `pipeline-analyst` subagent (in `core-ops`) when installed; falls back to direct CRM queries.
- Optional integration with `claude-cortex` for working-memory context.
- Optional integration with `weekly-outreach` for pulling outreach contacts into outreach blocks.
- Setup reads `~/Documents/Claude/identity.md` (shared identity from cortex) when available.
- Rich event description templates per block type: deep work, meeting prep, emails, outreach batch, post-call capture.
