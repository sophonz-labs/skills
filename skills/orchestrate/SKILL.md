---
name: orchestrate
description: "Use when the user asks to split work across several coding agents, run agents in parallel, delegate a task to another agent and supervise it, or coordinate workers in tmux through st. Not for a single quick subagent."
allowed-tools: "Bash(st *)"
---

Coordinate other coding agents (Claude Code, Codex) through st: each worker
runs in its own tmux window, and the user can watch the delegation graph.

Before running any st orchestration command, load the guide that matches the
installed st:

```bash
st skills get orchestrate
```

Follow it exactly: st orch start, then st worker start for each worker, then
st worker wait, st worker read, and report.
