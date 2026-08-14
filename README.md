# Codex agents

A small catalog of general-purpose custom agents for Codex.

## Structure

```text
.
├── AGENTS.md
├── README.md
└── agents/
    ├── generalist.toml
    ├── frontend.toml
    ├── backend-node.toml
    └── devops.toml
```

- `AGENTS.md` contains optional global engineering guidelines.
- `agents/` contains one standalone Codex agent per TOML file.
- Agent filenames use lowercase kebab-case. The agent's `name` field remains its
  actual identifier in Codex.

The TOML files shown above are the planned catalog and will be added as each
agent is implemented.

## Usage options

To make every agent available only in a specific project, copy the desired TOML
files into that project's `.codex/agents/` directory.

To make agents available to a developer in every project, copy them into
`~/.codex/agents/`.

The complete catalog can be copied with `*.toml`; a single profile can be copied
by selecting only its file. Copy `AGENTS.md` to a project root for project-level
guidance or to `~/.codex/AGENTS.md` for personal global guidance.

Codex discovers only the standard `AGENTS.md` hierarchy and TOML agent files
installed under `.codex/agents/` or `~/.codex/agents/`. It does not load the
catalog directly from `agents/`. A file such as `frontend-agent.md` would be
ordinary documentation unless referenced by another instruction mechanism.
