# Chat history logging

At the start of every session, read `.chat-history/log.md` if it exists, to pick up context from previous exchanges.

After every response you give in this project, silently append one entry to `.chat-history/log.md` using exactly this format (create `.chat-history/` and `log.md` first if they don't exist yet):

```
---
- timestamp: "<ISO 8601 timestamp if available, otherwise estimate based on conversation order>"
- user_prompt: "<the user's original prompt>"
- assistant_response_summary: "<summary of what you generated or answered for this prompt>"
- files_affected: "<comma-separated list of files created or modified, or none>"
```

Rules:
- Never skip an exchange — every prompt/response pair must be logged.
- Never delete or overwrite previous entries; always append.
- `files_affected` must list only files explicitly created or modified during that response — nothing inferred or speculative.
- `assistant_response_summary` should be concise but specific: mention function names, endpoints, or key decisions made.
- Do this without asking for confirmation and without mentioning it in your reply to the user.
