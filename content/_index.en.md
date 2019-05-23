---
title: "PILMBC103 Best practices on remote storage and computing systems"
---

# Requirements


- Your own computer: Linux or MacOSX. If you have Windows, follow this guideline: https://docs.docker.com/docker-for-windows/ 
- Have an editor for programming, install _Atom_: https://atom.io/
- Install sshfs: MACOSX (download and install the _two_ packages you see here: https://osxfuse.github.io/). LINUX (ubuntu, debian: sudo apt-get install sshfs)
- know what is a terminal or
	-  make section 1 of this tutorial: [Learn Enough Command Line to Be Dangerous |  Learn Enough to Be Dangerous](https://www.learnenough.com/command-line-tutorial/basics)
	- [Navigating the Terminal: A Gentle Introduction - YouTube](https://www.youtube.com/watch?v=Vhcx4KJbtes&feature=youtu.be)
	- play this game done at MIT: [Terminus](http://web.mit.edu/mprat/Public/web/Terminus/Web/main.html)
- eofe5 credentials: If you don't have one follow this link: https://engaging-web.mit.edu/request_account. Choose your PI names under `Group` droplist. You need to know your user name and the `eofe-key` file that you get after completion of your account.



# Goal


* connect to a remote server to transfer data securely: eofe5
* connect to a cluster and keep the session alive: eofe5
* transfer data
* learn how to send jobs to the queue
* learn how to start interactive jobs to test quick scripts or test data
