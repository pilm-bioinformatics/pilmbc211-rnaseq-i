---
title: File transfer
weight: 20
disableToc: false
---

## mount the server

* Open a new terminal.

A good way to interact with remote storage is to mount the server as a folder in your computer. For that we need the `sshfs` command (See requirements to know how to install it).

```
mkdir -p ~/mnts/mit
sshfs mit:. ~/mnts/mit -o delay_connect -o follow_symlinks
```

Now you should be able to see your space:

`ls ~/mnts/mit`

## rsync command

This is the best tool to use to transfer files. The main advantages:

* include only some files
* exclude some files
* copy the file metadata
* dry-run: you can check what is going to do
* it checks the file content

The basic command is:

`rsync [options] origin target`

Normally `origin` or `target` is a local folder or a remote computer.

### test file

* Open a new terminal

Download the following file:

```
cd ~/Downloads
mkdir work && cd work
curl -L https://github.com/nf-core/test-datasets/raw/smrnaseq/testdata/sample_1.fastq.gz -o sample.fastq.gz
cd ..
```

### data in/out

In this case, we will copy from our local computer to the MIT storage cluster.

`rsync -avn work/sample.fastq.gz mit:~/pilm103`

Options explained:

* a: all files, keeping owner, timestamp, recursive
* v: verbose on, to know what files are being copying
* P: progess
* n: dry-run, so there is no copy action 

Alternatives:

* full folder: `rsync -avn work mit:~/pilm103`
* full folder ignoring that folder: `rsync -avn work/ mit:~/pilm103`

If what we see makes sense, then we repeat it without the `-n` option. We can add `-P` to see the progress of the transfer.

`rsync -avP work mit:~/pilm103`

Move to the terminal where you did the first connection to the server and check if you see the file now in your home directory.

