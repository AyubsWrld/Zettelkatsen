```lua
return { { "neovim/nvim-lspconfig", config = function() local lspconfig = require("lspconfig") -- C++ LSP lspconfig.clangd.setup({}) -- Go lsp lspconfig.gopls.setup({}) -- TypeScript/JavaScript LSP lspconfig.tsserver.setup({ on_attach = function(client, bufnr) -- Disable formatting for tsserver (use prettier/eslint instead) client.server_capabilities.documentFormattingProvider = false end, }) end, }, }work
```
___
Tags: #neovim #lsp