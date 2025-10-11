# PWN College - Linux Luminarium: Terminal Multiplexing Challenges

## Challenge 1: Detaching and Reattaching with screen

Learn to use screen's detach and reattach functionality. Launch screen, detach from it, run /challenge/run, then reattach to see the flag.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- used screen

Use this blob for pasting commands you've run:
```sh
$ screen
```

### Flag: 

```
pwn.college{wtb_NT4IMc37x1rh8rvAo3ElGcl.0VN4IDOxwiN1EzNzEzW}
```

### Notes:
- `screen` launches a new screen session
- Detach: Press `Ctrl-A`, then `d` (hold Ctrl+A, release, press d)
- `screen -r` reattaches to the session
- You'll see `[detached from...]` message when successful
- Screen keeps running in background when detached
- This is crucial for maintaining sessions over unstable connections
- Ctrl-A is screen's activation key for all shortcuts

---

## Challenge 2: Multiple screen Sessions

Work with multiple screen sessions. Three sessions have been created - one contains the flag, the other two are decoys. Find the right one!

### Solution:

- attached and detached from a screen
- 
- 

Use this blob for pasting commands you've run:
```sh
$ screen 
$ /challenge/run
$ screen -r
```

### Flag: 

```
pwn.college{w3prcoM9QfUqV-W8hmyF6P7B8qR.0lN4IDOxwiN1EzNzEzW}
```

### Notes:
- `screen -ls` lists all screen sessions
- Sessions identified as: `PID.name` (e.g., `23847.mysession`)
- `screen -r name` or `screen -r PID` reattaches to specific session
- Detach from each session (Ctrl-A d) before trying the next
- Check each session until you find the flag
- Multiple sessions useful for organizing different tasks

---

## Challenge 3: Multiple Windows in screen

Learn to use multiple windows within a single screen session. Create and navigate between windows using screen's keyboard shortcuts.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- 
- 
- 

Use this blob for pasting commands you've run:
```sh
$ screen -ls
$ screen -r session_e1040a45ab9a9832 
$ screen -r session_87c42633ac330e9c
```

### Flag: 

```
pwn.college{kMLRF_NzJLc-cok9axONiG1xiFr.01N4IDOxwiN1EzNzEzW}

```

### Notes:
- Inside screen, windows work like browser tabs
- `Ctrl-A c` creates a new window
- `Ctrl-A n` switches to next window
- `Ctrl-A p` switches to previous window
- `Ctrl-A "` lists all windows (can select from list)
- `Ctrl-A 0-9` jumps to window number 0-9
- `Ctrl-A A` renames current window
- Windows stay within same session

---

## Challenge 4: Splitting Panes in screen

Learn to split your screen into multiple panes for side-by-side work.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- changed pages in screen
- 
- 

Use this blob for pasting commands you've run:
```sh
$ screen -r
(ctrl) + A + 0
```

### Flag: 

```
pwn.college{UETF0J97SDNnIPYO3gTTz1-aKVk.0FO4IDOxwiN1EzNzEzW}
```

### Notes:
- `Ctrl-A S` splits screen horizontally (capital S)
- `Ctrl-A |` splits screen vertically
- `Ctrl-A Tab` moves between panes
- `Ctrl-A c` creates new shell in current pane
- `Ctrl-A X` closes current pane (capital X)
- `Ctrl-A Q` closes all panes except current (capital Q)
- Panes allow viewing multiple things simultaneously

---

## Challenge 5: Detaching and Reattaching with tmux

Learn tmux basics - detaching and reattaching. Launch tmux, detach, run /challenge/run, then reattach.

### Solution:
- detached and reattached from tmux
- 
- 

Use this blob for pasting commands you've run:
```sh
$ tmux
ctrl + B + d
$ /challenge/run
$ tmux a

```

### Flag: 

```
pwn.college{MB0gBCA2cob0jq7AIk-O4NwwXMx.0VO4IDOxwiN1EzNzEzW}
```

### Notes:
- `tmux` launches a new tmux session
- Detach: Press `Ctrl-B`, then `d` (tmux uses Ctrl-B, not Ctrl-A!)
- `tmux attach` or `tmux a` reattaches to session
- You'll see `[detached (from session...)]` message
- tmux is more modern than screen
- Ctrl-B is tmux's command prefix
- Similar functionality to screen but different keybindings

---

## Challenge 7: Multiple Windows in tmux

Learn to use multiple windows within a single tmux session.

### Solution:

Describe your thought process and solve, write as much as possible with steps:

- 
- 
- 

Use this blob for pasting commands you've run:
```sh
$ 
$ 
$ 
```

### Flag: 

```
pwn.college{ }
```

### Notes:
- `Ctrl-B c` creates a new window
- `Ctrl-B n` next window
- `Ctrl-B p` previous window
- `Ctrl-B w` list windows (interactive selection)
- `Ctrl-B 0-9` jump to window number
- `Ctrl-B ,` rename current window
- `Ctrl-B &` kill current window
- Windows shown in bottom status bar

---

