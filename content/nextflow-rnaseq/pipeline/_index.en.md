---
title: RNAseq pipeline
weight: 25
disableToc: true
---

* Source code: https://github.com/pilm-bioinformatics/pipelines-nf-rnaseq
* Documentation: https://pilm-bioinformatics.github.io/pipelines-nf-rnaseq/
* Public dataset browser: https://ewels.github.io/sra-explorer/#

## Scheme

Pipeline Overview: https://pilm-bioinformatics.github.io/pipelines-nf-rnaseq/output.html

![](pipeline_dag.png)

* The pipeline is defined in the `main.nf` file
* The config files are defined in: `nextflow.config` and all the files in the `conf` folder.

## Logging

![](nf-running.png)

## Important parameters

Some parameters that have an important impact to the computer resources requirements and time execution.

* `--pseudo_aligner salmon`: to run best practices for gene/transcript quantification
* `--singleEnd`: in case of not being paired dataset
* `--aligner hisat2`: to reduce the resources during alignment (if salmon is on)
* `--skipGenebodyCoverage`: long process that gives the same information than Qualimap
* `--skipDupRadar`: long process that gives similar information than Qualimap
* `--skipPreseq`: long process that gives similar information than Qualimap
* `--skipRseQC`: long process that gives similar information than Qualimap

All parameters are defined at `nextflow.config`

## Reports

* [output explanation](https://pilm-bioinformatics.github.io/pipelines-nf-rnaseq/output.html)
* execution_timeline.html
* execution_report.html
* results_description.html
* software_versions.csv

