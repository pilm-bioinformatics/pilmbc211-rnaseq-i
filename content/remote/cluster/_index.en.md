---
title: Usage of cluster
weight: 25
disableToc: false
tags: ["slurm", "cluster"] 
---

## most used commands on a cluster

Full tutorial to learn [hpc](https://epcced.github.io/hpc-intro/010-hpc-concepts/). A cluster has two types of computers:

* login node
* computing node

### interactive jobs in eofe5

```
srun --time=0:1:00 --mem=200  -c 1 --pty --partition=sched_any /bin/bash
```

{{% notice info %}}
Notice how the computer names has change to something like `nodeXXX`
{{% /notice %}}


`md5sum pilm103/work/*gz`

`ctrl-d` to exit from the computing node.

Exercise: send md5sum to interactive

```
srun --time=0:1:00 --mem=200 -c 1 --partition=sched_any md5sum pilm103/work/sample.fastq.gz
```

### Batch jobs in eofe5

Download the [script](https://gist.githubusercontent.com/lpantano/fb4986dacd57c8cbb0c58db0d2d05ad0/raw/bde0bd504cdeb8d904788903e0c08b0b84035d0d/run_test.slurm) from here: 

`wget https://gist.githubusercontent.com/lpantano/fb4986dacd57c8cbb0c58db0d2d05ad0/raw/bde0bd504cdeb8d904788903e0c08b0b84035d0d/run_test.slurm`

It looks like that:

```
#!/bin/bash
#SBATCH -N 1
#SBATCH -c 1
#SBATCH --mem=200
#SBATCH -t 00:1:00
#SBATCH -J "init"
#SBATCH -e run.e
#SBATCH -o run.o
## SBATCH --mail-type=END,FAIL # this line is commented
## SBATCH --mail-user=you@mit.edu  # this line is commented

sleep 60 # wait 60 seconds
md5sum pilm103/work/sample.fastq.gz
```

You can check that by typing `cat run_test.slurm`.

Exercise:  send md5sum to queue

```
sbatch run_test.slurm
```

### Check your jobs:

```
squeue -u USERNAME
```

### Check you past jobs

```bash
 sacct -j $JOBID --format=User,JobID,Jobname,partition,state,time,start,end,elapsed,MaxRss,MaxVMSize,nnodes,ncpus,nodelist
```

## OpenMind cluster


### Interactive Jobs

```
srun --time=0:15:00 --mem=2000 -c 1  --pty  /bin/bash
```

### Batch Jobs

```
#!/bin/bash
#SBATCH -N 1
#SBATCH -c 1
#SBATCH --mem=200
#SBATCH -t 24:00:00
#SBATCH -J "init"
#SBATCH -e run.e
#SBATCH -o run.o
## SBATCH --mail-type=END,FAIL # this line is commented
## SBATCH --mail-user=you@mit.edu  # this line is commented

sleep 60 # wait 60 seconds
```
