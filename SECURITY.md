# Security Policy

## What this plugin does with your data

Plan Tomorrow pulls from your CRM, working memory, calendar, and inbox to create time blocks on your calendar. Read-most-things; create-only on the calendar.

**Reads:**
- **Calendar** — existing events for the target day to find free slots and identify meetings to prep for.
- **CRM** (or `pipeline-analyst` subagent if `core-ops` installed) — tasks owned by you, status NOT_STARTED or IN_PROGRESS, due on/before target day.
- **Email** (Gmail) — unanswered inbound, threads where you were last sender 3+ days ago.
- **Working memory** (if `claude-cortex` installed) — `~/Documents/Claude/memory/DASHBOARD.md` and active project nodes for P0/P1 actions, open threads.
- **Weekly outreach** (if `weekly-outreach` installed) — current week's outreach queue for outreach blocks.
- **Plugin references** — `references/user-context.md`.
- **Shared user-level config** — `~/Documents/Claude/identity.md` (read-only).

**Writes (all behind explicit user approval):**
- **Calendar events** — *new* time blocks for the target day. **Always created with `sendUpdates: "none"`** (no attendee notifications) and a `colorId` per your preferences.
- **Plugin user-context** — `references/user-context.md` (after `/setup-plan`).

**Does not:**
- **Edit or update existing calendar events.** Strictly read-only on existing events; this is a hard rule documented in the command body.
- **Create events with attendees.** Task blocks are personal; no invitations.
- **Modify CRM tasks.** Read-only against CRM.
- **Modify working memory.** Read-only against cortex memory.
- **Auto-create blocks.** Always presents a confirmation table; waits for user "yes."

## Where data lives

- Plugin reference files inside the installed plugin directory.
- Calendar events live in your authorized calendar service.
- Shared identity (read-only) at `~/Documents/Claude/identity.md`.

## What gets sent off your machine

- Whatever your authorized CRM, calendar, Gmail connectors send when invoked.

## Supported versions

| Version | Supported |
|---------|-----------|
| 0.1.x   | Yes       |

## Reporting a vulnerability

Report privately via GitHub Security Advisories:

https://github.com/BrightWayAI/plan-tomorrow/security/advisories/new

Do not open a public issue for security concerns. We aim to respond within 5 business days.
