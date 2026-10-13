# REA kit for Claude Code

Config that gives Claude Code [REA (Reverse Engineer Anything)](https://github.com/morluto/rea),
pinned to **rea-agents 6.4.0**. This repo holds config only, not REA's source.

| File | Purpose |
| --- | --- |
| `.mcp.json` | Registers the REA MCP server (`npx -y rea-agents@6.4.0 mcp`) |
| `.claude/settings.json` | Pre-approves the `rea` server so it loads without a prompt |
| `.claude/skills/reverse-engineer-anything/` | REA's workflow skill and references from the 6.4.0 release (MIT, see its `LICENSE`) |

## Claude Code on the web

Start a session on this repo. Claude Code reads `.mcp.json` and the skill on startup.
Run `/mcp` to check that `rea` is connected.

- The environment's network policy must allow the npm registry, because the server is fetched with `npx`.
- Static JavaScript, Electron and website analysis needs no extra tools. Native-binary analysis
  also needs Ghidra, IDA or Hopper, which a cloud container doesn't have by default.
- To use REA in another repo, copy `.mcp.json`, `.claude/settings.json` and `.claude/skills/` into it.

## Your own computer

With Node.js and npm installed:

```bash
npx rea-agents@6.4.0 setup --client claude_code
```

Review the plan and approve it, then restart Claude Code. This registers REA in `~/.claude.json`
and installs the skill for all your local sessions. Check it with:

```bash
npx rea-agents@6.4.0 doctor
```

## Updating

Change the version in `.mcp.json`, and refresh the skill from the matching
[release](https://github.com/morluto/rea/releases).
