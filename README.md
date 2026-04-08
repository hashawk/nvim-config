# nvim-config

Personal Neovim configuration based on [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim), customized for Python, Go, and C development.

## Stack

**Languages:** Python, Go, C, Lua, YAML, JSON, Markdown

**LSP Servers** (auto-installed via Mason):
- `pyright` — Python
- `gopls` — Go
- `clangd` — C/C++
- `yamlls` — YAML
- `jsonls` — JSON
- `marksman` — Markdown
- `lua_ls` — Lua

**Linters:**
- `ruff` — Python
- `golangci-lint` — Go
- `yamllint` — YAML
- `jsonlint` — JSON
- `markdownlint` — Markdown

**Formatters:**
- `ruff` — Python
- `goimports` — Go
- `clang-format` — C
- `prettier` — JSON, YAML, Markdown
- `stylua` — Lua

## Key Plugins

| Plugin | Purpose |
|---|---|
| lazy.nvim | Plugin manager |
| nvim-lspconfig + Mason | LSP management and auto-install |
| blink.cmp | Autocompletion |
| nvim-treesitter | Syntax highlighting and code understanding |
| telescope.nvim | Fuzzy finder (files, grep, buffers, help) |
| conform.nvim | Autoformatting on save |
| nvim-lint | Linting |
| kanagawa.nvim | Colorscheme (wave variant) |
| mini.nvim | Statusline, surround, textobjects |
| which-key.nvim | Keybinding discovery |

## Custom Settings

- Relative line numbers with absolute on cursor line
- `Ctrl-d` / `Ctrl-u` scroll and center
- Per-language indentation via `ftplugin/` (4 spaces for Python/C, tabs for Go, 2 spaces for YAML/JSON/Lua/Markdown)
- Format on save with `<Space>f` for manual format
- System clipboard sync
- Persistent undo history across sessions

## Setup

### Prerequisites

```bash
# Fedora
sudo dnf install neovim gcc gcc-c++ make ripgrep fd-find golang nodejs npm

# macOS
brew install neovim ripgrep fd golang node
```

### Install

```bash
git clone git@github.com:hashawk/nvim-config.git ~/.config/nvim
nvim
```

On first launch, lazy.nvim bootstraps itself and installs all plugins. Mason auto-installs LSP servers, linters, and formatters. Treesitter compiles parsers. Give it a couple of minutes.

### Structure

```
~/.config/nvim/
├── init.lua                      # Main config (options, keymaps, plugins)
├── ftplugin/                     # Per-language settings
│   ├── python.lua
│   ├── go.lua
│   ├── c.lua
│   ├── yaml.lua
│   ├── json.lua
│   ├── lua.lua
│   └── markdown.lua
├── lua/
│   ├── kickstart/plugins/        # Optional kickstart extras
│   │   └── lint.lua              # Linter config (enabled)
│   └── custom/plugins/           # Personal plugin additions
└── lazy-lock.json                # Pinned plugin versions
```

## Keybinds

Leader key is `Space`. Press `Space` and wait for which-key to show available bindings.

| Key | Action |
|---|---|
| `<Space>sf` | Search files |
| `<Space>sg` | Search by grep |
| `<Space>sh` | Search help |
| `<Space>f` | Format buffer |
| `<Space>q` | Open diagnostic quickfix list |
| `gd` | Go to definition |
| `gr` | Go to references |
| `K` | Hover documentation |
| `<Space>rn` | Rename symbol |
| `<Space>ca` | Code actions |
| `Ctrl-d` | Scroll down + center |
| `Ctrl-u` | Scroll up + center |
| `Ctrl-hjkl` | Navigate splits |
| `[d` / `]d` | Previous/next diagnostic |
