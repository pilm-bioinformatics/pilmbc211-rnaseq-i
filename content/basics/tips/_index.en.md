---
title: Permanent connection
weight: 15
disableToc: true
---

## tricks to use sessions inside teminal: tmux 

Learn more about [tmux](https://thoughtbot.com/blog/a-tmux-crash-course), but basically is a way to leave alive your terminal environment in a remote computer.

For instance, imaging you use an interactive job to copy a lot of files over. If you lose the connection to the remote computer, that session ends, and the transfer will be killed. As well, it allows to have multiple sessions with a single connection.

Communication with **tmux** is by the use of two keys in the keyboard: `Ctrl + b`. That is called the *prefix*, and is the trigger to get **tmux** listen to what you want to do next: for instance create a new windows, or change between windows, etc... 

When you are in the remote computer, type:

```
tmux new -s s1
```

Then create another window:

```
prefix + c
```

Name windows:

```
prefix + ,
```

Now type `other` and press `Enter`

Move to among windows:

```
prefix + 0
prefix + 1
```

detach the session and come back:

```
prefix + d
tmux a -t s1
```

Disconnect from the computer and come back:

```
ctrl + d
ssh mit
tmux -a -t s1
```

