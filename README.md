# ccs

Claude control sessions: open Claude Code sessions in tabs of a terminal window (tmux on a private socket) and type prompts into them.

## Install

```bash
ln -s "$PWD/ccs" ~/.local/bin/ccs
```

Needs `tmux`, `jq`, `gnome-terminal` and `claude`.

## Usage

```
Claude control sessions: open Claude sessions in tabs of a terminal window and type prompts into them.
  ccs open [-d dir] [-n name] [-M model] [-e effort] [-m permission-mode] [-k] [prompt...]
                                                                new tab running claude
  ccs send <name> [prompt...|-]                                 type a prompt into a session (- reads stdin)
  ccs peek <name> [lines]                                       print what the session's screen shows
  ccs list                                                      sessions opened by ccs, with status
  ccs show <name>                                               switch to the session's tab, reopening its window
  ccs close <name>                                              /exit the session and close its tab
  ccs done                                                      from inside a tab: close it once its turn ends
  ccs control [claude args...]                                  start the control session here
Sessions run in tmux on a private socket, so typed prompts arrive as if typed at the keyboard.
Sessions opened from the same control session share one tmux session (one terminal window),
one tmux window (tab) each; outside a control session they share the group "main".
Every session, the control one included, runs with Remote Control under its own name.
Run from a Claude session, `ccs open` tells the new session to report back to it with SendMessage
and then run `ccs done`, which closes the tab; -k keeps the tab open after the report.
```
