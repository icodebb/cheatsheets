Forked from [niyumard/Doom-Emacs-Cheat-Sheet](https://github.com/niyumard/Doom-Emacs-Cheat-Sheet), with my additional content.

# A few tips for Emacs newbies

- Use [EmacsClient](https://www.emacswiki.org/emacs/EmacsClient) and set up a daemon. Your Emacs experience will improve **a lot** and you will save a lot of time.
- For better experience, use Emacs\'s inner file manager.
- Get [LSP](https://emacs-lsp.github.io/lsp-mode/) up and running. It
    will turn Emacs into a fully-featured modern IDE. Emacs supports LSP
    for almost every language.
- Try to avoid terminal version of Emacs when possible.
- Use Doom Emacs\'s built-in helps to understand how things work under
    the hood and change them to suit your needs.
  - `SPC h k` tells you how key combinations translate to
        Emacs commands.
  - `SPC h w` helps you find keyboard shortcuts for
        different commands.
  - `SPC h v` lets you see what\'s inside variables and
        change them.
  - `SPC h f` tells you about functions and where they
        are defined.
- Github doesn\'t render org files very well. It\'s best that you
    clone this repository and open it in Emacs.
- See other files in this repository as well. Currently additional
    instructions for Go, and Python are also offered. If there\'s
    anything missing, or you can suggest a better workflow, make sure to
    contribute.

# Command Abbreviations

- `C` \"Control\" key
- `M` \"Alt\" or \"Option\" key
- `S` \"Super\" or \"Command\" key `SPC`
    \"Space\" key

# General

- `SPC f s` for saving the current file
- `SPC :` for entering a command
- `SPC q q` to close Emacs
- `SPC f D` to delete this file

# Motion

- `g g` move to beginning of the document
- `C-f` `fn-shift-down` move forward/page down
- `C-b` `fn-shift-up` move backward/page up
- `Shift-g` move to the end of the document
- `C-c C-n/p` move the next/previous heading

# Edit

- `C-RET` insert new heading after subtree(does not work as
    expected)
- `M-x org-insert-heading` insert headline at current line
- `M-RET` append new heading/item at current level
- `C-c -` change the current level items type between
    `-, +, 1, 1), a, A, a), A)`.
- `C-c *` change the item into headline(same level)
- `C-x u` undo in Emacs way, one step, Vim does a lot,
    cannot live with it.
- `M-x evil-redo` redo, since Vim undo too much
- Use `mRemoteNG` with Putty to run Doom, to copy from
    Windows and paste with right mouse.
- Use `Shift` + Mouse Right Click to paste in Doom Emacs
    when using Putty to remote Linux

# Projects with Projectile

- `SPC p a` to add a new project
- `SPC p d` to delete a project from the list
- `SPC p p` to open a project
- `SPC SPC` to open a file in a project
- `SPC o p` to open the file explorer
- `SPC o E` to open the shell (eshell) in fullscreen
- `SPC o e` to open the shell (eshell) in a popup window
- `SPC f r` recently visited files
- `SPC p r` recently visited files in a project
- `M-x projectile-discover-projects-in-directory` to find
    projects within given folder using Projectile
- `M-x projectile-discover-projects-in-search-path` to find
    projects in the folder defined by the
    `projectile-project-search-path` variable using
    Projectile

# Dired

- Dired (Directory Editor) is how you interfaces with a directory
- Press `C-x d` to open dired.
- Use `RET` to go to a folder or open a file.
- Use `-` for going one folder back
- Use `+` for creating a new directory
- Use `d` to mark the files for deletion, press
    `x` to delete.
- Use `M` to change permissions
- Use `o` to sort by modes.
- Use `O` to change the owner.
- Use `m` to mark and `u` to unmark files or
    directories.
- `U` to unselect all
- Use `t` to invert the selection.
- `t` to switch between files and directories
- Use `C` to copy.
- Use `R` to move.
- Move with `h`, `j`, `k`,
    `l`
- Toggle `(` for simple view
- `SPC .` to create or find a file
  - Use either arrow keys, or hold `C-` with
        `h`,=j=,=k=, and `l` to choose between
        options.
- `*` to select all directories.
- `C` copy to another window
- `R` move to another window
- `dired-do-what-i-mean-target` set to true
- `i` to edit file/dir name, `Esc Z Z` to save
    the modification, `Esc Z Q` to discard.

# Buffers, Windows and Basic Navigation

## Buffers and Files

Buffers are a special concept in emacs they can be terminals, files,
directories, etc.

- `SPC b b` to open/switch another buffer
  - workspace buffer
- `SPC b B` list all the buffer
- `SPC ,` to switch buffers (it\'s an alias)
- `SPC SHIFT ,` to switch to all buffers
- `SPC b n/]` next buffer
- `SPC b p/[` previous buffer
- `SPC b X` You can create a scratch buffer.
- `SPC SPC` or `SPC f f` Open a file from
    project.
- `SPC .` Create of find a file.
- `SPC b s` to save and name the buffer
- `SPC b S` to save all buffers
- `SPC b d/k` to kill the current buffer
- `SPC b K` to kill all buffers

## Windows

Windows are panes in your screen

- `SPC w v` window split vertically
- `SPC w s` window split horizontally
- `SPC w w` `C-x o` to switch windows
- `SPC w q` `SPC w c` `C-x 0` to
    close window, frame, quit EMACS if it\'s the last frame.
- `C-x 1` to close all other windows, this is Emacs
    command.
- `SPC w +` and `SPC w -` to increase and
    decrease window height
- `SPC w >` and `SPC w <` to increase and
    decrease window width
- You can use vim motion keys to navigate between open windows for
    example `SPC w H` moves the window to the left.

## Workspaces

- `SPC TAB TAB` display tab bar
- `SPC TAB n` new workspace
- `SPC TAB N` new named workspace
- `SPC TAB r` rename current workspace
- `SPC TAB [` previous workspace
- `SPC TAB ]` next workspace
- `SPC TAB d` remove workspace
- `SPC TAB R` restore last session
- `SPC TAB .` switch to workspace (display list)
- `SPC TAB {n}` Switch to workspace {n}
- `M-1` Switch to workspace 1
- `M-2` Switch to workspace 2 and so forth.
- `SPC TAB s` Save workspace to a file.
- `SPC TAB l` Load workspace from a file.

# Installing Packages using org-super-agenda as an example

- `SPC f p` to open the config.
- To add a package, add the package to `.doom.d/package.el`
- Then close and `doom refresh`
- Then go to `.doom.d/config.el` to configure the package
- `def-package!` is a macro you can use to configure
    packages
  - `space h help` you can look up method man pages
  - `:init` is used for setting the package up
  - `:config` to set configuration after the package has
        been initialized
  - `:after` lets you set which package it should load
        after
- You can use `:after!` to configure packages that are
    already there

# Quick, horizontal movements with evil-snipe

## Inline navigation

- `f` and then the letter you want to navigate to.
  - `,` will go backward
  - `;` will go forward after that \"find\"
- `t` to find and move cursor to the character before what
    you\'ve searched.
- `v` puts you in visual mode. You can select text by with
    `v t some-char-you-navigate-to` or
    `v f some-char-you-navigate-to`
- `;` to jump to the next find
- `,` to jump to the previous one
- `s` to snipe

## Long distance navigation inside the file

- Evil-snipe lets you go to all the occurrences in your document
- `g s SPC` to use avy and going to a certain word in file.
- `t` is the same thing except for a character you want to
    jump to before the one you insert
- `s` to do a double character search
- Evil-snipe will remember your last search so `,` and
    `;` will navigate
- `F` or `T` to go backwards
- `g s SPC` and then select the letter that avy gives you
    to navigate to that spot
  - These letters are on your home row so they are easy to click
- `SPC h v` for variable, to set the avy variable to search
    all open windows
  - `avy-all-windows` lets you search in all windows
        open.
- You can remove a word with
    `g s SPC select-one-letter x select-the-removal-spot`
  - You can use `X` to stay in your original spot of
        search
- You can go
    `g s space select-one-letter i select-the-correction-spot`
    to correct the spelling of the search
  - Install ispell on your OS first
- You can `yank` a word from one place to another with
    `g s SPC select-one-letter y select-the-correction-spot-to-paste`
- Use `t` to \"teleport\" the word from one place to
    another
    `g s SPC select-one-letter t select-the-correction-spot-to-teleport`

# Multiple cursor in Emacs with evil-multiedit

- Using evil-multiedit (known as multiple cursors in other IDEs) you
    can make selections and then edit those selections simultaneously.
    To do this uncomment `multiple-cursors` in your
    `init.el`.
- `M-d` will select the current word, press this again and
    it will find another occurrence
- `M-D` will find an occurrence upward
- You can use a visual selection to select multiple words as well.
- `R` will select all occurrences.
- `CTRL n` for next selection `CTRL p` for
    previous.
- Exclude matches with `RET`
- You can make an edit and the changes will be reflected to all the
    selections.

# Org Mode

## Basics

- `M-x hl-line-mode` highlight current line on/off
- Org mode gives you structure to your document
- `*` for a h1 `**` for an h2 and so on
- You can `TAB` a section to fold a subtree (hide it)
- You can use `SHIFT TAB` to cycle through folded states
- `CTRL return` to create a headline of the same type
- `M return` to create a headline at same level
- `M-arrow up` lets you shift the position of the section
- `M-h` promotes a headline to the next level
- `M-l` demotes
- `M-left/right` to promote or demote a headline
- You can create lists
    1.  one
    2.  2
    3.  wooo
    4.  3

## Links, Hyperlinks and more

- `C-x C-o` open a link, same to RET while cursor in on the
    link
- `SPC m l t` `M-x org-toggle-link-display` to
    show the link as plain text
- `M-x font-lock-mode` switch to normal text mode and
    decorated form, sometimes rich mode messed up
- `SPC m l` to add a link to an org page
- You can add `::` to specify a heading or a line number
- You can paste http links as well
- You can \"link\" some text with specific code `SPC m l`
    elisp: [(+ 2 2)](elisp:(+ 2 2)) when you click the link, emacs will
    evaluate the expression
- Show [My Agenda](elisp:org-agenda)
- [List Files](shell:ls) in directory

## Defining custom Link Types

- [Watch the video about custom
    links](https://youtube.com/watch?v=Febe4lUK5G4)

## Linking to words & Bookmarks

- `SPC n l` stores a link to a particular headline

## Code Snippets & Babel

- `SPC i s` for inserting code snippets
  - Example:

        ``` {.commonlisp org-language="emacs-lisp" tangle="yes"}
        (+ 2 3 4 5)
        ```
- `C-c C-c` to execute the code.
- `SPC m '` to edit inside the babel in another buffer.
- Results will show up in a `##+RESULTS` header
- This feature is called Babel
- One snippet can consume the output of another snippet
- You can create your own snippets in the following directory:
    `~/.doom.d/snippets/`

## Task Management

- Create a task by prefixing any heading with `TODO`
- `DONE` means the task is done
- You can create your custom key words by changing this variable:
    `org-todo-keywords`
  - remember you can get to your variables through
        `SPC h v` (M-x counsel-describe-variable)

  - These values are already set in Doom:

    ``` example
    ((sequence "TODO(t)" "PROJ(p)" "STRT(s)" "WAIT(w)" "HOLD(h)" "|" "DONE(d)" "KILL(k)")
    (sequence "[ ](T)" "[-](S)" "[?](W)" "|" "[X](D)"))
    ```

- `SPC m t` to change a status of a todo
- `SHIFT left` and `SHIFT right` can be used to
    change the status of a todo as well.
- If you finish a task with a command, org mode will add a date that
    you \"closed\" the task.
- `SPC o a t` to open the agenda -\> todo list
- `q` to quit
- `org-agenda-files` is a variable you can set to filter
    which files agenda searches for todos in.

### Priorities for Tasks

- `SHIFT up` and `SHIFT down` will toggle the
    priority of tasks
- `org-fancy-priorities` gives you fancy looking priorities

### Marking Tasks with Tags

- Tags can be attached to any headlines
- `SPC m q` to tag a headline
- Example:
  - TODO play more games :fun:
- Tags are hierarchical so nested headings will be tagged with the
    parent header tag
- `org-tag-sparce-tree` will search for headings that only
    have a specific tag

### Setting a property for a task/headline

- `SPC m o` is used for setting a property.

1.  Marking Headlines with Categories

  - You can use
        [categories](https://orgmode.org/manual/Categories.html) to
        change the label in agenda view.

2.  Org-Habits

  - If you want to [keep track of your
        habits](https://orgmode.org/manual/Tracking-your-habits.html)
        using org mode, you can set the `STYLE` property to
        habit.

## Lists

- Two types of lists, ordered and unordered lists
  - `SHIFT right` and `SHIFT left` can be used
        to change the type of lists.
- You can also change an unordered list by changing the first item
    to 1. and then typing `C-c C-c` and vice versa.

## Checkboxes

- [ ] This is still todo
- [ ] This is in progress
- [x] This is a done task

### You can see how many are done with a \"cookie\" \[1/2\]

- [ ] Task 1
- [x] Task 2
- You can do this by adding \[/\] to the heading and pressing
    `C-c C-c`
- You can\'t assign a tag or a priority

## Pretty Bullets

- [Get pretty org-bullets in Doom
    Emacs](https://mpas.github.io/posts/2020/10/16/20201016-org-bullets-doom-emacs/)

- \~/.doom.d/init.el

    ``` {.commonlisp org-language="lisp"}
    :lang
    (org +pretty ) ; organize your plain life in plain text
    ```

- \~/.doom.d/config.el

    ``` list
    (setq
        org-superstar-headline-bullets-list '("⁖" "◉" "○" "✸" "✿")
    )
    ```

- [Nerd Fonts Download](https://www.nerdfonts.com/font-downloads)

# Magit

- Magit is enabled by default in Doom Emacs\'s init.el
- `SPC g g` shows Magit status page
  - Most commands are done from the status page
  - Use tab to expand headlines in the status page
- `?` in Magit\'s status page for a nice list of available
    commands and help, `q` to close this help page
- Open diff view for a file with `TAB`
- Press `s` under \"Unstaged changes\" to stage a change
  - `u` to undo a change
  - `c` to commit
- `b s` for branch and spinoff to create another branch,
    rewinding the commits you made to master
- `b b` to switch branches

## Git Commit Flow in More Detail

- `t t` to create a tag, default place is the commit you
    are currently selecting
- `V` to select a change in a diff and `x` to
    discard that change.
- `s` to stage
- `c` to commit, you can `q` to quit the commit
    screen
- `P` to push and then `p` to your remote or
    `u` to a another remote

## Magit with Forge for Issuing Pull Requests - Emacs

- Forge is installed in emacs doom
- `@` for forge
- Set up forge with `M x forge-pull`
  - the first time you will get a token from Github
- `@ c p` to create a pull request with forge
  - select the base branch
  - then select the target branch
  - then provide a short description
  - `CTRL c CTRL c` to finish the pull request
- Now there will be a `pull requests` tab

# LSP-Mode

## LSP related

- `lsp-update-server` select a language server to update.
- `lsp-workspace-folders-add` to interactively set a folder
    as an LSP workspace.
- `lsp-workspace-folders-remove` to interactively unset a
    folder as an LSP workspace.
- `lsp-workspace-restart` to restart your workspace.
    Especially useful after activating a virtual environment.

## While coding

- `SPC c c` to run a compile command (or a test, or any
    other command in the current directory)
- `SPC c C` to repeat the command above
- `SPC c d` jump to var/func/... definitions
  - `C o` (`evil-jump-backward`) Go back to
        your last position in the jump list
  - `C i` (`evil-jump-forward`) Go forward in
        the jump list
- `SPC c D` see references to var/func/...
- `SPC c e` to evaluate the current buffer or region (when
    nothing is selected, equivalent to running `SPC c c` and
    writing `go run` + the file name.)
- `SPC c f` see references to var/func/...
- `SPC c k` jump to documentation
- `SPC c r` rename all references and definitions for the
    var/func at point in all project files
- `SPC c s` send to REPS
- `SPC c x` see all LSP diagnostics
- `lsp-ui-imenu` to navigate definitions in your code
- `flycheck-list-errors` to see the errors detected by LSP.

# Spell

- `z =` Check word, choose suggestions or save to
    dictionary
- `M-x flyspell-mode/M-SPC t s` Enable the flyzspell mode
- `${HOME}/.ispell_default` Edit the default user
    dictionary file to remove unwanted entries.

# Terminal

- Set up vterm in your init.el file.
- `SPC o T` for opening vterm
- `SPC o t` for opening vterm in a popup window

# File/Project Tree

- Set up neotree or treemacs in your init.el file.
- `SPC o p` for opening neotree or treemacs
- `SPC w ->/<-` Move to right window or treemacs pane
- `>/<` Increase/decrease treemacs width

# Others

- `C-c C-z` to insert a note for a heading in org mode.

<!-- -->

- `C-c C-c` to insert a tag for a heading in org mode.

# Capturing

- `SPC X` to capture (the new thing gets captured to a
    single file but that\'s fine since we can easily refile it.)
- `SPC m r r` to refile

# Org Roam

These keybindings only work after installing org-roam. To install
org-roam edit your `init.el` file and add
`(org +roam2)` in its designated place. Watch [this
video](https://www.youtube.com/watch?v=AyhPmypHDEw) to understand what
org-roam is.

- `SPC n r f` Find an existing node or create a new one.
- `SPC n r i` Insert a link to another node.
- `SPC n r r` Toggle backlinks pane
- `SPC m m o t` Add a roam tag.
- `SPC m m o a` Add a roam alias.

# Code Folding

Code folding helps with code readability. First, make sure
`fold` is not commented in your `init.el` file
then move your cursor to the definition of a class or a function and try
the following:

- `z a` Toggle the fold at point.
- `z m` Close all the folds.
- `z r` Open all the folds.
- `z j` Next folded region.
- `z k` Previous folded region.

# Resources

## Documentation

- [This org file is mostly from the notes taken from the series above
    by
    ianjones.us](https://www.ianjones.us/zaiste-programming-doom-emacs-tutorial/#org7ad2452)
- [Doom Emacs Documentation](https://github.com/doomemacs/doomemacs)
- [Three Huge Mistakes New Emacs Users
    Make](https://www.youtube.com/watch?v=s0ed8Da3mjE) (they are
    included in the tips in the beginning of the file)
- [Org mode syntax example - Graphics, Images, Video,
    etc.](http://www.pirilampo.org/org-mode/syntax/index.html)
- [ORG-MODE BASICS IV: FORMATTING TEXT AND SOURCE
    CODE](https://pragmaticemacs.wordpress.com/2015/09/25/org-mode-basics-iv-formatting-text-and-source-code/)
- [org-special-block-extras - A unified interface for special blocks
    and links: defblock](http://alhassy.com/org-special-block-extras/)
- [Code vs. Verbatim in Org Mode](https://irreal.org/blog/?p=11123)
- [My Doom Emacs configuration, with
    commentary](https://zzamboni.org/post/my-doom-emacs-configuration-with-commentary/)
- [gitlab.com*h-cheung/doom-emacs-config*-/blob/master/init.el](https://gitlab.com/h-cheung/doom-emacs-config/-/blob/master/init.el)
    lots of \"+\"s in org line.
- [Switching from Spacemacs to Doom
    Emcas](https://ethanaa.com/blog/switching-to-doom-emacs/#why-the-switch)

## YouTube

- [Link:w to the youtube video
    series](https://www.youtube.com/watch?v=BRqjaN4-gGQ&list=PLhXZp00uXBk4np17N39WvB80zgxlZfVwj&index=10)
- [Emacs: Org mode
    basics](https://www.youtube.com/watch?v=e9Ucb1JHUfQ)

## Tools

- [Pandoc a universal document
    converter](https://pandoc.org/MANUAL.html)

# Known Issues

- `hl-todo-mode` Does not work.
- Don\'t know how to paste content from Windows via Putty, it\'s not
    in \'doom run\', but with \'emacs file-name\'.

# What to learn \[0/3\]

- [ ] LSP
- [ ] [Org Roam](https://www.orgroam.com)
- [ ] abbrev-mode
