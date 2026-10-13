---
description: Read my recent Slack messages and write a daily digest file. Asks for me first, then a short summary per channel. Read-only, never posts.
---

# Slack Digest

Read my Slack messages since the last digest and save a plain-text summary I can skim.

## Rules

- **Read only.** Never send, schedule, draft, react to, or edit anything in Slack.
- **Don't guess.** If a message links to something you can't read (a DM I'm not in, a deleted message), list the link and ask me to paste it.
- **Don't decide for me.** If you're unsure whether something needs me, put it under "Asks of me" with a note.

## Steps

1. **Find the window.** Read the last run time from `~/slack_notes/.last_run`. If it doesn't exist, use 24 hours ago. Start a few minutes early so nothing falls in a gap.
2. **Pull the messages** with the Slack connector's search tool (`slack_search_public_and_private`):
   - `after` = the window start (Unix timestamp), `only_my_channels` = true, `sort` = timestamp, `response_format` = detailed, `include_bots` = true
   - Keep paging until there are no more results.
3. **Check threads.** For any message with replies, make sure every reply was captured. If not, read the thread with `slack_read_thread`.
4. **Write the digest** to `~/slack_notes/YYYY-MM-DD.txt` (today's date). If the file exists, append a new section with the time window. Plain text, this format:

```
=== Slack digest: <start time> to <end time> (<N> messages) ===

ASKS OF ME
- <who> in <channel>: <what they need> <permalink>

BY CHANNEL
- <channel>: <1-2 sentences. When a few people go back and forth, write it as a conversation: "A and B discussed X. Outcome: Y.">

KEY THINGS TO REMEMBER
- <decisions, dates, numbers, or facts worth keeping>

NEED A PASTE
- <links you couldn't read>
```

5. **Save the run time** to `~/slack_notes/.last_run`.
6. **Show me the "Asks of me" section** in the chat, short. I'll open the file for the rest.

Reminder for me: the connector can't mark messages as read. I do that in the Slack app (Shift+Esc marks everything read).
