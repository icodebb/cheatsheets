# tmux

## Command Line

```Bash
tmux new -s session-name           # create a new session with session-name  
tmux a(at, attach) n               # attaching to a existing session  
tmux a -t session-name             # attach to a named session  
tmux ls(list-sessions              # show sessions  
tmux detach                        # detaching from a session  
tmux kill-session -t session-name  # kill a names session
tmux kill-server                   # kill all sessions
```

## Shortcuts

The Ctrl-b options reference.

### Basics  
  
`?` get help, view all key bindings, Q to exit.  
`:` run a command, Q to exit.  

### Session management
  
`s` list sessions and switch to another one if you want, `q` to quit the view
`$` rename the current session  
`d` detach from the current session  
`: new` start a new session
`: kill-session` kill/delete the current session
`(` move to previous session
`)` move to next session
`L` lock your tmux session
`:source-file ~/.tmux.conf` reload config inside tmux
`:setw synchronize-panes on` synchronize panes(type same command in all panes)
`:setw synchronize-panes off` turn synchronize off
### Windows
  
`c` create a new window  
`,` rename the current window  
`w` list windows, sessions and windows preview
`&` close current window
`%` split horizontally  
`"` split vertically  
`n` change to the next window
`p` change to the previous window
`l` toggle last active window
`0...9` to select windows 0 through 9  
`&` kill window
`exit` or `Ctrl` + `d` to close window

### Panes
  
`%` create a horizontal pane  
`"` create a vertical pane  
`←/h` move to the left pane. (`hjlk` don't work on hsv-tor3)  
`↓/j` move to the pane below *  
`→/l` move to the right pane *  
`↑/k` move to the pane above *
`;` toggle last active pane
`q` show pane numbers  
`o` toggle between panes  
`}` swap with next pane  
`{` swap with previous pane  
`!` break the pane out of the window  
`x` kill the current pane  
`w` open a panel to navigate across windows in multiple sessions, Q to exit.  
`exit` or `Ctrl` + `d` to close pane
`!` convert pane into a window

### Resize

Use: tmux + cmd from bash command line, or C-b then : from bar

`: resize-pane -D` (Resizes the current pane down)  
`: resize-pane -U` (Resizes the current pane upward)  
`: resize-pane -L` (Resizes the current pane left)  
`: resize-pane -R` (Resizes the current pane right)  
`: resize-pane -D 20` (Resizes the current pane down by 20 cells)  
`: resize-pane -U 20` (Resizes the current pane upward by 20 cells)  
`: resize-pane -L 20` (Resizes the current pane left by 20 cells)  
`: resize-pane -R 20` (Resizes the current pane right by 20 cells)  
`: resize-pane -t 2 20` (Resizes the pane with the id of 2 down by 20 cells)  
`: resize-pane -t -L 20` (Resizes the pane with the id of 2 left by 20 cells)  

### Copy Mode 
  
`[` Enter copy mode to scroll in pane
`↑` scroll up
`↓` scroll down
`q` to quit copy mode
`g` go to top line
`G` go to bottom line

To copy text:
1. Press `Space` to start selection.
2. Move cursor to end, then press `Enter`.
3. Paste with `Ctrl + b` then `]`.
### Miscellaneous  
  
`t` show the time in current pane


## ~/.tmux.conf

```shell
# ~/.tmux.conf

# Easier prefix key (optional)
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix

# Mouse support
set -g mouse on

# Enable 256 colors
set -g default-terminal "screen-256color"

# Set window index starting from 1
set -g base-index 1
setw -g pane-base-index 1

# Shorter command delay
set -sg escape-time 0

# Status bar styling
set -g status-bg black
set -g status-fg white
set -g status-left '[#S]'
set -g status-right '#(date +"%H:%M %d-%b-%y")'
```
## Links

* [Tmux Cheat Sheet & Quick Reference](https://tmuxcheatsheet.com/)
