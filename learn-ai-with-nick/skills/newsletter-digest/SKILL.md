---
name: newsletter-digest
version: 1.0.0
description: Fetch newsletters from Gmail and compile a digest with themes, highlights, and action items. Use when asked to "digest newsletters", "check newsletters", "what landed in my inbox", or "newsletter summary".
allowed-tools:
  - mcp__claude_ai_Gmail__gmail_search_messages
  - mcp__claude_ai_Gmail__gmail_read_message
  - mcp__claude_ai_Gmail__gmail_read_thread
  - mcp__claude_ai_Gmail__gmail_list_labels
---

# Newsletter Digest

You fetch recent newsletters from Gmail and output a structured digest. All output goes to the conversation — do not write any files.

---

## STEP 1: Search Gmail for Newsletters

1. Use `gmail_search_messages` to find newsletters from the last 24 hours.
   - Try this query first: `category:promotions newer_than:1d`
   - Then also search: `label:newsletters newer_than:1d` (if the user has a newsletters label)
2. Deduplicate results by message ID.
3. If no messages are found, tell the user there are no new newsletters and stop.

---

## STEP 2: Read Each Newsletter

1. For each message found, use `gmail_read_message` to get the full content.
2. Extract: sender name, subject line, and body text.
3. Skip messages that are clearly not newsletter content — receipts, password resets, order confirmations, marketing promos for a single product. You want editorial content: curated links, essays, roundups, industry news.
4. If a message is truncated or you need the full thread, use `gmail_read_thread`.

---

## STEP 3: Compile the Digest

Analyze all newsletters and output the digest using this structure:

```
# Newsletter Digest — YYYY-MM-DD

## Top Themes
1. **Theme title** — 1-sentence explanation of why this matters
2. ...
(3-5 themes that appear across multiple newsletters)

## Newsletter Highlights

### [Newsletter Name] — [Subject Line]
- Key takeaway 1
- Key takeaway 2
- Key takeaway 3

### [Newsletter Name] — [Subject Line]
- ...

(repeat for each newsletter)

## Action Items
- [ ] Things worth doing based on what you read

## Links Worth Reading
- [Article title](URL) — why it's worth your time
- ...
```

Keep it concise. The goal is to save the user from reading 10+ newsletters — give them the signal, skip the noise.

---

## STEP 4: Summary

End with a short summary: how many newsletters were processed and the single most interesting finding across all of them.
