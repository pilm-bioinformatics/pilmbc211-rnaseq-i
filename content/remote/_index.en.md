---
title: Remote actions
weight: 10
pre: "<b>2. </b>"
chapter: true
---

### Chapter 2

# Remote actions

Here, you will learn how to interact with remote computers, transfer files and send jobs to a cluster.

```mermaid
graph LR;
  A[Local computer] -->|connection| B{credentials?}
    B -->|password| C[semi-secure]
    B -->|keys| D[secure]
    C --> E[Server-login node]
    D --> E[Server-login node]
    E -->|job1| F[compute node 1]
    E -->|job2| G[compute node 2]
```

How you jobs get schedule:

- According to the requested resources/ available resources
- According your **Fairshare** score:
  - number of jobs/resources requested in the past
  - precision of the resources requested vs needed
  
## Summary

- transfer
  - `sshfs` to mount remote folders
  - `rsync` to transfer files
- cluster
  - `srun` for interactive or on the spot Jobs
  - `sbatch` for automatize Jobs
  - `-c` to aks for number of cores
  - `--mem` to ask for memory in **Mb** (2000 is 2GB)
  - `--time=d-hh:mm:00` to define limit duration