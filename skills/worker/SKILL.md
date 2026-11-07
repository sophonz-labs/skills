---
name: worker
description: "Use when the environment variable ST_RUN is set, or a message from st's coordinator gives you a task: you are a worker of st orchestration and report with st worker done. If your shell says st cannot be checked from it, call st through st's MCP tool st (args = the words after st)."
user-invocable: false
allowed-tools: "Bash(st *), mcp__st__st"
---

You are a worker in an st orchestration run. Your task is in the file named by
`$ST_TASK_FILE`, or in the brief st typed at you. Load your obligations first,
then what every agent using st follows (these only read, so they work in a
sandbox too):

```bash
st skills get worker
st skills get common
```

An st older than 0.4.3 answers `no guide "common"`: the worker's guide is
then all you need.

Run st from your shell. If a command there says "st cannot be checked from
this shell" (Codex's sandbox), call st through its MCP tool `st` instead, with
the guide's words: `st worker done --summary "…"` is the tool `st` with args
`["worker", "done", "--summary", "…"]`. Files you name must be in your working
directory; a command that waits returns within 10 minutes, and exit 2 means
call it again. If you have neither a shell that reaches st nor the tool, say
so in your answer: the user sets the tool up with `st hooks install`.
