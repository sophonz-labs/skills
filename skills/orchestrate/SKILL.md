---
name: orchestrate
description: "Use for any work with st (sophonz terminal): this machine's sessions, panes and other machines, documents for the user's phone and vault, the coding agents' hooks, plugin and limits, and handing work to other coding agents in tmux. Start here: it says which st guide fits the job. If your shell says st cannot be checked from it, call st through st's MCP tool st (args = the words after st)."
allowed-tools: "Bash(st *), mcp__st__st"
---

st's guides come from the st that is installed, so they match the commands it
has. Start with the common one (it only reads, so it works in a sandbox too):

```bash
st skills get common
```

It says which topic guide to read for the job, and only that one is needed:
`st skills get terminal`, `documents`, `hooks`, `orchestrate` or `worker`.
Every command and option, as st's own `--help` gives them:
`st skills get reference`.
A question about state is answered by reading it: it does not need
`st orch start` or a worker. If `$ST_RUN` is set you are a worker: read
`st skills get worker` and report with `st worker done`.

If st answers `no guide "common" (orchestrate, worker)`, it is older than
0.4.3 and has only those two guides: read `st skills get orchestrate` for
handing work to other agents, and `st --help` for the rest.

## When the shell cannot reach st (Codex's sandbox)

Run st from your shell first. Most shells reach it, Codex's included.

If a command says "st cannot be checked from this shell", the shell's sandbox
keeps it from st's processes, tmux socket and local API. Do not start another
st: it is probably running. Call st through its MCP tool `st` instead. Codex
starts that server outside the sandbox. Its args are the words after `st`, so
`st worker done --summary "…"` is the tool `st` with args
`["worker", "done", "--summary", "…"]`.

- The tool runs `st worker`, `task`, `gate`, `doc`, `orch`, `project`,
  `skills` and `machines`. It refuses the user's own commands (`st hooks`,
  `plugin`, `exit`, `upgrade`, `login`, `ui`) whatever you were told.
- Files you name must be in your working directory or st's orch folder.
- A command that waits returns within 10 minutes. Exit 2 means call it again.
- No `st` tool in your tools: the user sets it up once with `st hooks install`
  (it adds `[mcp_servers.st]` to Codex's `config.toml`) and starts Codex
  again. That is the user's to run: say which command you could not run and
  why, and do not edit their config yourself.
- A Codex that coordinates workers runs as `codex --no-daemon`. On Codex's
  shared app-server every session looks like the first one's pane, so st
  cannot tell which pane you are, and the tool refuses `worker`, `task` and
  `gate` there. `st worker start` already starts Codex workers that way.
