# Learn AI with Nick — Claude Code Skills

A set of Claude Code skills for daily productivity. Built for the [Learn AI with Nick](https://learnaiwithnick.com) community.

## Skills

### Newsletter Digest

Fetches your recent newsletters from Gmail and compiles a structured digest with themes, highlights, and action items.

```bash
claude install-skill markhamsquareventures/learn-ai-with-nick-plugins/skills/newsletter-digest
```

**Requires:** Gmail MCP connection in Claude Code

### Meetings Digest

Reads Granola meeting transcripts and extracts action items, commitments, and decisions into a structured summary.

```bash
claude install-skill markhamsquareventures/learn-ai-with-nick-plugins/skills/meetings-digest
```

**Requires:** Granola meeting transcripts saved as markdown files

### Prep My Day

Outputs a structured daily template with optional hook points where you can wire in your own tools — task managers, calendars, email digests, and meeting prep.

```bash
claude install-skill markhamsquareventures/learn-ai-with-nick-plugins/skills/prep-my-day
```

**Requires:** Nothing — works standalone. Hooks are optional.

## How it works

Each skill is a markdown file that tells Claude Code what to do. Install a skill, then run it by name:

```
/learn-ai-with-nick:newsletter-digest
/learn-ai-with-nick:meetings-digest
/learn-ai-with-nick:prep-my-day
```

All skills output to the conversation — they don't write files or modify your system. Copy the output wherever you need it.

## License

MIT
