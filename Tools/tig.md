# The `tig` Tool

`tig` is an ncurses text-mode interface for Git. It browses history, inspects diffs, stages changes at hunk/line level, and can act as a pager for Git command output.

Press `h` inside tig for context-sensitive help. Defaults below match stock `/etc/tigrc` (tig 2.5+).

---

## Installation

```bash
sudo apt install tig        # Debian/Ubuntu
sudo dnf install tig        # Fedora/RHEL
sudo pacman -S tig          # Arch
brew install tig            # macOS (or: brew install tig --HEAD)
tig --version
```

---

## Invocation

| Command                 | Description                                       |
|-------------------------|---------------------------------------------------|
| `tig`                   | Main view (commit log)                            |
| `tig status`            | Status / staging view                             |
| `tig log`               | Log view (full messages + diffstat)               |
| `tig show [rev]`        | Diff view via `git show`                          |
| `tig blame FILE`        | Blame view                                        |
| `tig blame REV -- FILE` | Blame file at revision                            |
| `tig refs`              | Branches, remotes, tags                           |
| `tig stash`             | Stash list                                        |
| `tig grep [pattern]`    | Grep view (`git grep` options)                    |
| `tig reflog`            | Reflog view                                       |
| `tig master`            | History for a branch                              |
| `tig test..master`      | Commits reachable from `master` but not `test`    |
| `tig FILE`              | History that touched `FILE`                       |
| `tig -- path/`          | History for a directory                           |
| `tig v0.0.3:README`     | Blob at revision (`tig show` style)               |
| `tig -C /repo/path`     | Run as if started in `/repo/path` (like `git -C`) |
| `tig +42`               | Open first view with line 42 selected             |

You can substitute most `git log` / `git diff` option usage with `tig` — pass the same options:

```bash
tig --all --decorate --graph
tig --author="Alice"
tig --since="2024-01-01" -n100
tig --grep="fix"
tig HEAD~5..HEAD
tig a1b2c3d                   # start at / focus around a specific commit
tig test master               # commits from one or more branches
tig commit1 commit2           # revisions listed on the command line
tig master...feature          # symmetric difference (merge-base style)
tig origin..HEAD              # unpushed commits
tig --after="May 5th" --before="2006-05-16" -- README
tig --word-diff=plain
tig log -- path/to/dir        # log limited to a path
```

Separate paths from options/refs with `--` when names clash (e.g. a file named `status`):

```bash
tig -- status
```

### Pager mode

Pipe Git output into tig to colorize and browse it:

```bash
git show | tig
git log -Schange -p --raw | tig
git rev-list --author=vivien HEAD | tig show --stdin
tig --no-walk --stdin < cherry-picks.txt
git reflog --pretty=raw | tig --pretty=raw
```

---

## Core Views

| View   | Key           | Purpose                                 |
|--------|---------------|-----------------------------------------|
| Main   | `m` (default) | One-line commit history + graph/refs    |
| Diff   | `d` / `Enter` | Commit or working-tree diff             |
| Log    | `l`           | Richer log (message + diffstat)         |
| Reflog | `L`           | Reflog browser                          |
| Tree   | `t`           | Directory tree for current revision     |
| Blob   | `f`           | File contents                           |
| Blame  | `b`           | Line-level authorship                   |
| Refs   | `r`           | Branches, remotes, tags                 |
| Status | `s` / `S`     | Working tree + stage/unstage            |
| Stage  | `c`           | Hunk/line staging for selected file     |
| Stash  | `y`           | Stash list                              |
| Grep   | `g`           | Search file contents                    |
| Pager  | `p`           | Pager for stdin / prompt command output |
| Help   | `h`           | Keybinding reference                    |

Navigate *between* views rather than typing Git commands. History views are mostly read-only; staging/commit happens in **status** / **stage**.

---

## Shortcut Keys

### View switching

| Key       | Description      |
|-----------|------------------|
| `m`       | Main view        |
| `d`       | Diff view        |
| `l`       | Log view         |
| `L`       | Reflog view      |
| `t`       | Tree view        |
| `f`       | Blob (file) view |
| `b`       | Blame view       |
| `r`       | Refs view        |
| `s` / `S` | Status view      |
| `c`       | Stage view       |
| `y`       | Stash view       |
| `g`       | Grep view        |
| `p`       | Pager view       |
| `h`       | Help view        |

### View manipulation

| Key            | Description                                                                      |
|----------------|----------------------------------------------------------------------------------|
| `Enter`        | Open / drill into selection (context-sensitive; in main/log splits to show diff) |
| `Tab`          | Focus next (split) view                                                          |
| `<`            | Go back to previous view state                                                   |
| `,`            | Move to parent (tree: parent dir; blame: parent commit; merges: query parent)    |
| `O`            | Maximize current view                                                            |
| `R` / `F5`     | Reload / refresh current view                                                    |
| `q`            | Close current view (quit if last)                                                |
| `Q` / `Ctrl-C` | Close all views and quit                                                         |

### Cursor navigation

