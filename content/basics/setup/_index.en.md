---
title: Set up
weight: 10
disableToc: true
tags: ["ssh", "rsa", "connection"] 
---

## set up environment

* Open a terminal: You need to know about these commands: `ls` , `cd folder`, `cd ..`,  `ctrl+d`
* Open your editor: Atom or your favorite text plain editor.

## How to connect to servers

* password
* encrypted key files: how to create your own [keys](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)

## setup your credentials

Look for the `eofe-key` file. Normally is good to save it inside the `~.ssh/` folder so it is private. Copy the file to that location:

`mkdir -p ~/.ssh`

`cp PATH_TO_EOFE_KEY/eofe-key ~/.ssh/.`

Check the file permission: `ll ~/.ssh/eofe-key`

It should show something like this:

`-rw-------@ 1 lpantano  staff   1.7K May 23 10:32 /Users/lpantano/.ssh/eofe-key`

If not, type this:

`chmod 600 ~/.ssh/eofe-key`

Then add the following lines to this file `~/.ssh/config` (Open it with Atom editor if you don't have experience editing from the terminal). This file contains information on how to connect to different computers: like `username`, `hostname` ...

```
Host mit
Hostname eofe5.mit.edu
User lpantano
IdentityFile ~/.ssh/eofe-key
UseKeychain yes
```

{{% notice warning %}}
UseKeychain, only in OSX systems
{{% /notice %}}

{{% notice info %}}
change the username to yours
{{% /notice %}}

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


{{% notice warning %}}
You need to get this working to move forward
{{% /notice %}}

### Create working folder

`mkdir pilm103` 

### Shared folders

Every group in PILM has a private and shared space folder:

```
ls /net/eofe-data004/mnt/pool/picower001/
```

inside your group folder, you have the following structure:

- user1
- user2
- user3
- lab_shared
  - user1
  - user2
  - user3