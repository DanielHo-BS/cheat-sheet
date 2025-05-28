# Tmux User Guide

Tmux is a terminal multiplexer. It lets you manage multiple sessions, windows, and panes in one terminal.

- **Prefix key:** `Ctrl + b` (by default)

## Understanding Tmux Concepts

### Basic Components

- **Session:** A collection of windows and panes. Keeps your work organized and persistent, even if you disconnect.
- **Window:** Like a tab within a session. Each window can have one or more panes.
- **Pane:** A split area within a window. You can run different commands in each pane.

### Visual Structure

```
Session
 ├── Window 1
 │    ├── Pane A
 │    └── Pane B
 ├── Window 2
 │    └── Pane C
 └── Window 3
      ├── Pane D
      ├── Pane E
      └── Pane F
```

### Real-World Analogy

Think of Tmux like a modern workspace:

| Tmux Concept | Real-World Analogy | Description |
|--------------|-------------------|-------------|
| Session | Project Folder | Contains all your terminal activity; persists even when you close your terminal |
| Window | Browser Tab | Each window is like a separate tab where you can work on different tasks |
| Pane | Split Screen | Multiple terminal views within a window, like having multiple apps side by side |

---

## Sessions

| Command                        | Description                  |
|--------------------------------|------------------------------|
| `tmux`                         | Start a new session          |
| `tmux new -s [name]`           | Create a new named session   |
| `tmux ls`                      | List all sessions            |
| `tmux a` or `tmux attach`      | Attach to the last session   |
| `tmux a -t [name]`             | Attach to a named session    |
| `tmux kill-session -t [name]`  | Kill a named session         |
| `tmux switch -t [name]`        | Switch to a session          |

---

## Windows (after Prefix)

| Command   | Description              |
|-----------|--------------------------|
| `c`       | Create a new window      |
| `,`       | Rename the window        |
| `w`       | List and choose windows  |
| `n` / `p` | Next / previous window   |
| `&`       | Close the window         |

---

## Panes (after Prefix)

| Command         | Description                        |
|-----------------|------------------------------------|
| `%`             | Split pane vertically              |
| `"`             | Split pane horizontally            |
| Arrow keys/hjkl | Move between panes                 |
| `x`             | Close the current pane             |
| `z`             | Maximize/restore current pane      |
| `Ctrl + o`      | Rotate panes                       |
| `Space`         | Change pane layout                 |

---

## Copy & Scroll Mode (after Prefix)

| Command              | Description                        |
|----------------------|------------------------------------|
| `[`                  | Enter scroll/copy mode             |
| `q`                  | Exit scroll/copy mode              |
| Mouse/Arrow keys     | Scroll up/down                     |
| `Enter`              | Select text (in copy mode)         |

---

## Common Tmux Configurations

Add these lines to your `.tmux.conf` file for useful settings:

```tmux
# Change prefix to Ctrl + a
unbind C-b
set -g prefix C-a
bind C-a send-prefix

# Enable mouse support
set -g mouse on

# Increase scrollback buffer
set -g history-limit 10000

# Use vi mode for copy
setw -g mode-keys vi

# Auto-switch to new pane after split
bind | split-window -h \; select-pane -R
bind - split-window -v \; select-pane -D
```

---

## Tips

- **Keep sessions running:** Tmux keeps your tasks (like tests or model training) running even if you close the terminal.
- **Name your sessions/windows:** Makes it easier to organize different tasks.
- **Combine tmux with SSH:** Great for remote development and testing.

---

## References

- [Tmux Wiki](https://github.com/tmux/tmux/wiki)