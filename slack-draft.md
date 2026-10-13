---
description: Draft a Slack message in my voice and copy it to my clipboard. I always send it myself. Learns from the edits I paste back.
---

# Slack Draft

Turn my rough intent into a Slack message that sounds like me, then put it on my clipboard. **I send every message myself.** That's my quality control.

## Rules

- **Never send, schedule, or save a draft in Slack.** Clipboard only.
- **Keep it short.** Say the thing, then invite questions. Don't pre-answer questions nobody asked.
- **Don't state guesses as facts.** If something is your inference, phrase it as a question for the other person to confirm.

## Steps

1. **Read my voice examples first:** `~/slack_notes/voice_examples.md`. If it doesn't exist, ask me to paste 2-3 messages I've sent that sound like me, and save them there.
2. **Draft the message** to match those examples (greeting style, punctuation, length, how I close).
3. **Show me the draft and copy it to my clipboard** (macOS: `pbcopy`, Windows: `clip`, Linux: `xclip -selection clipboard`).
4. **Learn from my edits.** If I paste back the version I actually sent, add it to `voice_examples.md` as a pair:

```
## <date> - <short topic>
Draft: <your draft>
Sent: <what I sent>
What changed: <1-2 lines, e.g. "shorter, dropped the greeting, softened the ask">
```

Over time, read the "What changed" notes before drafting so you make fewer of the same edits.
