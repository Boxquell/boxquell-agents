# boxquell-agents

Official agent recipes for [Boxquell](https://github.com/Boxquell/boxquell). Boxquell adds this repository by itself on first use.

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
| `herdr` | [herdr](https://github.com/herdrdev/herdr) (terminal workspace for supervising coding agents) | `herdr` |
| `gemini` | Gemini CLI | `gemini` |
| `aider` | Aider | `aider` |
| `goose` | goose (Block) | `goose` |
| `amp` | Amp (Sourcegraph) | `amp` |
| `copilot` | GitHub Copilot CLI | `copilot` |
| `cursor` | Cursor CLI | `cursor-agent` |
| `qwen` | Qwen Code | `qwen` |

The Orca server listens on port 7777 in the sandbox. Installing the recipe forwards that port from `127.0.0.1:7777` on your computer, so the pairing link it prints (`ws://127.0.0.1:7777`) works in the Orca app on the same computer. The agents Orca runs (Claude Code, Codex, …) are installed with their own recipes.

herdr has no port of its own. Install the recipe, run `boxquell ssh-config --install` once, and attach from your computer with `herdr --remote boxquell-<name>` (herdr must be installed on your computer too). Inside the sandbox, `herdr` opens it in a terminal.

To pair from another device, let the forward listen on an address that device can reach and tell Orca to advertise it:

```sh
boxquell port rm mybox 7777
boxquell port add mybox 7777 --bind 192.168.1.20        # an address of your computer
boxquell run mybox orca serve --bind 0.0.0.0 --port 7777 --pairing-address 192.168.1.20
```

Each agent recipe allows the API hosts the agent needs and names the host secrets it can use. Node.js comes from the [languages](https://github.com/Boxquell/boxquell-languages) repository.

## Contributing

One TOML file per recipe in `recipes/`. The format is described in [docs/recipes.md](https://github.com/Boxquell/boxquell/blob/main/docs/recipes.md); the workflow in this repository checks every file.

A recipe may carry `icon = "<file>.svg"` right after its `description`; the file lives in `icons/` and is a single-colour SVG under 60 KB. Icons in `icons/` come from [Simple Icons](https://simpleicons.org) (CC0), generic glyphs from [Lucide](https://lucide.dev) (ISC), and a few are the projects' own logos. The logos remain trademarks of their owners.

## License

Licensed under either of [Apache License 2.0](LICENSE-APACHE) or [MIT license](LICENSE-MIT) at your option.
