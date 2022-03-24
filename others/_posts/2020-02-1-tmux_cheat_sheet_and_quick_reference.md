---
layout: post
title: Tmux cheat Sheet & Quick Reference
description: >
  `tmux` lets you keep things running persistently on servers, so you can disconnect and connect as needed without interrupting tasks that are in progress.
---

## start new:

```bash
tmux
```

## start new with session name:

```bash
tmux new -s session_name
```

## list session

```bash
tmux ls
```

## Attach to named

```bash
tmux a -t session_name 
```

## Kill session

```bash
tmux kill-session -t session_name
```

## Rename session

```bash
Ctrl+b $
```
## Detach from session

```bash
Ctrl+b d
```

## Create Window

```bash
Ctrl+b c
```

## Rename current windows

```bash
Ctrl+b ,
```

## Close current windows

```bash
Ctrl+b &
```

## Previous windows 

```bash
Ctrl+b p
```

## Next windows

```bash
Ctrl+b n
```

## Switch/select window by number

```bash
Ctrl+b 0...9
```

## Toggle last active window

```bash
Ctrl+b l
```

## Toggle last active pane

```bash
Ctrl+b ;
```

## Split pane with horizontal layout

```bash
Ctrl+b %
```

## Move the current pane left

```bash
Ctrl+b {
```

## Toggle between pane layout
  
```bash
Ctrl+b Spacebar
```

## Switch to next pane

```bash
Ctrl+b o
```




