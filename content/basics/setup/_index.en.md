---
title: Set up
weight: 10
disableToc: true
---

## set up environment

* Open a terminal: You need to know about these commands: `ls` , `cd folder`, `cd ..`,  `ctrl+d`
* Open your editor: Atom or your favourite text plain editor.

## setup your credentials

Look for the `eofe-key` file. Normally is good to save it inside the `~.ssh/` folder so it is private. Copy the file to that location:

`cp PATH_TO_EOFE_KEY/eofe-key ~/.ssh/.`

Check the file permision: `ll ~/.ssh/eofe-key`

It should show something like this: `-rw-------@ 1 lpantano  staff   1.7K May 23 10:32 /Users/lpantano/.ssh/eofe-key`

If not, type this:

`chmod 600 ~/.ssh/eofe-key`

Then add the following lines to this file `~/.ssh/config` (Open it with Atom editor). This file contains information on how to connect to different computers: like `username`, `hostname` ...

```
Host mit # alias
Hostname eofe5.mit.edu # full hostname
User lpantano
IdentityFile ~/.ssh/eofe-key
```

This will do that you can connect to that space just by doing `ssh mit` and if you are on:

* mac OSX: you will be asked for the password once and it'll save it until you restart your computer
* linux: things are not that nice here, but it is not that bad :). You can do the following to get ask by the password only once.
 
```
eval `ssh-agent`
ssh-add ~/.ssh/eofe-key
# type the passphrase you used when registering your account
```

### Test your connection

Now is the time to try and connect:

`ssh mit`

> You need to get this working to move forward.

### Create working folder

`mkdir work_lpantano` 

> change the user name to match yours
