# sophonz skills

The orchestration skills for coding agents, for Claude Code and Codex. One
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
| `skills/orchestrate/SKILL.md` | the coordinator: splits the work, starts workers, waits, reports |
| `skills/worker/SKILL.md` | a worker started by st (`ST_RUN` is set); reports with `st worker done` |

Each file is short on purpose. It tells the agent to load the full guide from
the `st` that is actually installed:

```sh
st skills get orchestrate
st skills get worker
```

So the guide always matches your `st`, and these files do not go stale when
`st` gains commands.

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
