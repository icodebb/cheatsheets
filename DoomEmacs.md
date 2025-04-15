Forked from [niyumard/Doom-Emacs-Cheat-Sheet](https://github.com/niyumard/Doom-Emacs-Cheat-Sheet), with my additional content.

# A few tips for Emacs newbies

-   Use [EmacsClient](https://www.emacswiki.org/emacs/EmacsClient) and set up a daemon. Your Emacs experience will improve **a lot** and you will save a lot of time.
-   For better experience, use Emacs\'s inner file manager.
-   Get [LSP](https://emacs-lsp.github.io/lsp-mode/) up and running. It
    will turn Emacs into a fully-featured modern IDE. Emacs supports LSP
    for almost every language.
-   Try to avoid terminal version of Emacs when possible.
-   Use Doom Emacs\'s built-in helps to understand how things work under
    the hood and change them to suit your needs.
    -   `SPC h k`{.verbatim} tells you how key combinations translate to
        Emacs commands.
    -   `SPC h w`{.verbatim} helps you find keyboard shortcuts for
        different commands.
    -   `SPC h v`{.verbatim} lets you see what\'s inside variables and
        change them.
    -   `SPC h f`{.verbatim} tells you about functions and where they
        are defined.
-   Github doesn\'t render org files very well. It\'s best that you
    clone this repository and open it in Emacs.
-   See other files in this repository as well. Currently additional
    instructions for Go, and Python are also offered. If there\'s
    anything missing, or you can suggest a better workflow, make sure to
    contribute.

# Command Abbreviations

-   `C`{.verbatim} \"Control\" key
-   `M`{.verbatim} \"Alt\" or \"Option\" key
-   `S`{.verbatim} \"Super\" or \"Command\" key `SPC`{.verbatim}
    \"Space\" key

# General

-   `SPC f s`{.verbatim} for saving the current file
-   `SPC :`{.verbatim} for entering a command
-   `SPC q q`{.verbatim} to close Emacs
-   `SPC f D`{.verbatim} to delete this file

# Motion

-   `g g`{.verbatim} move to beginning of the document
-   `C-f`{.verbatim} `fn-shift-down`{.verbatim} move forward/page down
-   `C-b`{.verbatim} `fn-shift-up`{.verbatim} move backward/page up
-   `Shift-g`{.verbatim} move to the end of the document
-   `C-c C-n/p`{.verbatim} move the next/previous heading

# Edit

-   `C-RET`{.verbatim} insert new heading after subtree(does not work as
    expected)
-   `M-x org-insert-heading`{.verbatim} insert headline at current line
-   `M-RET`{.verbatim} append new heading/item at current level
-   `C-c -`{.verbatim} change the current level items type between
    `-, +, 1, 1), a, A, a), A)`{.verbatim}.
-   `C-c *`{.verbatim} change the item into headline(same level)
-   `C-x u`{.verbatim} undo in Emacs way, one step, Vim does a lot,
    cannot live with it.
-   `M-x evil-redo`{.verbatim} redo, since Vim undo too much
-   Use `mRemoteNG`{.verbatim} with Putty to run Doom, to copy from
    Windows and paste with right mouse.
-   Use `Shift`{.verbatim} + Mouse Right Click to paste in Doom Emacs
    when using Putty to remote Linux

# Projects with Projectile

-   `SPC p a`{.verbatim} to add a new project
-   `SPC p d`{.verbatim} to delete a project from the list
-   `SPC p p`{.verbatim} to open a project
-   `SPC SPC`{.verbatim} to open a file in a project
-   `SPC o p`{.verbatim} to open the file explorer
-   `SPC o E`{.verbatim} to open the shell (eshell) in fullscreen
-   `SPC o e`{.verbatim} to open the shell (eshell) in a popup window
-   `SPC f r`{.verbatim} recently visited files
-   `SPC p r`{.verbatim} recently visited files in a project
-   `M-x projectile-discover-projects-in-directory`{.verbatim} to find
    projects within given folder using Projectile
-   `M-x projectile-discover-projects-in-search-path`{.verbatim} to find
    projects in the folder defined by the
    `projectile-project-search-path`{.verbatim} variable using
    Projectile

# Dired

-   Dired (Directory Editor) is how you interfaces with a directory
-   Press `C-x d`{.verbatim} to open dired.
-   Use `RET`{.verbatim} to go to a folder or open a file.
-   Use `-`{.verbatim} for going one folder back
-   Use `+`{.verbatim} for creating a new directory
-   Use `d`{.verbatim} to mark the files for deletion, press
    `x`{.verbatim} to delete.
-   Use `M`{.verbatim} to change permissions
-   Use `o`{.verbatim} to sort by modes.
-   Use `O`{.verbatim} to change the owner.
-   Use `m`{.verbatim} to mark and `u`{.verbatim} to unmark files or
    directories.
-   `U`{.verbatim} to unselect all
-   Use `t`{.verbatim} to invert the selection.
-   `t`{.verbatim} to switch between files and directories
-   Use `C`{.verbatim} to copy.
-   Use `R`{.verbatim} to move.
-   Move with `h`{.verbatim}, `j`{.verbatim}, `k`{.verbatim},
    `l`{.verbatim}
-   Toggle `(`{.verbatim} for simple view
-   `SPC .`{.verbatim} to create or find a file
    -   Use either arrow keys, or hold `C-`{.verbatim} with
        `h`{.verbatim},=j=,=k=, and `l`{.verbatim} to choose between
        options.
-   `*`{.verbatim} to select all directories.
-   `C`{.verbatim} copy to another window
-   `R`{.verbatim} move to another window
-   `dired-do-what-i-mean-target`{.verbatim} set to true
-   `i`{.verbatim} to edit file/dir name, `Esc Z Z`{.verbatim} to save
    the modification, `Esc Z Q`{.verbatim} to discard.

# Buffers, Windows and Basic Navigation

## Buffers and Files

Buffers are a special concept in emacs they can be terminals, files,
directories, etc.

-   `SPC b b`{.verbatim} to open/switch another buffer
    -   workspace buffer
-   `SPC b B`{.verbatim} list all the buffer
-   `SPC ,`{.verbatim} to switch buffers (it\'s an alias)
-   `SPC SHIFT ,`{.verbatim} to switch to all buffers
-   `SPC b n/]`{.verbatim} next buffer
-   `SPC b p/[`{.verbatim} previous buffer
-   `SPC b X`{.verbatim} You can create a scratch buffer.
-   `SPC SPC`{.verbatim} or `SPC f f`{.verbatim} Open a file from
    project.
-   `SPC .`{.verbatim} Create of find a file.
-   `SPC b s`{.verbatim} to save and name the buffer
-   `SPC b S`{.verbatim} to save all buffers
-   `SPC b d/k`{.verbatim} to kill the current buffer
-   `SPC b K`{.verbatim} to kill all buffers

## Windows

Windows are panes in your screen

-   `SPC w v`{.verbatim} window split vertically
-   `SPC w s`{.verbatim} window split horizontally
-   `SPC w w`{.verbatim} `C-x o`{.verbatim} to switch windows
-   `SPC w q`{.verbatim} `SPC w c`{.verbatim} `C-x 0`{.verbatim} to
    close window, frame, quit EMACS if it\'s the last frame.
-   `C-x 1`{.verbatim} to close all other windows, this is Emacs
    command.
-   `SPC w +`{.verbatim} and `SPC w -`{.verbatim} to increase and
    decrease window height
-   `SPC w >`{.verbatim} and `SPC w <`{.verbatim} to increase and
    decrease window width
-   You can use vim motion keys to navigate between open windows for
    example `SPC w H`{.verbatim} moves the window to the left.

## Workspaces

-   `SPC TAB TAB`{.verbatim} display tab bar
-   `SPC TAB n`{.verbatim} new workspace
-   `SPC TAB N`{.verbatim} new named workspace
-   `SPC TAB r`{.verbatim} rename current workspace
-   `SPC TAB [`{.verbatim} previous workspace
-   `SPC TAB ]`{.verbatim} next workspace
-   `SPC TAB d`{.verbatim} remove workspace
-   `SPC TAB R`{.verbatim} restore last session
-   `SPC TAB .`{.verbatim} switch to workspace (display list)
-   `SPC TAB {n}`{.verbatim} Switch to workspace {n}
-   `M-1`{.verbatim} Switch to workspace 1
-   `M-2`{.verbatim} Switch to workspace 2 and so forth.
-   `SPC TAB s`{.verbatim} Save workspace to a file.
-   `SPC TAB l`{.verbatim} Load workspace from a file.

# Installing Packages using org-super-agenda as an example

-   `SPC f p`{.verbatim} to open the config.
-   To add a package, add the package to `.doom.d/package.el`{.verbatim}
-   Then close and `doom refresh`{.verbatim}
-   Then go to `.doom.d/config.el`{.verbatim} to configure the package
-   `def-package!`{.verbatim} is a macro you can use to configure
    packages
    -   `space h help`{.verbatim} you can look up method man pages
    -   `:init`{.verbatim} is used for setting the package up
    -   `:config`{.verbatim} to set configuration after the package has
        been initialized
    -   `:after`{.verbatim} lets you set which package it should load
        after
-   You can use `:after!`{.verbatim} to configure packages that are
    already there

# Quick, horizontal movements with evil-snipe

## Inline navigation

-   `f`{.verbatim} and then the letter you want to navigate to.
    -   `,`{.verbatim} will go backward
    -   `;`{.verbatim} will go forward after that \"find\"
-   `t`{.verbatim} to find and move cursor to the character before what
    you\'ve searched.
-   `v`{.verbatim} puts you in visual mode. You can select text by with
    `v t some-char-you-navigate-to`{.verbatim} or
    `v f some-char-you-navigate-to`{.verbatim}
-   `;`{.verbatim} to jump to the next find
-   `,`{.verbatim} to jump to the previous one
-   `s`{.verbatim} to snipe

## Long distance navigation inside the file

-   Evil-snipe lets you go to all the occurrences in your document
-   `g s SPC`{.verbatim} to use avy and going to a certain word in file.
-   `t`{.verbatim} is the same thing except for a character you want to
    jump to before the one you insert
-   `s`{.verbatim} to do a double character search
-   Evil-snipe will remember your last search so `,`{.verbatim} and
    `;`{.verbatim} will navigate
-   `F`{.verbatim} or `T`{.verbatim} to go backwards
-   `g s SPC`{.verbatim} and then select the letter that avy gives you
    to navigate to that spot
    -   These letters are on your home row so they are easy to click
-   `SPC h v`{.verbatim} for variable, to set the avy variable to search
    all open windows
    -   `avy-all-windows`{.verbatim} lets you search in all windows
        open.
-   You can remove a word with
    `g s SPC select-one-letter x select-the-removal-spot`{.verbatim}
    -   You can use `X`{.verbatim} to stay in your original spot of
        search
-   You can go
    `g s space select-one-letter i select-the-correction-spot`{.verbatim}
    to correct the spelling of the search
    -   Install ispell on your OS first
-   You can `yank`{.verbatim} a word from one place to another with
    `g s SPC select-one-letter y select-the-correction-spot-to-paste`{.verbatim}
-   Use `t`{.verbatim} to \"teleport\" the word from one place to
    another
    `g s SPC select-one-letter t select-the-correction-spot-to-teleport`{.verbatim}

# Multiple cursor in Emacs with evil-multiedit

-   Using evil-multiedit (known as multiple cursors in other IDEs) you
    can make selections and then edit those selections simultaneously.
    To do this uncomment `multiple-cursors`{.verbatim} in your
    `init.el`{.verbatim}.
-   `M-d`{.verbatim} will select the current word, press this again and
    it will find another occurrence
-   `M-D`{.verbatim} will find an occurrence upward
-   You can use a visual selection to select multiple words as well.
-   `R`{.verbatim} will select all occurrences.
-   `CTRL n`{.verbatim} for next selection `CTRL p`{.verbatim} for
    previous.
-   Exclude matches with `RET`{.verbatim}
-   You can make an edit and the changes will be reflected to all the
    selections.

# Org Mode

## Basics

-   `M-x hl-line-mode`{.verbatim} highlight current line on/off
-   Org mode gives you structure to your document
-   `*`{.verbatim} for a h1 `**`{.verbatim} for an h2 and so on
-   You can `TAB`{.verbatim} a section to fold a subtree (hide it)
-   You can use `SHIFT TAB`{.verbatim} to cycle through folded states
-   `CTRL return`{.verbatim} to create a headline of the same type
-   `M return`{.verbatim} to create a headline at same level
-   `M-arrow up`{.verbatim} lets you shift the position of the section
-   `M-h`{.verbatim} promotes a headline to the next level
-   `M-l`{.verbatim} demotes
-   `M-left/right`{.verbatim} to promote or demote a headline
-   You can create lists
    1.  one
    2.  2
    3.  wooo
    4.  3

## Links, Hyperlinks and more

-   `C-x C-o`{.verbatim} open a link, same to RET while cursor in on the
    link
-   `SPC m l t`{.verbatim} `M-x org-toggle-link-display`{.verbatim} to
    show the link as plain text
-   `M-x font-lock-mode`{.verbatim} switch to normal text mode and
    decorated form, sometimes rich mode messed up
-   `SPC m l`{.verbatim} to add a link to an org page
-   You can add `::`{.verbatim} to specify a heading or a line number
-   You can paste http links as well
-   You can \"link\" some text with specific code `SPC m l`{.verbatim}
    elisp: [(+ 2 2)](elisp:(+ 2 2)) when you click the link, emacs will
    evaluate the expression
-   Show [My Agenda](elisp:org-agenda)
-   [List Files](shell:ls) in directory

## Defining custom Link Types

-   [Watch the video about custom
    links](https://youtube.com/watch?v=Febe4lUK5G4)

## Linking to words & Bookmarks

-   `SPC n l`{.verbatim} stores a link to a particular headline

## Code Snippets & Babel

-   `SPC i s`{.verbatim} for inserting code snippets
    -   Example:

        ``` {.commonlisp org-language="emacs-lisp" tangle="yes"}
        (+ 2 3 4 5)
        ```
-   `C-c C-c`{.verbatim} to execute the code.
-   `SPC m '`{.verbatim} to edit inside the babel in another buffer.
-   Results will show up in a `##+RESULTS`{.verbatim} header
-   This feature is called Babel
-   One snippet can consume the output of another snippet
-   You can create your own snippets in the following directory:
    `~/.doom.d/snippets/`{.verbatim}

## Task Management

-   Create a task by prefixing any heading with `TODO`{.verbatim}
-   `DONE`{.verbatim} means the task is done
-   You can create your custom key words by changing this variable:
    `org-todo-keywords`{.verbatim}
    -   remember you can get to your variables through
        `SPC h v`{.verbatim} (M-x counsel-describe-variable)

    -   These values are already set in Doom:

        ``` example
           ((sequence "TODO(t)" "PROJ(p)" "STRT(s)" "WAIT(w)" "HOLD(h)" "|" "DONE(d)" "KILL(k)")
        (sequence "[ ](T)" "[-](S)" "[?](W)" "|" "[X](D)"))
        ```
-   `SPC m t`{.verbatim} to change a status of a todo
-   `SHIFT left`{.verbatim} and `SHIFT right`{.verbatim} can be used to
    change the status of a todo as well.
-   If you finish a task with a command, org mode will add a date that
    you \"closed\" the task.
-   `SPC o a t`{.verbatim} to open the agenda -\> todo list
-   `q`{.verbatim} to quit
-   `org-agenda-files`{.verbatim} is a variable you can set to filter
    which files agenda searches for todos in.

### Priorities for Tasks

-   `SHIFT up`{.verbatim} and `SHIFT down`{.verbatim} will toggle the
    priority of tasks
-   `org-fancy-priorities`{.verbatim} gives you fancy looking priorities

### Marking Tasks with Tags

-   Tags can be attached to any headlines
-   `SPC m q`{.verbatim} to tag a headline
-   Example:
    -   TODO play more games :fun:
-   Tags are hierarchical so nested headings will be tagged with the
    parent header tag
-   `org-tag-sparce-tree`{.verbatim} will search for headings that only
    have a specific tag

### Setting a property for a task/headline

-   `SPC m o`{.verbatim} is used for setting a property.

1.  Marking Headlines with Categories

    -   You can use
        [categories](https://orgmode.org/manual/Categories.html) to
        change the label in agenda view.

2.  Org-Habits

    -   If you want to [keep track of your
        habits](https://orgmode.org/manual/Tracking-your-habits.html)
        using org mode, you can set the `STYLE`{.verbatim} property to
        habit.

## Lists

-   Two types of lists, ordered and unordered lists
    -   `SHIFT right`{.verbatim} and `SHIFT left`{.verbatim} can be used
        to change the type of lists.
-   You can also change an unordered list by changing the first item
    to 1. and then typing `C-c C-c`{.verbatim} and vice versa.

## Checkboxes

-   [ ] This is still todo
-   [ ] This is in progress
-   [x] This is a done task

### You can see how many are done with a \"cookie\" \[1/2\]

-   [ ] Task 1
-   [x] Task 2
-   You can do this by adding \[/\] to the heading and pressing
    `C-c C-c`{.verbatim}
-   You can\'t assign a tag or a priority

## Pretty Bullets

-   [Get pretty org-bullets in Doom
    Emacs](https://mpas.github.io/posts/2020/10/16/20201016-org-bullets-doom-emacs/)

-   \~/.doom.d/init.el

    ``` {.commonlisp org-language="lisp"}
    :lang
    (org +pretty ) ; organize your plain life in plain text
    ```

-   \~/.doom.d/config.el

    ``` list
    (setq
        org-superstar-headline-bullets-list '("⁖" "◉" "○" "✸" "✿")
    )
    ```

-   [Nerd Fonts Download](https://www.nerdfonts.com/font-downloads)

# Magit

-   Magit is enabled by default in Doom Emacs\'s init.el
-   `SPC g g`{.verbatim} shows Magit status page
    -   Most commands are done from the status page
    -   Use tab to expand headlines in the status page
-   `?`{.verbatim} in Magit\'s status page for a nice list of available
    commands and help, `q`{.verbatim} to close this help page
-   Open diff view for a file with `TAB`{.verbatim}
-   Press `s`{.verbatim} under \"Unstaged changes\" to stage a change
    -   `u`{.verbatim} to undo a change
    -   `c`{.verbatim} to commit
-   `b s`{.verbatim} for branch and spinoff to create another branch,
    rewinding the commits you made to master
-   `b b`{.verbatim} to switch branches

## Git Commit Flow in More Detail

-   `t t`{.verbatim} to create a tag, default place is the commit you
    are currently selecting
-   `V`{.verbatim} to select a change in a diff and `x`{.verbatim} to
    discard that change.
-   `s`{.verbatim} to stage
-   `c`{.verbatim} to commit, you can `q`{.verbatim} to quit the commit
    screen
-   `P`{.verbatim} to push and then `p`{.verbatim} to your remote or
    `u`{.verbatim} to a another remote

## Magit with Forge for Issuing Pull Requests - Emacs

-   Forge is installed in emacs doom
-   `@`{.verbatim} for forge
-   Set up forge with `M x forge-pull`{.verbatim}
    -   the first time you will get a token from Github
-   `@ c p`{.verbatim} to create a pull request with forge
    -   select the base branch
    -   then select the target branch
    -   then provide a short description
    -   `CTRL c CTRL c`{.verbatim} to finish the pull request
-   Now there will be a `pull requests`{.verbatim} tab

# LSP-Mode

## LSP related

-   `lsp-update-server`{.verbatim} select a language server to update.
-   `lsp-workspace-folders-add`{.verbatim} to interactively set a folder
    as an LSP workspace.
-   `lsp-workspace-folders-remove`{.verbatim} to interactively unset a
    folder as an LSP workspace.
-   `lsp-workspace-restart`{.verbatim} to restart your workspace.
    Especially useful after activating a virtual environment.

## While coding

-   `SPC c c`{.verbatim} to run a compile command (or a test, or any
    other command in the current directory)
-   `SPC c C`{.verbatim} to repeat the command above
-   `SPC c d`{.verbatim} jump to var/func/... definitions
    -   `C o`{.verbatim} (`evil-jump-backward`{.verbatim}) Go back to
        your last position in the jump list
    -   `C i`{.verbatim} (`evil-jump-forward`{.verbatim}) Go forward in
        the jump list
-   `SPC c D`{.verbatim} see references to var/func/...
-   `SPC c e`{.verbatim} to evaluate the current buffer or region (when
    nothing is selected, equivalent to running `SPC c c`{.verbatim} and
    writing `go run`{.verbatim} + the file name.)
-   `SPC c f`{.verbatim} see references to var/func/...
-   `SPC c k`{.verbatim} jump to documentation
-   `SPC c r`{.verbatim} rename all references and definitions for the
    var/func at point in all project files
-   `SPC c s`{.verbatim} send to REPS
-   `SPC c x`{.verbatim} see all LSP diagnostics
-   `lsp-ui-imenu`{.verbatim} to navigate definitions in your code
-   `flycheck-list-errors`{.verbatim} to see the errors detected by LSP.

# Spell

-   `z =`{.verbatim} Check word, choose suggestions or save to
    dictionary
-   `M-x flyspell-mode/M-SPC t s`{.verbatim} Enable the flyzspell mode
-   `${HOME}/.ispell_default`{.verbatim} Edit the default user
    dictionary file to remove unwanted entries.

# Terminal

-   Set up vterm in your init.el file.
-   `SPC o T`{.verbatim} for opening vterm
-   `SPC o t`{.verbatim} for opening vterm in a popup window

# File/Project Tree

-   Set up neotree or treemacs in your init.el file.
-   `SPC o p`{.verbatim} for opening neotree or treemacs
-   `SPC w ->/<-`{.verbatim} Move to right window or treemacs pane
-   `>/<`{.verbatim} Increase/decrease treemacs width

# Others

-   `C-c C-z`{.verbatim} to insert a note for a heading in org mode.

<!-- -->

-   `C-c C-c`{.verbatim} to insert a tag for a heading in org mode.

# Capturing

-   `SPC X`{.verbatim} to capture (the new thing gets captured to a
    single file but that\'s fine since we can easily refile it.)
-   `SPC m r r`{.verbatim} to refile

# Org Roam

These keybindings only work after installing org-roam. To install
org-roam edit your `init.el`{.verbatim} file and add
`(org +roam2)`{.verbatim} in its designated place. Watch [this
video](https://www.youtube.com/watch?v=AyhPmypHDEw) to understand what
org-roam is.

-   `SPC n r f`{.verbatim} Find an existing node or create a new one.
-   `SPC n r i`{.verbatim} Insert a link to another node.
-   `SPC n r r`{.verbatim} Toggle backlinks pane
-   `SPC m m o t`{.verbatim} Add a roam tag.
-   `SPC m m o a`{.verbatim} Add a roam alias.

# Code Folding

Code folding helps with code readability. First, make sure
`fold`{.verbatim} is not commented in your `init.el`{.verbatim} file
then move your cursor to the definition of a class or a function and try
the following:

-   `z a`{.verbatim} Toggle the fold at point.
-   `z m`{.verbatim} Close all the folds.
-   `z r`{.verbatim} Open all the folds.
-   `z j`{.verbatim} Next folded region.
-   `z k`{.verbatim} Previous folded region.

# Resources

## Documentation

-   [This org file is mostly from the notes taken from the series above
    by
    ianjones.us](https://www.ianjones.us/zaiste-programming-doom-emacs-tutorial/#org7ad2452)
-   [Doom Emacs Documentation](https://github.com/doomemacs/doomemacs)
-   [Three Huge Mistakes New Emacs Users
    Make](https://www.youtube.com/watch?v=s0ed8Da3mjE) (they are
    included in the tips in the beginning of the file)
-   [Org mode syntax example - Graphics, Images, Video,
    etc.](http://www.pirilampo.org/org-mode/syntax/index.html)
-   [ORG-MODE BASICS IV: FORMATTING TEXT AND SOURCE
    CODE](https://pragmaticemacs.wordpress.com/2015/09/25/org-mode-basics-iv-formatting-text-and-source-code/)
-   [org-special-block-extras - A unified interface for special blocks
    and links: defblock](http://alhassy.com/org-special-block-extras/)
-   [Code vs. Verbatim in Org Mode](https://irreal.org/blog/?p=11123)
-   [My Doom Emacs configuration, with
    commentary](https://zzamboni.org/post/my-doom-emacs-configuration-with-commentary/)
-   [gitlab.com*h-cheung/doom-emacs-config*-/blob/master/init.el](https://gitlab.com/h-cheung/doom-emacs-config/-/blob/master/init.el)
    lots of \"+\"s in org line.
-   [Switching from Spacemacs to Doom
    Emcas](https://ethanaa.com/blog/switching-to-doom-emacs/#why-the-switch)

## YouTube

-   [Link:w to the youtube video
    series](https://www.youtube.com/watch?v=BRqjaN4-gGQ&list=PLhXZp00uXBk4np17N39WvB80zgxlZfVwj&index=10)
-   [Emacs: Org mode
    basics](https://www.youtube.com/watch?v=e9Ucb1JHUfQ)

## Tools

-   [Pandoc a universal document
    converter](https://pandoc.org/MANUAL.html)

# Known Issues

-   `hl-todo-mode`{.verbatim} Does not work.
-   Don\'t know how to paste content from Windows via Putty, it\'s not
    in \'doom run\', but with \'emacs file-name\'.

# What to learn \[0/3\]

-   [ ] LSP
-   [ ] [Org Roam](https://www.orgroam.com)
-   [ ] abbrev-mode
