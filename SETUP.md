# Connect Slack to Claude Code (read-only)

## 1. Log in to Claude Code with your claude.ai account

Connectors only load when Claude Code uses your claude.ai login (not an API key or Bedrock). Run `/status` to check, and `/login` to switch if needed.

## 2. Connect Slack from Claude Code

Run `/mcp`. Find **claude.ai Slack** in the claude.ai section (it may be under "Show unused connectors"), select it, and sign in to Slack.

If Slack isn't listed at all, your org hasn't added it yet. On Team and Enterprise plans only admins can add connectors, so ask your Claude admin. On a personal plan, add it at **claude.ai/customize/connectors**.

## 3. Test it

Quick test: ask Claude Code "summarize my Slack messages from the last hour".

## 4. Make it read-only (recommended)

Add this to `~/.claude/settings.json` so Claude Code can't post, react, or edit in Slack, even by mistake:

```json
{
  "permissions": {
    "deny": [
      "mcp__claude_ai_Slack__slack_send_message",
      "mcp__claude_ai_Slack__slack_send_message_draft",
      "mcp__claude_ai_Slack__slack_schedule_message",
      "mcp__claude_ai_Slack__slack_add_reaction",
      "mcp__claude_ai_Slack__slack_create_conversation",
      "mcp__claude_ai_Slack__slack_create_canvas",
      "mcp__claude_ai_Slack__slack_update_canvas",
      "mcp__claude_ai_Slack__slack_create_list",
      "mcp__claude_ai_Slack__slack_add_list_record",
      "mcp__claude_ai_Slack__slack_update_list",
      "mcp__claude_ai_Slack__slack_update_list_record",
      "mcp__claude_ai_Slack__slack_get_file_upload_url",
      "mcp__claude_ai_Slack__slack_complete_file_upload"
    ]
  }
}
```

If you already have a `permissions` block, add these lines to its `deny` list instead of replacing it.

## 5. Add the skills

Each skill needs its own folder in `~/.claude/skills/`, with the file renamed to `SKILL.md`:

- `slack-digest.md` → `~/.claude/skills/slack-digest/SKILL.md`
- `slack-draft.md` → `~/.claude/skills/slack-draft/SKILL.md`

Or ask Claude Code to do it: "Install these two skills from my Downloads folder."

Then run `/slack-digest` to read your messages, or `/slack-draft <what you want to say>` to draft a reply.

**Note:** the connector can't mark messages as read. Do that in the Slack app (Shift+Esc marks everything read).
