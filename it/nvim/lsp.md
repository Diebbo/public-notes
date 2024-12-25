---
tags:
  - nvim
  - lsp
---
extraced from [[it/nvim/README|README]]
#  :LiLanguages: LSP

- editor client server
- definition of what's under my curso:


## nvim integration

nvim client + api integration

`:lua vim.lsp_XXX` function

`:help vim.lsp`

what nvim needs:
- where the servers are
- when to start
- configuration ^a6847d

>[!Info] **Note**
>nvim-lspconfig **plugin**


## [configuration](#^a6847d)

`:help lspconfig-all` -> search

```lua
retrun {
	"nvim/lspconfig",
	deps = {
		{
			"folke/lazydev",
			ft = "lua",
			...
		}
	},
	config = function ()
		require('lspconfig').lua({})
	end,
}
```

>[!Info] **Note**
>folke/lazydev -> confiugre for lua in auto

ins-completion: `i_CTRL-X_CTRL-O` **omnifunc**
`CTRL-]` **tagfunc**

always hit the **help**


## 🔥Keybind
- `gnr` -> go to reference
- `grn` -> rename