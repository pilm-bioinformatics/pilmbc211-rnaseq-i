---
title: Set up
weight: 10
disableToc: true
tags: ["ssh", "rsa", "connection"] 
---

## Set up environment

* Open a terminal: You need to know about these commands: `ls` , `cd folder`, `cd ..`,  `ctrl+d`
* Open your editor: Atom or your favorite plain text editor.

## How to connect to servers

* encrypted key files: how to create your own [keys](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)
* password

## Setup your credentials

Look for the `eofe-key` file. The standard location is inside the `~.ssh/` folder with tight permissions, so it is private and only your user has access to it. Copy the file to that location:

Create the folder if it doesn't exists: `mkdir -p ~/.ssh`

`-rw-------@ 1 lpantano  staff   1.7K May 23 10:32 /Users/lpantano/.ssh/eofe-key`

Move the file to the location: `mv PATH_TO_EOFE_KEY/eofe-key ~/.ssh/.`

Check the file's permission: `ll ~/.ssh/eofe-key`

The file's permission should look like this (look at the left hand side, the rw part):

`-rw-------@ 1 lpantano  staff   1.7K May 23 10:32 /Users/lpantano/.ssh/eofe-key`

If not, type this:

`chmod 700 ~/.ssh/`
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

This will allow you to connect just by issuing `ssh mit` and if you are on:

* mac OSX: you will be asked for the password once and it'll save it until you restart your computer.
* linux: things work the same way if you are on a graphic session, otherwise you need a bit more work, it is not that bad :). You can do the following to be asked by the password only once.
 
```
eval `ssh-agent`
ssh-add ~/.ssh/eofe-key
```
{{% notice info %}}
Type the password you gave during registration
{{% /notice %}}

### Test your connection

Now is the time to try and connect:

`ssh mit`


{{% notice warning %}}
You need to get this working to move forward
{{% /notice %}}

### Create working folder at the mit server

`mkdir pilm103` 

### Group shared folders

Every group at PILM has a private and shared space folder:

```
ls /net/eofe-data004/mnt/pool/picower001/
```

You should see this:

```
[lpantano@eofe5:~]
|$ ls /net/eofe-data004/mnt/pool/picower001/
general  heimanlab  lhtsailab  littletonlab  surlab  tyelab  wilsonlab  xulab
```

inside your group folder, you have the following structure:

- user1
- user2
- user3
- lab_shared
  - user1
  - user2
  - user3
