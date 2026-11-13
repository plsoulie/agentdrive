---
name: handoff
description: Save or load a session handoff note in agentdrive, so the next session can continue where this one stopped. Use when the user says "handoff", "save where we are", "pick up where we left off", or ends or starts a work session.
---

# Handoff

A handoff is one Markdown file in the user's agentdrive drive. It tells the next session what happened and what is left. It uses the agentdrive MCP tools: `save_file`, `list_files`, `read_file`, `get_file_link`.

If the agentdrive tools are not available, tell the user to run `/mcp`, choose agentdrive and authenticate. They need a free drive first: https://useagentdrive.com/signin

## Save a handoff

1. Write a short Markdown note with these headings: Done, Left to do, Open questions, Files and commands that matter.
2. Keep it under one page. Leave out secrets, tokens and passwords.
3. Call `save_file` with the name `handoff-<project>-<YYYY-MM-DD>.md` and `mime_type` `text/markdown`.
4. A save is confirmed only when the result says `status=saved`. Tell the user the file name.
5. Give a file link only if the user asks for one. Anyone holding the link can read the file.

## Load a handoff

1. Call `list_files` and find the newest file whose name starts with `handoff-` for this project.
2. Call `read_file` with `encoding` `utf8`.
3. Summarize it in a few lines, then ask the user which item to start with.

Never delete a handoff unless the user asks.
