---
template-version: 1.0.0
aliases: [ Terminal]
creation date: 2024-12-15 12:05
modification date: Sunday 15th December 2024 12:05:04
tags: [nvim  ]
---

extracted-from::[[it/nvim/README]]

# :LiTerminal: Terminal emulator inside nvim

`help :term`

```nvim
:new --window
:term

```

Customizable with
```lua
vim.api.create_auto_cmd('TermOpen', {
	group = vim.api.nvim_create_autogroup('custom-term-open', { clear = true })
	callback = function()
		Vim.opt.number = false, 
		Vim.opt.relative_numbers = false
	End,
)
```

we can also save the job number, and send some custom commands!

```lua
local job_id = 0
vim.keymap.set('n', '<leader>st', function()
	vim.cmd.vnew()
	vim.cmd.term()
	vim.wincmd("J")
	vim.api.nvim_win_set_height(0,5)

	job_id = vim.bo.channel
end)

vim.keymap.set('n', '<space>ex', function()
	vim.fn.chansend(job_id, { "echo 'hi' " })
end)
```

using this with `make`