# sophonz skills

The skills that teach a coding agent st, for Claude Code and Codex: this
machine's sessions and panes, your other machines, documents for your phone
and vault, the agents' hooks and limits, and orchestration. One
agent coordinates others — each worker a real Claude Code or Codex session in
its own tmux window, on this machine or another of your machines — and you can
watch and step in from the desktop app, a browser or your phone.

```sh
npx skills@1.7.2 add https://github.com/sophonz-labs/skills \
  --skill orchestrate --skill worker --global sophonz
```

Or, if you already have `st`, the same two skills come from the binary:

```sh
st plugin install      # also installs them for Codex
st plugin status
```

## What is here

| Skill | For |
|---|---|
| `skills/orchestrate/SKILL.md` | the way in for any work with st; sends the agent to the guide for the job |
| `skills/worker/SKILL.md` | a worker started by st (`ST_RUN` is set); reports with `st worker done` |

Each file is short on purpose. It tells the agent to load the full guide from
the `st` that is actually installed:

| Guide | For |
|---|---|
| `st skills get common` | where to start; rules for every job; reaching st from a sandbox |
| `st skills get terminal` | sessions, windows, panes, sharing, other machines |
| `st skills get documents` | leaving and finding documents, messages and briefs to a worker |
| `st skills get hooks` | the agents' hooks, st's plugin and skills, plan limits |
| `st skills get orchestrate` | handing work to other agents and supervising them |
| `st skills get worker` | a worker's duties |

The topic guides come with st 0.4.3. An older st has only `orchestrate` and
`worker`, and the skills fall back to those.

So the guide always matches your `st`, and these files do not go stale when
`st` gains commands.

## Codex in a sandbox

Codex's sandbox can keep its shell from reaching st (processes, the tmux
socket, the local API). st then says "st cannot be checked from this shell",
and the skills tell Codex to call st through st's MCP server instead, which
Codex starts outside the sandbox. Set it up once:

```sh
st hooks install
```

That adds `[mcp_servers.st]` to `~/.codex/config.toml` (one tool, `st`, that
runs st's orchestration and document commands and refuses the rest) and turns
off Codex's shared app-server, so each Codex window is its own pane. Start
Codex again afterwards. A Codex that coordinates workers runs as
`codex --no-daemon`.

## It needs st

`st` is what runs the workers. Without it the skills have nothing to call.

```sh
curl -fsSL https://dl.sophonz.io/install.sh | sh     # macOS, Linux
irm https://dl.sophonz.io/install.ps1 | iex          # Windows
```

More: <https://www.sophonz.io/docs/orchestrate/overview>

## Licence

The two `SKILL.md` files in this repository are MIT (see `LICENSE`). `st`
itself, the guides it prints, and the sophonz apps are not covered by it.
