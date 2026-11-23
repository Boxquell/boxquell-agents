# boxquell-agents

Official agent recipes for [Boxquell](https://github.com/ToBee94/boxquell). Boxquell adds this repository by itself on first use.

```sh
boxquell recipes                      # everything that can be installed
boxquell add mybox claude
boxquell repo update agents          # fetch the latest recipes
```

## Recipes

| Recipe | Agent | Command |
|---|---|---|
| `claude` | Claude Code | `claude` |
| `codex` | Codex | `codex` |
| `opencode` | opencode | `opencode` |
| `pi` | pi | `pi` |
| `orca` | Orca server (headless runtime of the [Orca](https://github.com/stablyai/orca) desktop app) | `orca serve` |

To reach the Orca server from the Orca app on your computer, forward its port: `boxquell port add mybox 7777`, then connect the app to `127.0.0.1:7777`. The agents Orca runs (Claude Code, Codex, …) are installed with their own recipes.

Each agent recipe allows the API hosts the agent needs and names the host secrets it can use. Node.js comes from the [languages](https://github.com/ToBee94/boxquell-languages) repository.

## Contributing

One TOML file per recipe in `recipes/`. The format is described in [docs/recipes.md](https://github.com/ToBee94/boxquell/blob/main/docs/recipes.md); the workflow in this repository checks every file.

## License

Licensed under either of [Apache License 2.0](LICENSE-APACHE) or [MIT license](LICENSE-MIT) at your option.
