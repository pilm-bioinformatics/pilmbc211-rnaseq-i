---
title: Nextflow
weight: 15
disableToc: true
---

[Nextflow](https://www.nextflow.io/) enables scalable and reproducible scientific workflows using software containers. It allows the adaptation of pipelines written in the most common scripting languages. 

Documentation: https://www.nextflow.io/docs/latest/index.html

[nf-core](https://nf-co.re/): repository of [pipelines](https://nf-co.re/pipelines)

## Example of workflow

```
#!/usr/bin/env nextflow

params.str = 'Hello world!'

process splitLetters {

    output:
    file 'chunk_*' into letters mode flatten

    """
    printf '${params.str}' | split -b 6 - chunk_
    """
}


process convertToUpper {

    input:
    file x from letters

    output:
    stdout result

    """
    cat $x | tr '[a-z]' '[A-Z]'
    """
}

result.println { it.trim() }
```

## Errors

Nextflow is the most user-friendly workflow to find out why something is not working.

In a case of an error, you will see RED text with the error that the tool found.

At the end, it will show the working directory, something like this:

`/om/user/lpantano/test-pilm211/work/1a/2556d7bc7ff6773c41d37968e13f5f`

In that folder you will find the next important files:

* `.command.sh`: the command that produced the error
* `.command.our/err/log`: information related to the error

This is an example of an error due to a file is corrupted:

```
SUMMARISING RUN PARAMETERS
==========================
Input filename: SRR9166086_D5_1.fastq.gz
Trimming mode: paired-end
Trim Galore version: 0.6.1
Cutadapt version: 2.3
Number of cores used for trimming: 1
Quality Phred score cutoff: 20
Quality encoding type selected: ASCII+33
Adapter sequence: 'CTGTCTCTTATA' (Nextera Transposase sequence; auto-detected)
Maximum trimming error rate: 0.1 (default)
Minimum required adapter overlap (stringency): 1 bp
Minimum required sequence length for both reads before a sequence pair gets removed: 20 bp
Running FastQC on the data once trimming has completed
Output file(s) will be GZIP compressed

Writing final adapter and quality trimmed output to SRR9166086_D5_1_trimmed.fq.gz


  >>> Now performing quality (cutoff '-q 20') and adapter trimming in a single pass for the adapter sequence: 'CTGTCTCTTATA' from file SRR9166086_D5_1.fastq.gz <<<
10000000 sequences processed
This is cutadapt 2.3 with Python 3.6.7
Command line parameters: -j 1 -e 0.1 -q 20 -O 1 -a CTGTCTCTTATA SRR9166086_D5_1.fastq.gz
Processing reads on 1 core in single-end mode ...
cutadapt: error: Error in FASTQ file at line 64953264: Length of sequence and qualities differ


Cutadapt terminated with exit signal: '256'.
Terminating Trim Galore run, please check error message(s) to get an idea what went wrong...

Work dir:
/om/user/lpantano/test-pilm211/work/1a/2556d7bc7ff6773c41d37968e13f5f

Tip: you can try to figure out what's wrong by changing to the process work dir and showing the script file named `.command.sh`

-- Check '.nextflow.log' file for details
```

If you run any of our pipelines or nf-core pipelines and you find an error, please submit an issue first here:https://github.mit.edu/PILM-bioinformatics/support/issues
