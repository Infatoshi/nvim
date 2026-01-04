# NeoVim Configuration

Minimal NeoVim 0.11+ configuration with LSP, completion, and fuzzy finding.

## Requirements

- NeoVim 0.11+
- Git
- A Nerd Font (for icons)
- ripgrep (for Telescope live grep)

## Installation

```bash
git clone https://github.com/Infatoshi/nvim.git ~/.config/nvim
nvim
```

Lazy.nvim will auto-install on first launch. Mason will install configured LSP servers.

## Structure

```
~/.config/nvim/
  init.lua           -- Core settings, keymaps, lazy.nvim bootstrap
  lua/plugins/
    init.lua         -- Plugin specifications
```

## Key Bindings

Leader key: `Space`

| Key | Action |
|-----|--------|
| `<leader>ff` | Find files |
| `<leader>fg` | Live grep |
| `<leader>fb` | Buffers |
| `<leader>fh` | Help tags |
| `gd` | Go to definition |
| `gr` | Find references |
| `K` | Hover documentation |
| `<leader>rn` | Rename symbol |
| `<leader>ca` | Code action |
| `<leader>q` | Diagnostic list |
| `<C-h/j/k/l>` | Window navigation |

## Plugins

- **lazy.nvim** - Plugin manager
- **tokyonight.nvim** - Colorscheme
- **nvim-treesitter** - Parser installation (0.11+ has built-in highlighting)
- **telescope.nvim** - Fuzzy finder
- **mason.nvim** - LSP server installer
- **nvim-lspconfig** - LSP configuration (lua_ls, pyright, rust_analyzer)
- **nvim-cmp** - Autocompletion
- **gitsigns.nvim** - Git integration
- **lualine.nvim** - Status line
- **Comment.nvim** - Comment toggling (gcc)
- **nvim-autopairs** - Auto-close brackets

---

## For LLMs

If you are an AI assistant helping with this NeoVim configuration:

### File Locations
- Core config: `init.lua` - settings, options, keymaps, lazy.nvim bootstrap
- Plugins: `lua/plugins/init.lua` - all plugin specs in one file

### Adding a Plugin
Add a new table entry to the return table in `lua/plugins/init.lua`:
```lua
{
  "author/plugin-name",
  opts = {},  -- or use config = function() ... end for complex setup
},
```

### Adding a Keymap
Add to `init.lua` after the "Basic keymaps" section:
```lua
vim.keymap.set("n", "<leader>xx", function() ... end, { desc = "Description" })
```

### Adding an LSP Server
1. Add server name to `ensure_installed` in mason-lspconfig spec
2. Add `vim.lsp.config("server_name", {})` in nvim-lspconfig config
3. Add `vim.lsp.enable("server_name")`

### API Notes
- This config uses NeoVim 0.11+ APIs: `vim.lsp.config()`, `vim.lsp.enable()`
- Treesitter highlighting is built-in; the plugin is only for parser installation
- OSC 52 clipboard is configured for SSH/remote usage

### Do Not
- Add lazy-lock.json to commits (gitignored)
- Use deprecated APIs (vim.lsp.start_client, require("lspconfig").server.setup)
- Over-complicate - this config intentionally stays minimal
