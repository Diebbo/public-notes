---
template-version: 1.0.0
aliases: 
creation date: 2024-12-07 20:36
modification date: Saturday 7th December 2024 21:31:10
tags:
  - nvim
link: https://www.youtube.com/watch?v=MpnjYb-t12A&t=205s
---

- extracted from [[it/nvim/README|README]]
# :LiTreeDeciduous: Tree Sitter

>[!Note] Definizione
> **parser** -> tradotto in C

good *error* recovery!

already implemented in nvim: `vim.treesitter.XXX` -> we miss the updated parsers and queries

writing query in lisp syntax.


:LiCommand: `:Inspect` 

## Query

let's take this [query](https://github.com/nvim-treesitter/nvim-treesitter/blob/master/queries/lua/highlights.scm):
```lisp
(function_call
  (identifier) @function.builtin
  (#any-of? @function.builtin
    ; built-in functions in Lua 5.1
    "assert" "collectgarbage" "dofile" "error" "getfenv" "getmetatable" "ipairs" "load" "loadfile"
    "loadstring" "module" "next" "pairs" "pcall" "print" "rawequal" "rawget" "rawlen" "rawset"
    "require" "select" "setfenv" "setmetatable" "tonumber" "tostring" "type" "unpack" "xpcall"
    "__add" "__band" "__bnot" "__bor" "__bxor" "__call" "__concat" "__div" "__eq" "__gc" "__idiv"
    "__index" "__le" "__len" "__lt" "__metatable" "__mod" "__mul" "__name" "__newindex" "__pairs"
    "__pow" "__shl" "__shr" "__sub" "__tostring" "__unm"))

```

we can get the same result by having the cursor a word and calling the :LiCommand: `:InspectTree`

so by taking as an example: 
```lua
require(...).XXX
```

the list query is telling us: if you match one of the following words -> then it's a built-in

## Usage

by calling the

```lua
vim.cmd [[hi @funciton.builtin.lua guifg="yellow"]]
```
- `hi` highlights
- `guifd` These give the foreground (guifg) from :LiCommand: `:help guidf`

is changing the color of all the built-in for lua files!

## Query editor

i can get all the functions calls by:

```lisp
(funciton_call) @fn
```

![[Pasted image 20241207220324.png]]
