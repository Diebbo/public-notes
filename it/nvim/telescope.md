---
template-version: 1.0.0
aliases: [ ]
creation date: 2024-12-09 22:44
modification date: Monday 9th December 2024 22:44:26
tags: [nvim  ]
---

extracted-from::[[it/nvim/README]]

# :LiTelescope: Telescope

fuzzy finder for files

don't forget the `:Telescope builtin` for all function

## find files in the nvim config folder

```lua
  km.set('n', '<leader>sc', function()
	tbuiltin.find_files({
	  prompt_title = 'Search in Nvim Config',
	  cwd = vim.fn.stdpath('config'),
	})
  end, { desc = '[S]earch in nvim [C]onfig' })
```


## :LiFireExtinguisher: Binding
- `g*` for *Goto* ... with lsp
- `<leader>f` or `<leader>s` for search or file


## :LiCurlyBraces: themes

ways of open the telescope window.

