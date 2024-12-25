---
template-version: 1.0.0
aliases: [ ]
creation date: 2024-12-08 14:58
modification date: Sunday 8th December 2024 14:58:55
tags: [nvim  ]
---

extracted-from::[[it/nvim/README]]

# :LiFoldHorizontal: Formatting 

boring `=` cmd in vim

`:vim.lsp.buf.format` -> check as always the `help`


## Autoformatting

```lua
    vim.api.nvim_create_autocmd('LspAttach', {
      callback = function(args)
        local bufnr = args.buf
        local client = vim.lsp.get_client_by_id(args.data.client_id)
        if not client then return end

        if client.supports_method('textDocument/codeAction') then
          vim.api.nvim_create_autocmd('BufWritePre', {
            buffer = bufnr,
            callback = function()
              vim.lsp.buf.format({ bufnr = bufnr, id = client.id })
            end,
          })
        end
      end,
    })
```

- `xxx.autocmd`: 
	- `LspAttach` event is triggered when a new LSP client attaches to a buffer.
	- `BufWritePre` event is triggered before writing the buffer to disk.
- `callback`: pretty self-explanatory, it's the function that is called when the event is triggered.
- `vim.lsp.get_client_by_id(args.data.client_id)`: get the client that is attached to the buffer.


## Language specific settings

all stored in the `.editorconfig` file