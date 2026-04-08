## Konsole for Ubuntu

Since you're using **Konsole** on Ubuntu (likely under GNOME or KDE), you'll find it much more feature-rich than Xterm.
It supports split views, profiles, and advanced search—all things that require a bit of a "roadmap" to navigate.

Here is your full Konsole cheatsheet, categorized for quick access.

---

### 1. Essential Window & Tab Management

These are the most common shortcuts you'll use daily to keep your workflow organized.

| Action                    | Shortcut                          |
| :------------------------ | :-------------------------------- |
| **New Tab**               | `Ctrl` + `Shift` + `T`            |
| **New Window**            | `Ctrl` + `Shift` + `N`            |
| **Close Tab**             | `Ctrl` + `Shift` + `W`            |
| **Next / Previous Tab**   | `Shift` + `Right` / `Left`        |
| **Move Tab Left / Right** | `Ctrl` + `Alt` + `Left` / `Right` |
| **Detach Current Tab**    | `Ctrl` + `Shift` + `L`            |
| **Toggle Full Screen**    | `F11`                             |

---

### 2. The "Hidden" Split View (Multiplexing)

Konsole can split your window into multiple panes without needing `tmux` or `screen`.

* **Split View Left/Right:** `Ctrl` + `(`
* **Split View Top/Bottom:** `Ctrl` + `)`
* **Expand/Shrink Current View:** `Ctrl` + `Shift` + `]` / `[`
* **Maximize Current View:** `Ctrl` + `Shift` + `E`
* **Focus Next Pane:** `Tab` (while holding `Ctrl` + `Shift`)

---

### 3. Text & Interaction

Unlike the standard Ubuntu terminal, Konsole has a unique **Keyboard Selection Mode** that lets you copy text without touching your mouse.

* **Copy / Paste:** `Ctrl` + `Shift` + `C` / `V`
* **Search Text:** `Ctrl` + `Shift` + `F`
* **Clear & Reset Terminal:** `Ctrl` + `Shift` + `K`
* **Enlarge / Shrink Font:** `Ctrl` + `+` / `-`
* **Enter Keyboard Selection Mode:** `Ctrl` + `Shift` + `D`
  * *In this mode, use `h`, `j`, `k`, `l` (Vim keys) to move and `v` to start selecting.*

---

### 4. Advanced Monitoring Tools

Konsole can "watch" your terminal for you. This is perfect for long-running compiles or log files.

* **Monitor for Activity:** `Ctrl` + `Shift` + `A` (Alerts you when something happens in a background tab).
* **Monitor for Silence:** `Ctrl` + `Shift` + `I` (Alerts you when a process *stops* outputting text).
* **Monitor for Prompt:** `Ctrl` + `Shift` + `R` (Alerts you when a command finished and you're back at the `$` prompt).

---

### 5. Configuration & Profiles

If the menu bar is hidden (common in some Ubuntu themes), use these to get back to your settings:

* **Show/Hide Menu Bar:** `Ctrl` + `Shift` + `M`
* **Open Settings/Profile Editor:** `Ctrl` + `Shift` + `,`
* **Rename Current Tab:** `Ctrl` + `Alt` + `S`

> **Pro Tip:** If you want to use your **Nerd Fonts** or custom colors (like the ones you use in Neovim), you can create a new **Profile** in `Settings > Configure Konsole`. Profiles allow you to have different terminal styles for different tasks (e.g., a "Development" profile with low transparency and a "Monitoring" profile with bright red text).
