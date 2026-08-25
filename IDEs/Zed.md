# Zed Editor Cheatsheet

> **Config note:** `base_keymap` is set to **Emacs**, with heavy custom overrides.
> Keys use the notation: `ctrl` = Control, `cmd` = Super/Meta (often mapped to Alt or Win on Linux), `alt` = Alt.

---

## Table of Contents

1. [File & Workspace](#1-file--workspace)
2. [Navigation — Cursor Movement](#2-navigation--cursor-movement)
3. [Selection](#3-selection)
4. [Editing & Deletion](#4-editing--deletion)
5. [Search & Replace](#5-search--replace)
6. [Code Intelligence (LSP / Xref)](#6-code-intelligence-lsp--xref)
7. [Code Actions & Refactoring](#7-code-actions--refactoring)
8. [Folding & Outline](#8-folding--outline)
9. [Git & Diagnostics](#9-git--diagnostics)
10. [Pane & Tab Management](#10-pane--tab-management)
11. [Workspace & Docks](#11-workspace--docks)
12. [Project Panel](#12-project-panel)
13. [Outline Panel](#13-outline-panel)
14. [Buffer Search Bar](#14-buffer-search-bar)
15. [Terminal](#15-terminal)
16. [AI / Agent](#16-ai--agent)
17. [Completion Menu](#17-completion-menu)
18. [Command Palette](#18-command-palette)
19. [Settings Reference](#19-settings-reference)

---

## 1. File & Workspace

| Keybinding      | Action                                   |
|-----------------|------------------------------------------|
| `ctrl-x ctrl-f` | Open file finder (fuzzy find)            |
| `ctrl-x ctrl-s` | Save current file                        |
| `ctrl-x ctrl-w` | Save As                                  |
| `cmd-t`         | New file (in workspace/terminal context) |
| `ctrl-x p p`    | Open recent projects                     |
| `ctrl-x p f`    | File finder (project scope)              |
| `ctrl-x p i`    | Project symbols                          |
| `ctrl-x p s`    | New project-wide search                  |
| `ctrl-x p m`    | Show diagnostics panel                   |
| `cmd-shift-t`   | Reopen last closed tab                   |

---

## 2. Navigation — Cursor Movement

### Line & Document

| Keybinding         | Action                     |
|--------------------|----------------------------|
| `ctrl-a` / `cmd-a` | Move to beginning of line  |
| `ctrl-e` / `cmd-e` | Move to end of line        |
| `cmd-<`            | Move to beginning of file  |
| `cmd->`            | Move to end of file        |
| `cmd-[`            | Move to start of paragraph |
| `cmd-]`            | Move to end of paragraph   |

### Character & Word

| Keybinding     | Action                      |
|----------------|-----------------------------|
| `ctrl-b`       | Move left (one character)   |
| `ctrl-f`       | Move right (one character)  |
| `cmd-b`        | Move to previous word start |
| `cmd-f`        | Move to next word end       |
| `ctrl-v`       | Page down (centers cursor)  |
| `ctrl-shift-v` | Page up (centers cursor)    |

### Line Transposition

| Keybinding | Action                 |
|------------|------------------------|
| `cmd-up`   | Move current line up   |
| `cmd-down` | Move current line down |

### Jump Navigation

| Keybinding | Action                       |
|------------|------------------------------|
| `ctrl-c g` | Go to line number            |
| `ctrl-m`   | Move to enclosing bracket    |
| `cmd-,`    | Go back (navigation history) |
| `ctrl--`   | Go back (pane history)       |
| `ctrl-_`   | Go forward (pane history)    |

---

## 3. Selection

### Basic Selection

| Keybinding     | Action                      |
|----------------|-----------------------------|
| `ctrl-x h`     | Select all                  |
| `cmd-l`        | Select current line         |
| `ctrl-shift-a` | Select to beginning of line |
| `ctrl-shift-e` | Select to end of line       |
| `ctrl-cmd-<`   | Select to beginning of file |
| `ctrl-cmd->`   | Select to end of file       |

### Word & Paragraph Selection

| Keybinding    | Action                        |
|---------------|-------------------------------|
| `cmd-shift-b` | Select to previous word start |
| `cmd-shift-f` | Select to next word end       |
| `cmd-{`       | Select to start of paragraph  |
| `cmd-}`       | Select to end of paragraph    |

### Direction Selection

| Keybinding     | Action                    |
|----------------|---------------------------|
| `ctrl-shift-p` | Extend selection upward   |
| `ctrl-shift-n` | Extend selection downward |
| `ctrl-shift-b` | Extend selection left     |
| `ctrl-shift-f` | Extend selection right    |

### Syntax-Aware Selection

| Keybinding     | Action                     |
|----------------|----------------------------|
| `ctrl-=`       | Select larger syntax node  |
| `ctrl-shift-=` | Select smaller syntax node |

### Multi-cursor Selection

| Keybinding | Action |
|---|---|
| `ctrl-<` | Select previous occurrence (add cursor) |
| `ctrl->` | Select next occurrence (add cursor) |

---

## 4. Editing & Deletion

### Deletion

| Keybinding | Action |
|---|---|
| `ctrl-d` | Delete character forward |
| `ctrl-k` | Cut to end of line (kill line) |
| `ctrl-backspace` | Delete to previous subword start |
| `cmd-backspace` | Delete to previous subword start |
| `cmd-d` | Delete to next subword end |
| `cmd-space` | Delete to next subword end |

### Cut / Copy / Paste

| Keybinding | Action |
|---|---|
| `ctrl-w` | Cut selection |
| `ctrl-y` | Paste |
| `cmd-w` *(Pane context)* | Copy |

### Line Operations

| Keybinding | Action |
|---|---|
| `ctrl-j` | Join lines |
| `cmd-shift-up` | Duplicate line upward |
| `cmd-shift-down` | Duplicate line downward |
| `ctrl-c d` | Duplicate line down |

### Indentation

| Keybinding | Action |
|---|---|
| `ctrl-cmd-[` | Outdent |
| `ctrl-cmd-]` | Indent |

### Comments

| Keybinding | Action |
|---|---|
| `cmd-;` | Toggle line comment (no cursor advance) |

### Undo / Redo

| Keybinding | Action |
|---|---|
| `ctrl-/` | Undo |
| `ctrl-shift-/` | Redo |

### Format

| Keybinding | Action |
|---|---|
| `ctrl-cmd-\` | Format document |

---

## 5. Search & Replace

### In-buffer Search

| Keybinding | Action | Context |
|---|---|---|
| `ctrl-s` | Open buffer search | Editor |
| `ctrl-r` | Open buffer search | Editor |
| `ctrl-shift-s` | New project-wide search | Editor |
| `ctrl-shift-r` | New project-wide search | Editor |
| `ctrl-g` | Cancel / dismiss | Editor |

### Search Bar Controls

| Keybinding | Action |
|---|---|
| `enter` | Select next match |
| `ctrl-s` / `ctrl-n` | Select next match |
| `ctrl-r` / `ctrl-p` | Select previous match |
| `ctrl-a` | Select all matches |
| `ctrl-g` | Dismiss search bar |
| `cmd-c` | Toggle case-sensitive |
| `cmd-w` | Toggle whole-word |
| `cmd-r` | Toggle regex mode |
| `↑` | Previous search history |
| `↓` | Next search history |

---

## 6. Code Intelligence (LSP / Xref)

| Keybinding | Action |
|---|---|
| `cmd-.` | Go to definition |
| `cmd-shift-.` | Go to definition (split pane) |
| `cmd-?` | Find all references |
| `ctrl-c ctrl-d` | Show hover documentation |
| `ctrl-\\` | Show inline AI completion |

---

## 7. Code Actions & Refactoring

| Keybinding      | Action                   |
|-----------------|--------------------------|
| `ctrl-c ctrl-a` | Toggle code actions menu |
| `ctrl-;`        | Rename symbol (iedit)    |

---

## 8. Folding & Outline

| Keybinding     | Action                   |
|----------------|--------------------------|
| `ctrl-c [`     | Fold region              |
| `ctrl-c ]`     | Unfold lines             |
| `ctrl-c o`     | Toggle outline panel     |
| `ctrl-shift-o` | Toggle the Modal Outline |

---

## 9. Git & Diagnostics

| Keybinding                         | Action                            |
|------------------------------------|-----------------------------------|
| `ctrl-shift-p`, `git: **`          | Git commands                      |
| `ctrl-shift-p`, `git graph:open`   | Toggle git history view           |
| `ctrl-shift-p`, `git panel:toggle` | Toggle git panel                  |
| `ctrl-c n`                         | Go to next hunk                   |
| `ctrl-c p`                         | Go to previous hunk               |
| `ctrl-c r`                         | Reveal file in file manager       |
| `ctrl-c ctrl-l`                    | Open diagnostics panel            |
| `ctrl-c ctrl-n`                    | Go to next diagnostic             |
| `ctrl-c ctrl-p`                    | Go to previous diagnostic         |
| `ctrl-x p m`                       | Diagnostics panel (project scope) |

---

## 10. Pane & Tab Management

### Pane Splitting

| Keybinding | Action                         |
|------------|--------------------------------|
| `ctrl-x 2` | Split pane horizontally (down) |
| `ctrl-x 3` | Split pane vertically (right)  |
| `ctrl-x o` | Activate next pane             |
| `ctrl-x 0` | Close active pane item         |
| `ctrl-x 1` | Maximize / toggle zoom         |

### Tab Switching

| Keybinding        | Action                     |
|-------------------|----------------------------|
| `ctrl-x b`        | Previous tab               |
| `ctrl-x f`        | Next tab                   |
| `ctrl-x k`        | Close active tab           |
| `ctrl-tab`        | Tab switcher               |
| `ctrl-shift-tab`  | Tab switcher (select last) |
| `cmd-1` … `cmd-9` | Switch to tab 1–9          |
| `cmd-0`           | Switch to last tab         |

---

## 11. Workspace & Docks

| Keybinding | Action |
|---|---|
| `ctrl-x ctrl-x` | Toggle command palette |
| `cmd-ctrl-b` | Toggle left dock |
| `cmd-ctrl-r` | Toggle right dock |
| `cmd-ctrl-j` | Toggle bottom dock |
| `cmd-ctrl-w` | Close all docks |
| `cmd-\`` | Toggle terminal panel focus |
| `cmd-ctrl-o` | Toggle outline panel focus |
| `cmd-ctrl-t` | Project symbols |

---

## 12. Project Panel

| Keybinding | Action |
|---|---|
| `enter` | Collapse selected entry |
| `space` | Expand selected entry |
| `ctrl-n` | Select next item |
| `ctrl-p` | Select previous item |
| `cmd-n` | New file |
| `alt-cmd-n` | New directory |
| `ctrl-w` | Cut |
| `alt-w` | Copy |
| `ctrl-y` | Paste |
| `backspace` / `delete` | Move to trash (with prompt) |
| `cmd-backspace` / `cmd-delete` | Delete permanently (with prompt) |
| `cmd-r` | Reveal in file manager |
| `alt-shift-f` | New search in directory |
| `escape` | Cancel |

---

## 13. Outline Panel

| Keybinding | Action |
|---|---|
| `enter` | Collapse selected entry |
| `space` | Expand selected entry |
| `ctrl-n` | Select next item |
| `ctrl-p` | Select previous item |
| `ctrl-o` | Open selected entry |
| `cmd-w` | Copy path |
| `cmd-shift-w` | Copy relative path |
| `cmd-r` | Reveal in file manager |

---

## 14. Buffer Search Bar

*(Active when the search bar is focused)*

| Keybinding | Action |
|---|---|
| `enter` / `ctrl-s` / `ctrl-n` | Next match |
| `ctrl-r` / `ctrl-p` | Previous match |
| `ctrl-a` | Select all matches |
| `ctrl-g` | Dismiss |
| `cmd-c` | Toggle case-sensitive |
| `cmd-w` | Toggle whole-word |
| `cmd-r` | Toggle regex |
| `↑` / `↓` | Previous / next search history |

---

## 15. Terminal

| Keybinding | Action |
|---|---|
| `cmd-\`` | Toggle terminal panel |
| `cmd-t` | New terminal |
| `cmd-!` | Toggle bottom dock |
| `ctrl-v` | Scroll up (page up) |
| `ctrl-shift-v` | Scroll down (page down) |
| `cmd-b` | Word backward (`Alt-b` in shell) |
| `cmd-f` | Word forward (`Alt-f` in shell) |
| `alt-w` | Copy selection |
| `ctrl-y` | Paste |
| `cmd-k` | Clear terminal |
| `ctrl-c` | Send `Ctrl-C` (interrupt) |
| `ctrl-z` | Send `Ctrl-Z` (suspend) |

**Terminal settings:**
- Docked at **bottom**
- `copy_on_select`: enabled
- Cursor shape: **bar**
- Minimum contrast: 45.0

---

## 16. AI / Agent

### Inline Assistant (Editor)
| Keybinding | Action |
|---|---|
| `ctrl-\\` | Show inline AI completion (Copilot) |

### Agent Panel Settings
| Setting | Value |
|---|---|
| Inline assistant model | `copilot_chat` / `claude-opus-4.5` |
| Default agent model | `copilot_chat` / `gpt-4o` |
| Edit predictions provider | `copilot` |
| Default profile | `ask` |
| Sound when done | `always` |
| Single file review | enabled |

---

## 17. Completion Menu

*(Active when completions or code actions are showing)*

| Keybinding | Action |
|---|---|
| `↑` / `ctrl-p` | Previous item |
| `↓` / `ctrl-n` | Next item |
| `alt-<` | First item |
| `alt->` | Last item |

---

## 18. Command Palette

| Keybinding | Action |
|---|---|
| `ctrl-x ctrl-x` | Toggle command palette |

> Tip: Type any action name to fuzzy-find it, e.g. `"theme"`, `"restart lsp"`, `"open default settings"`.

---

## 19. Settings Reference

### Editor Behavior

| Setting | Value | Notes |
|---|---|---|
| `base_keymap` | `Emacs` | All Emacs bindings as the base |
| `vim_mode` | `false` | Vim mode disabled |
| `format_on_save` | `on` | Auto-format on save |
| `soft_wrap` | `editor_width` | Wrap at editor edge |
| `preferred_line_length` | `89` | Target line length |
| `tab_size` | `4` | 4-space indentation |
| `show_whitespaces` | `all` | Always show whitespace chars |
| `scroll_beyond_last_line` | `vertical_scroll_margin` | Allows a little past last line |
| `use_smartcase_search` | `true` | Case-insensitive unless uppercase used |

### UI & Appearance

| Setting | Value |
|---|---|
| Theme (dark) | `One Dark` |
| Theme (light) | `One Light` |
| Icon theme (dark) | `Catppuccin Frappé` |
| UI font | `FiraCode Nerd Font` (size 15) |
| Editor font | `JetBrainsMono Nerd Font Mono` (size 13) |
| Line height | `2.0` (custom) |
| Minimap | Always shown, max 80 cols |
| Relative line numbers | Disabled |
| Colorize brackets | Enabled |
| Sticky scroll | Enabled |
| Unnecessary code fade | 50% |

### Code Intelligence

| Setting | Value |
|---|---|
| `show_completions_on_input` | `true` |
| `show_signature_help_after_edits` | `true` |
| `auto_signature_help` | `true` |
| `hover_popover_delay` | `300 ms` |

### Panels & Layout

| Panel | Dock position |
|---|---|
| Project panel | Right |
| Outline panel | Left |
| Terminal panel | Bottom |

### Language-Specific Format on Save

| Language | Formatter(s) |
|---|---|
| Python | Ruff → organize imports → fixAll → Black |
| Rust | `rust-analyzer` |
| SQL | Prettier (`prettier-plugin-sql`) |
| JSON / JSONC | Prettier |
| YAML | Prettier |
| Shell / Bash | Language server |
| Markdown | **Off** (no auto-format) |
| Dockerfile | **Off** |
| Make | **Off** (hard tabs required) |

### Active Language Servers

| Language | LSP(s) |
|---|---|
| Python | `pyright` (primary), `ruff` (lint/format) |
| Rust | `rust-analyzer` |
| YAML | `yaml-language-server` |
| JSON | `json-language-server` |
| Terraform/HCL | `terraform-ls` |
| Shell / Bash | `bash-language-server` + shellcheck |
| Dockerfile | `docker-langserver` |
| TOML | `taplo` |

---

## Quick Reference Card

```
MOVEMENT          SELECTION          EDITING
ctrl-a  ← BOL    ctrl-x h  all      ctrl-d  del→
ctrl-e  → EOL    cmd-l     line     ctrl-k  kill→EOL
ctrl-b  ← char   ctrl-/    undo     ctrl-w  cut
ctrl-f  → char   ctrl-shift-/ redo  ctrl-y  paste
cmd-b   ← word   ctrl-=    expand   ctrl-j  join lines
cmd-f   → word   ctrl-<>   multi    cmd-;   comment
cmd-<   ← BOF
cmd->   → EOF

NAVIGATION                 CODE
ctrl-c g  go to line       cmd-.       definition
cmd-,     go back          cmd-?       references
ctrl--    pane back        ctrl-;      rename
ctrl-c n  next hunk        ctrl-c ctrl-a  code actions
ctrl-c p  prev hunk        ctrl-cmd-\  format

PANES & TABS               WORKSPACE
ctrl-x 2   split↓          cmd-ctrl-b  left dock
ctrl-x 3   split→          cmd-ctrl-r  right dock
ctrl-x 0   close pane      cmd-ctrl-j  bottom dock
ctrl-tab   tab switcher     ctrl-x ctrl-x  command palette
cmd-1..9   switch tabs      cmd-`       terminal
```
