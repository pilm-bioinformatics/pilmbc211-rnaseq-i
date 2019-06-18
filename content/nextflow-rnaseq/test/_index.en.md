---
title: RNAseq test
weight: 30
disableToc: true
---

{{% notice warning %}}
This needs to have Docker and Nextflow installed
{{% /notice %}}

1. Start docker app and open the terminal

2. `docker pull nfcore/rnaseq:dev` this will download the software container

3. `./nextflow pull pilm-bioinformatics/pipelines-nf-rnaseq -r master`

4. `./nextflow run pilm-bioinformatics/pipelines-nf-rnaseq -profile docker,test` this run the pipeline with the software container we have defined previously and the test data defined by the pipeline.


### Container definition

What software container to use is defined inside `nextflow.config` in the variable: `process.container = 'nfcore/rnaseq:dev'`.

{{% notice note %}}
Nextflow will download by itself the software container if it is not installed.
{{% /notice%}}

What test to run is defined in the file `conf/test.config`.