| Key                 | Description                         |
|---------------------|-------------------------------------|
| `j` / `k`           | Move down / up one line             |
| `J` / `K`           | Next / previous entry               |
| `Ctrl-N` / `Ctrl-P` | Next / previous (same as `J` / `K`) |
| `Ctrl-D` / `Ctrl-U` | Half page down / up                 |
| `PgDn` / `Space`    | Page down                           |
| `PgUp` / `-`        | Page up                             |
| `Home`              | Jump to first line                  |
| `End`               | Jump to last line                   |

> Vim-style `gg` / `G` for top/bottom are **not** default; enable via `contrib/vim.tigrc` (see Configuration).

### Scrolling

| Key              | Description                    |
|------------------|--------------------------------|
| `Ins` / `Ctrl-Y` | Scroll one line up             |
| `Del` / `Ctrl-E` | Scroll one line down           |
| `←` / `→`        | Scroll one column left / right |
| `\|`             | Scroll to first column         |

### Searching

| Key       | Description                    |
|-----------|--------------------------------|
| `/`       | Search forward (regexp prompt) |
| `?`       | Search backward                |
| `n` / `N` | Next / previous match          |

Patterns are POSIX extended regex, or PCRE/PCRE2 if built that way (`tig -v`). Case sensitivity: `ignore-case` in `~/.tigrc`. Search applies to the **current view** only.

### Option toggles

| Key | Description                                          |
|-----|------------------------------------------------------|
| `o` | Open option menu                                     |
| `I` | Toggle sort order (asc/desc)                         |
| `i` | Toggle sort field                                    |
| `#` | Toggle line numbers                                  |
| `D` | Toggle date display modes                            |
| `A` | Toggle author display modes                          |
| `G` | Toggle revision graph (main view)                    |
| `~` | Toggle line graphics                                 |
| `F` | Toggle file names / refs display (context-dependent) |
| `W` | Toggle ignore whitespace in diffs                    |
| `X` | Toggle commit ID display                             |
| `%` | Toggle file filtering (full diff vs selected file)   |
| `^` | Toggle revision filtering (main view)                |
| `$` | Toggle commit-title overflow highlight               |

### Misc actions

| Key      | Description                                    |
|----------|------------------------------------------------|
| `e`      | Open file in `$EDITOR` / `TIG_EDITOR`          |
| `:`      | Open prompt (tig commands / jump)              |
| `H`      | Go to HEAD commit (main view)                  |
| `z`      | Stop background loading                        |
| `v`      | Show tig version                               |
| `Ctrl-L` | Redraw screen                                  |
| `C`      | Context-dependent external command (see below) |

### Main view

| Key     | Description                                     |
|---------|-------------------------------------------------|
| `Enter` | Split and show commit diff                      |
| `C`     | Cherry-pick selected commit (`git cherry-pick`) |
| `H`     | Jump to HEAD                                    |
| `G`     | Toggle commit graph                             |
| `F`     | Toggle refs (tags/branches) in titles           |

### Status view

| Key     | Description                                        |
|---------|----------------------------------------------------|
| `u`     | Stage / unstage file (also add untracked)          |
| `!`     | Revert / discard unstaged changes in file          |
| `C`     | Commit staged changes (`git commit`, opens editor) |
| `M`     | Resolve conflicts with `git mergetool`             |
| `Enter` | Open stage view for selected file                  |

**Commit workflow:** stage with `u` → press `C` → edit message → save/quit editor.

### Stage view

