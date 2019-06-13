---
title: RNAseq test
weight: 30
disableToc: true
---

{{% notice warning %}}
This needs to have Docker and Nextflow installed
{{% /notice %}}

1. Open to the terminal

2. `docker pull nfcore/rnaseq:dev`

3. `nextflow run pilm-bioinformatics/pipelines-nf-rnaseq -profile docker,test`

