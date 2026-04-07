---
name: meetings-digest
version: 1.0.0
description: Read Granola meeting transcripts and extract action items, commitments, and decisions. Use when asked to "digest meetings", "check meetings", "pull action items", or "meeting summary".
allowed-tools:
  - Read
  - Glob
---

# Meetings Digest

You read Granola meeting transcripts and output a structured summary of action items, commitments, and decisions. All output goes to the conversation — do not write any files.

---

## STEP 1: Locate Granola Transcripts

1. Ask the user for the path to their Granola notes directory if not already known.
   - Common default: `~/Documents/Granola/`
   - Also check: `~/Library/Application Support/Granola/`
2. Glob for all `.md` files in that directory (and subdirectories).
3. Read each file. Focus on the most recent files — default to meetings from the last 24 hours based on the date in the filename or frontmatter.
4. If no recent transcripts exist, tell the user and stop. Offer to look further back if they want.

---

## STEP 2: Read and Extract

For each transcript:

1. Read the full file content — both the user's private notes and the AI-enhanced notes/transcript sections.
2. Identify the meeting title, date, and attendees from the frontmatter or header.
3. Scan for action items, commitments, and decisions. Look for:
   - **Explicit commitments:** "I'll...", "I need to...", "let's...", "we should...", "action item:..."
   - **Requests to you:** "can you...", "please...", "send me...", "follow up on..."
   - **Decisions:** "we decided to...", "the plan is to...", "agreed that..."
   - **Deadlines:** "by Friday...", "next week...", "end of sprint..."
4. For each item, capture:
   - A concise description of the task or decision
   - The meeting it came from
   - The owner (if clear from context)
   - Any deadline mentioned

---

## STEP 3: Output Structured Summary

Output using this format:

```
# Meetings Digest — YYYY-MM-DD

**Meetings processed:** N
**Total items extracted:** N

## Action Items
- [ ] Item description (from: Meeting Title, owner: Name, due: Date)
- [ ] ...

## Commitments Made
- You committed to X (from: Meeting Title)
- [Other person] committed to Y (from: Meeting Title)

## Decisions
- Decision description (from: Meeting Title)
- ...

## Key Discussion Points
- Brief summary of important topics that don't have direct action items but are worth remembering
```

If a meeting had no action items, mention it briefly — "No action items from [Meeting Title]" — so the user knows it was reviewed.

---

## STEP 4: Summary

End with: how many meetings were processed, how many items per category, and flag anything with an upcoming deadline that needs attention soon.