| Key       | Description                                                   |
|-----------|---------------------------------------------------------------|
| `u`       | Stage / unstage current hunk (or whole diff if not on a hunk) |
| `1`       | Stage / unstage single line                                   |
| `2`       | Stage / unstage part of a chunk                               |
| `\`       | Split current diff hunk                                       |
| `@`       | Jump to next hunk (`/^@@`)                                    |
| `!`       | Revert current hunk                                           |
| `[` / `]` | Decrease / increase diff context                              |

### Diff / pager views

| Key       | Description                        |
|-----------|------------------------------------|
| `@`       | Jump to next hunk                  |
| `[` / `]` | Decrease / increase diff context   |
| `Enter`   | In diff view: scroll one line down |

### Tree / blob / blame

| Key     | Description                                                       |
|---------|-------------------------------------------------------------------|
| `Enter` | Tree/blob: open file; blame: show that line’s commit              |
| `,`     | Parent directory (tree) or blame parent commit (blame)            |
| `b`     | Blame selected file (from tree/blob)                              |
| `e`     | Edit file                                                         |
| `t`     | Open tree for current revision (from main/log)                    |
| `l`     | Switch to log view (file history context when opened from a path) |

Open blame from the shell with `tig blame file.go`, or press `t` in main then `b` on a file.

### Refs view

| Key     | Description                              |
|---------|------------------------------------------|
| `Enter` | Open / enter selected ref                |
| `C`     | Check out selected branch                |
| `!`     | Delete selected branch (`git branch -D`) |

### Reflog view

| Key | Description                                                      |
|-----|------------------------------------------------------------------|
| `C` | Check out selected entry                                         |
| `!` | Hard reset to selected commit (`git reset --hard`) — destructive |
| `F` | Toggle refs display                                              |

### Stash view

| Key | Description          |
|-----|----------------------|
| `A` | Apply selected stash |
| `P` | Pop selected stash   |
| `!` | Drop selected stash  |

---

## Prompt (`:`)

| Command              | Description                        |
|----------------------|------------------------------------|
| `:80`                | Jump to line 80                    |
| `:2f12bcc`           | Jump to commit                     |
| `:q`                 | Run keybinding `q`                 |
| `:!git log -p`       | Run system command in pager        |
| `:edit`              | Run tig action                     |
| `:goto %(commit)^2`  | Jump to revision (e.g. 2nd parent) |
| `:goto some/branch`  | Jump to branch tip                 |
| `:save-display FILE` | Save current display               |
| `:save-options FILE` | Save current options               |
| `:script FILE`       | Run commands from file             |
| `:echo …`            | Show text in status bar            |
| `:source ~/.tigrc`   | Reload config (common custom bind) |

---

## Configuration (`~/.tigrc`)

Also: `$XDG_CONFIG_HOME/tig/config`. System defaults: `/etc/tigrc`.

### Useful settings

```ini
set mouse = yes
set wrap-lines = no
set ignore-case = smart-case
set start-on-head = yes
set refresh-mode = auto
set vertical-split = auto
set split-view-height = 67%
set show-author = yes
set show-date = yes
```

### Colors

```ini
color diff-add green default
color diff-del red default
```

### Custom key bindings

```ini
bind generic q quit
bind diff w :toggle ignore-space
bind generic S :source ~/.tigrc          # reload config
bind generic + !git commit --amend
bind generic 9 @sh -c "echo -n %(commit) | xclip -selection c"
bind refs 3 !git rebase -i %(branch)
bind main B ?git checkout -b "%(prompt Enter new branch name: )"
```

External-command flags: `!` run in foreground, `@` background/no output, `?` confirm first, `<` exit tig after, `>` reopen tig after.

### Vim-style bindings

```bash
# From the tig package examples:
cp /usr/share/doc/tig/examples/vim.tigrc ~/.tigrc.vim
echo 'source ~/.tigrc.vim' >> ~/.tigrc
```

That adds `gg`/`G`, hjkl scrolling, etc.

### Mouse

There is no `tig --mouse` flag; enable in config:

```ini
set mouse = yes
set mouse-scroll = 3
```

---

## Environment variables

| Variable         | Purpose                                         |
|------------------|-------------------------------------------------|
| `TIGRC_USER`     | User config path                                |
| `TIGRC_SYSTEM`   | System config path (empty = built-in only)      |
| `TIG_DIFF_OPTS`  | Extra diff options for diff view                |
| `TIG_LS_REMOTE`  | Command for listing refs (like `git ls-remote`) |
| `TIG_EDITOR`     | Editor for visiting files                       |
| `TIG_TRACE`      | Trace file for Git commands                     |
| `TIG_SCRIPT`     | Startup script of prompt/key commands           |
| `TIG_NO_DISPLAY` | No terminal rendering (testing)                 |

State variables usable in binds: `%(commit)`, `%(file)`, `%(branch)`, `%(stash)`, `%(lineno)`, `%(prompt …)`, `%(repo:head)`, and more — see `man tigmanual`.

---

## Common workflows

### Investigate a regression

1. `tig`
2. `/bug` (search message)
3. `Enter` (diff)
4. `@` next hunk; `[` / `]` adjust context

### Review folder or file history

```bash
tig -- src/module/
tig -- path/to/file.go
```

### Pre-commit review / stage

```bash
tig status
# u to stage, Enter + u/1/\ for hunk/line staging, C to commit
```

### Compare branches

```bash
tig test..master
tig master...feature
```

### Blame then jump to commit

```bash
tig blame file.go
# Enter on a line → commit; , for parent blame
```

### Git alias

```bash
git config --global alias.tig '!tig'
```

---

## Limitations / tips

* History browsing is read-only; mutate via status/stage or custom `bind` shell commands.
* No interactive rebase UI built in (bind `git rebase -i` yourself).
* Directory rename history is limited by Git.
* Pass option arguments attached (`tig -Sfoo`, `tig --grep=foo`) so values are not parsed as revisions.
* Press `h` anytime; search help with `/`.
* Stock keys differ from some online “vim-ish” cards: top/bottom are `Home`/`End` (not `gg`/`G`); whitespace is `W` (not `w`); stage/unstage is `u` and commit is `C` (not `s`/`c`); refresh is `R`/`F5` (not `r`); next hunk is `@` (`[`/`]` change context). Use `contrib/vim.tigrc` if you want vim-style motion.

---

## Links

* [DevHints tig cheatsheet](https://devhints.io/tig)
* [Official manual](https://jonas.github.io/tig/doc/manual.html)
* [jonas/tig](https://github.com/jonas/tig)
* Local: `man tig`, `man tigmanual`, `man tigrc`
