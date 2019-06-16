---
title: RNAseq in Open Mind
weight: 35
disableToc: true
---

{{% notice warning %}}
This needs to have an account in OpenMind
{{% /notice %}}

1. Open the terminal

2. `ssh username@openmind7.mit.edu`

3. `cd /om/user/username`

4. `mkdir rnaseq-pilm211`

6. `cd rnaseq-pilm211`

7. `ls /om/group/pilm/test_data/mouse`

8. `cp /om2/group/pilm/master-scripts/pipelines-nf-rnaseq/* .` and `cp /om2/group/pilm/master-scripts/config/om-profile.config .`

9. `vim om-job.slurm`

modify the line to look like this: (remove the `#` character to uncomment the line and it actually runs)

```
#!/bin/bash
#SBATCH -N 1
#SBATCH -c 1
#SBATCH --mem=4000
#SBATCH -t 0-23:00:00
#SBATCH -J "rnaseq"
#SBATCH -e job.e
#SBATCH -o job.o
## SBATCH --mail-type=END,FAIL # this line is commented
## SBATCH --mail-user=user@mit.edu  # this line is commented

export PATH=/om2/group/pilm/conda3/envs/nf-core-rnaseq-1.4dev/bin:$PATH
export PATH=/om2/group/pilm/bin:$PATH

if [ ! -f "om-profile.config" ] ; then
  cp  /om2/group/pilm/master-scripts/config/om-profile.config .
fi
if [ ! -f "om-rnaseq" ] ; then
  cp  /om2/group/pilm/master-scripts/pipelines-nf-rnaseq/om-rnaseq.config .
fi

## Example pipeline
GENOME=/om/group/pilm/genomes/Mmusculus/GRCm38.96/GRCm38.96.config
#GENOME=/om/group/pilm/genomes/Mmusculus/GRCh38.96/GRCh38.96.config

# Add --singleEnd if true
nextflow run /om2/group/pilm/pipelines/dev/pipelines-nf-rnaseq -c om-profile.config -c om-rnaseq.config -c $GENOME  --reads "/om/group/pilm/test_data/mouse/*_{1,2}.fastq.gz" -resume
```

## Default parameters

The PILM pipeline runs under some default parameters in the following files.

### General

`om-profile.config`

```
executor {
  queueSize=24
}

process {

  // Global process config
  executor = 'slurm'
  // queue = ''
  cpus = 6
  // clusterOptions = { "--qos=" }

}
```

* `queueSize` is the number of jobs running at the same time.
* `cpus` the number of cores by default to use by process

### RNAseq

`om-rnaseq.config`

```
params {
  igenomes_base = '/om/group/pilm/genomes'
  skipRseQC = true
  skipGenebodyCoverage = true
  skipPreseq = true
  skipDupRadar = true
  aligner = 'hisat2'
  pseudo_aligner = 'salmon'
}
```

