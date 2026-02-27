# Neovim

## Installation

### Windows

- Use nvim-win64.msi.
- RC file location: /c/Users/iliu/AppData/Local/nvim/init.vim
- [Guide - How to Customize Your Vim Code Editor with Mappings, Vimscript, Status Line, and More](https://www.freecodecamp.org/news/vimrc-configuration-guide-customize-your-vim-editor/)
- [simonista/.vimrc](https://gist.github.com/simonista/8703722)

## Plug-ins

- [Neorg](https://github.com/nvim-neorg/neorg) - It's .norg but not .org file.
- [Vim-OrgMode](https://github.com/jceb/vim-orgmode) - No more maintain?


## Intro

Thanks to the author of [original doc](https://gist.github.com/angeloanan/a3b8d2a1e5c14bae840f586a6b394ecb), copied and made modifications.

*WARNING*: Most commands are case sensitive and modifier sensitive!

> * `w` means pressing `W` key
> * `W` means pressing `SHIFT` and `W` together (Capitalization!)
> * `^` means pressing `CTRL` ignoring capitalization; `^W` means `CTRL + w` WITHOUT SHIFT

## Basics

Cursor movement: Arrow keys or `hjkl`, preferably maximize `hjkl`

```text
h     l
left  right

j     k
down  up
```

----

* `w` - jump to next word before punctuation
* `W` - jump to next word
* `b` - jump to previous word before punctuation
* `B` - jump to previous word

----

* `gg` - jump to start / beginning of file
* `G` - jump to end of file (eof)

----

On VISUAL (`v`) or VISUAL-LINE `V` mode

* `>` - indent to the right
* `<` - indent to the left

----

Find / Fuzzy / Regex / Regular Expression

* `/` - Start finding stuff with Regex, end with Enter
* `n` - Find next result
* `N` - Find previous result

Replace - Highlight things that want to be replaced using Visual mode then

* `:s/<findterm>/<replaceterm>`

## Windows

* `^W` then movement keys to focus / highlight different window (pop-up help shows)
* `^W w` to switch windows
* `:sp` or `^W s` to open new window below (split horizontally)
* `:vsplit` or `^W v` to open new window to the right (split vertically)
* `^W h` to the window on the left (the file list)
* `^W l` to the window on the right (the file content)

----

Note, you can prefix these with numbers

* `^W >` - enlarges window size
* `^W <` - make window size smaller
* ??? - minimize window (idt its even possible)

## File / Word Finder (Telescope)

`:Telescope find_files` = `<Space> sf` Search files
`:Telescope ` = `<Space> sg` Search grep

## Embedded terminal

TBH just spawn a new tab / new window on your native terminal. Its not worth it.

Make a new window, run `:terminal` then enter Insert mode.
To make the terminal stop eating your input, switch to another window or `CTRL + \` `CTRL + N`

## LSP - Intellisense, Language Server, etc

* `<SPACE>rn` - Rename Symbol, VSCode's F2 (`vim.lsp.buf.rename`)
* `<SPACE>ca` - Code Action, VSCode's CTRL + `.` (`vim.lsp.buf.code_action`)
* `<SPACE>e` - Show errors / warning / diagnostics / codelens pop up on cursor (`vim.diagnostic.open_float`)
* `<SPACE>q` - List all errors / diagnostic / warning / codelens on bottom | VSCode's Problems panel (`vim.diagnostic.setloclist`)
* `gd` - Go to Definition (`vim.lsp.buf.definition`)
* `gr` - Go to References (`require('telescope.builtin').lsp_references`)
* `K` - Show hover information (`vim.lsp.buf.hover`) 
* `gcc` - Go Comment Line
* `gcb` - Go Comment Block - Try this if you're on React / Astro

### nvim-tree - File tree sidebar

Sidebar would need to be focused. If accidentally closed, run `:NvimTreeOpen`

* `g?` - Toggle help
* `a` - Create new file
  * Append an extra `/` to create a directory

## Links

* [Vim Cheat Sheet](https://vim.rtorr.com/)
* [Simple Neovim Cheatsheet](https://www.shortcutfoo.com/app/dojos/neovim/cheatsheet)
