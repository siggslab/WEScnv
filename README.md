# README

This is a workflow for calling CNV in WES data, and is currently under active development.

It utilises Docker/Singularity and Nextflow, with backend support for SGE and GoogleCloud.

## Docker

This workflow uses several Docker images, with the philosophy of one tool -> one image.
Dockerfiles are listed under each tool subdir in the Docker folder.

### Building Docker images

e.g. commands for building and testing Docker images


`docker build --no-cache -t joshmschmidt/wescnv:0.0.1 .`


`docker run --rm -ti joshmschmidt/wescnv:0.0.1  /bin/bash`



### Profiles

There are some basic profiles that can be selected, located in conf/

garvan.config provides a nice basic sge env template.

*TODO:*

dynamic resource, particulalry memory and TMPDIR on cluster.

`module load nextflow`

`nextflow run wescnv.nf -resume -profile garvan --batch WES-2528 --inputFile WES-2528-inputFiles.txt --reference_fasta /share/ScratchGeneral/jossch/reference/gatk/hg38/Homo_sapiens_assembly38.fasta --reference_fasta_index /share/ScratchGeneral/jossch/reference/gatk/hg38/Homo_sapiens_assembly38.fasta.fai --target_bed /share/ScratchGeneral/jossch/WEScnv/assets/Agilent_V5_targets-MAP100-GC-GC500-WD-M.bed --target_cov_txt /share/ScratchGeneral/jossch/WEScnv/assets/Agilent_V5_targets-MAP100-GC-GC500-WD-M.txt --bait_bed /share/ScratchGeneral/jossch/WEScnv/assets/Agilent_V5_probes.bed --cnvKitTarget /share/ScratchGeneral/jossch/WEScnv/exome_design/hg38_cnvkit_targets.bed --cnvKitAntiTarget /share/ScratchGeneral/jossch/WEScnv/exome_design/hg38_cnvkit_antitargets.bed`
