# RipGrep Cheatsheet

[https://github.com/BurntSushi/ripgrep](github.com/BurntSuchi/ripgrep)

## Commands

### General

| Commands                  | Description                                                                               |
| ------------------------- | ----------------------------------------------------------------------------------------- |
| `ripgrep --type-list`     | To ind the full list of file types.                                                       |
| `rg " main\(" --type c`   | To find the main() function in C file only.                                               |
| `rg "bar" -T py`          | To find exclude Python files.                                                             |
| `rg '12345' -g '*.adoc'`  | This globs through all files that end with .adoc for the number.                          |
| `rg "double" *.[ch]`      | Search the word "double" from *.c and *.h files in current folder.                        |
| `rg -g '!*html' "VPP"`    | Search "VPP" recursively from files excludes HTML files.                                  |
| `rg -w "whole-word-only"` | This option tells `rg` to match the search term as a whole word, same to `--word-regexp`. |
|                           |                                                                                           |

### Options

|Option|Short|Behavior|When to Use|Example|
|---|---|---|---|---|
|`--smart-case`|—|Case-insensitive if pattern is lowercase; case-sensitive if it contains uppercase|General coding workflow (recommended default)|`rg --smart-case foo`|
|`--ignore-case`|`-i`|Always case-insensitive|When case distinctions never matter|`rg -i foo`|
|`--case-sensitive`|`-s`|Always case-sensitive|Searching exact identifiers / symbols|`rg -s Foo`|
|`--fixed-strings`|`-F`|Treat pattern as literal string (no regex)|Faster exact text search|`rg -F foo.bar`|
|`--word-regexp`|`-w`|Match whole words only|Avoid partial matches like `foobar`|`rg -w foo`|
|`--glob`|—|Include or exclude specific file patterns|Limit search to certain file types|`rg foo --glob "*.go"`|
|`--hidden`|—|Search hidden files|Include dotfiles|`rg foo --hidden`|
|`--no-ignore`|—|Ignore `.gitignore` and ignore rules|Search everything|`rg foo --no-ignore`|
|`--vimgrep`|—|Output format compatible with Vim quickfix|For use with `:grep` in Neovim|`rg --vimgrep foo`|

## Cheatsheet

- [Ripgrep Cheatsheet](https://www.philipdaniels.com/blog/2019/ripgrep-cheatsheet/) - Phi'ls Blog
- [ripgrep Cheat Sheet) by njones (PDF downloaded](https://cheatography.com/njones/cheat-sheets/ripgrep/)
- [Ripgrep Cheat Sheet](https://devpoga.org/post/2019-09-20_ripgrep_cheat_sheet/) - Dev.Poga short list

## Links

- [Ripgrep cheatsheet](https://skerritt.blog/ripgrep-cheatsheet/) - skerritt.blog
- [How to Use `ripgrep` to Improve Your Search Efficiency](https://earthly.dev/blog/ripgrep-for-efficient-search/)
- [Using ripgrep (rg) Command in Linux](https://linuxhandbook.com/ripgrep/?ref=itsfoss.com) - Linux Handbook
- [Fast Searching with ripgrep](https://mariusschulz.com/blog/fast-searching-with-ripgrep)
- [BurnSushi/ripgreg/Guide](https://github.com/BurntSushi/ripgrep/blob/master/GUIDE.md)
- [How to Use `ripgrep` to Improve Your Search Efficiency](https://earthly.dev/blog/ripgrep-for-efficient-search/)
- [Try / ripgrep in Y minutes](https://codapi.org/try/ripgrep/)
  - With examples can be run in the web page.
  - rg provides a limited ability to replace matched text
