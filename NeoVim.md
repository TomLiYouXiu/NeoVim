# NeoVim的配置以及使用

[xiantang/Neovim-from-scratch (github.com)](https://github.com/xiantang/Neovim-from-scratch)

## 启动
在win下中的命令号可以直接输入nvim启动

## 基本配置
linux中或者mac
~~~ base
local set = vim.o //进行配置替换
set.number = true //显示行号
set.clipboard = "unnamed" //剪切板
---复制时代码高亮---
vim.api.nvim_create_autocmd({ "TextYankPost" }, {
	pattern = { "*" },
	callback = function()
		vim.highlight.on_yank({
			timeout = 300,
		})
	end,
})
-- keybindings
local opt = { noremap = true, silent = true }
-- 此时新建窗口变成了ctrl+L 正常的方向键即可
vim.g.mapleader = " "
vim.keymap.set({ "n", "t" }, "<C-h>", "<CMD>NavigatorLeft<CR>")
vim.keymap.set({ "n", "t" }, "<C-l>", "<CMD>NavigatorRight<CR>")
vim.keymap.set({ "n", "t" }, "<C-k>", "<CMD>NavigatorUp<CR>")
vim.keymap.set({ "n", "t" }, "<C-j>", "<CMD>NavigatorDown<CR>")
vim.keymap.set("n", "<Leader>v", "<C-w>v", opt)
vim.keymap.set("n", "<Leader>s", "<C-w>s", opt)
vim.keymap.set("n", "<Leader>[", "<C-o>", opt)
vim.keymap.set("n", "<Leader>]", "<C-i>", opt)
~~~

win中
在"C:\Users{username}\AppData\Local\nvim\init.lua"进行配置
~~~base
基本同上 有什么不同的我会及时在这里进行说明
~~~
## 配置上传仓库

# 快捷键

其余的基本上都是Vim的快捷键比如
~~~
行号的跳转 :4  跳转到第四行
跳转到尾部 G
跳转到首部 g
复制一行 yy
粘贴一行 p
删除一行 dd
视图模式 v 此时可以进行多行选择
链接跳转 gx
复制到最后一行 :pu
~~~

# 插件安装与选择

## lazy.nvim（插件管理）

[folke/lazy.nvim: 💤 A modern plugin manager for Neovim (github.com)](https://github.com/folke/lazy.nvim)

~~~lua
local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
if not vim.loop.fs_stat(lazypath) then
  vim.fn.system({
    "git",
    "clone",
    "--filter=blob:none",
    "https://github.com/folke/lazy.nvim.git",
    "--branch=stable", -- latest stable release
    lazypath,
  })
end
vim.opt.rtp:prepend(lazypath)
require("lazy").setup(plugins, opts)
~~~

启动直接  :Lazy即可

## colorscheme

使用lazy安装

~~~
:Lazy install nvim-base16 
~~~

配置文件中使用

~~~lua
-- color scheme
require("lazy").setup({
	{
		"RRethy/nvim-base16",
		lazy = true,
	},
})
vim.cmd.colorscheme("base16-tender")
~~~

## telescope.nvim（）

 

#  LSP



