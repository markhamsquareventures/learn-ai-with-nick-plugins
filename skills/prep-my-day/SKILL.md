---
name: prep-my-day
version: 1.0.0
description: Scaffold a structured daily template with optional hook points for integrations. Use when asked to "prep my day", "start my day", "daily scaffold", or "set up today".
allowed-tools: []
---

# Prep My Day

You output a structured daily template that helps the user organize their day. All output goes to the conversation — do not write any files.

The template uses a **hooks pattern**: clearly marked sections where users can wire in their own integrations (task managers, calendars, email, meeting tools). Hooks are optional — the template works standalone as a simple daily planner.

---

## Output the Daily Template

Use today's date from the system context. Output the following template:

```markdown
# YYYY-MM-DD

## Priorities
What are the 1-3 things that would make today a success?

1.
2.
3.

## Tasks

- [ ] ...

<!-- HOOK: task-manager-sync
     Pull in tasks from your task manager. Examples:
     - Jira: use an MCP server or API call to fetch current sprint items
     - Linear: pull active issues assigned to you
     - Todoist: sync today's tasks
     - GitHub: fetch assigned issues or PRs needing review
     Replace this comment with a skill call or your own task list. -->

## Calendar

<!-- HOOK: calendar-review
     Pull in today's schedule. Examples:
     - Google Calendar: use the Google Calendar MCP to list today's events
     - Outlook: fetch today's meetings via API
     Show meetings, focus blocks, and deadlines for the day.
     Replace this comment with your calendar output. -->

## Inbox

<!-- HOOK: email-digest
     Catch up on overnight signal. Examples:
     - Run /learn-ai-with-nick:newsletter-digest to summarize newsletters
     - Use an email MCP to surface flagged or important messages
     Replace this comment with your digest output. -->

## Meetings Prep

<!-- HOOK: meeting-prep
     Prepare for today's meetings. Examples:
     - Run /learn-ai-with-nick:meetings-digest for yesterday's action items
     - Pull agenda docs for today's meetings
     - Review notes from previous meetings with the same attendees
     Replace this comment with your meeting prep output. -->

## Notes

(Space for freeform notes throughout the day)

## End of Day

- What went well?
- What would I do differently?
- Carry forward to tomorrow:
```

---

## After Output

Tell the user:

1. **The template is ready** — copy it into your notes app, journal, editor, or wherever you plan your day.
2. **Hooks are optional** — each `<!-- HOOK: ... -->` block describes where you can plug in tools. Replace the comment with a skill call, MCP tool output, or just type in your own content.
3. **Customize freely** — add sections, remove what you don't need, change the structure. This is a starting point, not a rigid format.
