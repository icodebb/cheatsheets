# RipGrep Cheatsheet

[https://github.com/BurntSushi/ripgrep](github.com/BurntSuchi/ripgrep)

## Commands

| Commands | Description |
| -------- | ----------- |
|`ripgrep --type-list` | To ind the full list of file types. |
|`rg " main\(" --type c` |To find the main() function in C file only. |
|`rg "bar" -T py` | To find exclude Python files. |
|`rg '12345' -g '*.adoc'` |This globs through all files that end with .adoc for the number. |
|`rg "double" *.[ch]` |Search the word "double" from *.c and *.h files in current folder. |
|`rg -g '!*html' "VPP"` |Search "VPP" recursively from files excludes HTML files. |
|`rg -w "whole-word-only"` |This option tells `rg` to match the search term as a whole word, same to `--word-regexp`.|

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
