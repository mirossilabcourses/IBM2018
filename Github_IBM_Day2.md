# Introduction to bioinformatics for microbiologists

## Day 2 (Thursday 18.04.18)

### Program of the day

* 15'  - What have you learn from day 1?
* 45' - Anatomy of a fastQ: assessing quality of short reads and preprocessing
* 15' - Break
* 45' - From raw reads to an assembly
* 10' - Break
* 20' - Quality assessment of the assembly 
* 20' - Linux corner: a quick tour on assembling genomes on command line using docker
*  5' - Self-assessment
### Anatomy of a fastQ
#### Suggested readings and video
* [Quality Scores for Next-Generation Sequencing](https://www.illumina.com/documents/products/technotes/technote_Q-Scores.pdf)
* [Manual of Trimmomatic](https://www.google.fi/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0ahUKEwjL_vLMjcPaAhVQKywKHSCqAVsQFggnMAA&url=http%3A%2F%2Fwww.usadellab.org%2Fcms%2Fuploads%2Fsupplementary%2FTrimmomatic%2FTrimmomaticManual_V0.32.pdf&usg=AOvVaw1UrW4bh4XHUrc0Y9o7K9O1)
* [Blog on common NGS problems](https://sequencing.qcfail.com/)
* [A post on duplication in FastQC](http://proteo.me.uk/2013/09/a-new-way-to-look-at-duplication-in-fastqc-v0-11/)
* [*Video* on Base calling and quality score](https://www.youtube.com/watch?v=U4QnpciIJhM&t=8s)

#### Activity 1- Coverage estimation
Raw coverage estimation is a good starting point for understanding if you have obtained sufficient amount of sequence. Estimation of the coverage is simply the calculation of how many time a base in a genome have been sequence in average. Consider that assemblers, such as SPAdes, are not able to assembly genomes if raw reads do not cover at least ~15 time the total size. What you need to know is how many bases the *fastQ* contains and what is the expected size of the genome. Based on what you have learn yesterday you should be able to answer the following question:
* **what is the estimated coverage for the run ERR840705?**
#### Activity 2 - Exploring the quality of raw reads using FASTQC
Using FASTQC is pretty easy, but it might take some time to understand how to interpret the results. This [*Video*](https://www.youtube.com/watch?v=bz93ReOv87Y) explains step by step the use of FASTQC trough the GUI. 
1. Read the FASTQC manual. The manual is in the following directory `./FastQC/Help/3 Analysis Modules`  
2. Evaluate the following reads **which one you would resequence?** 
	* [SRR6044997](https://www.ebi.ac.uk/ena/data/view/SRR6044997) (QC evaluation can be download from [here](https://www.dropbox.com/sh/zt3gcfkq9t6dbvb/AACaVuU3jbOjo8IrHE1DSqq0a?dl=0))
		* R [1](ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR604/007/SRR6044997/SRR6044997_1.fastq.gz) and [2](ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR604/007/SRR6044997/SRR6044997_2.fastq.gz) before trimming
		* R [1](https://www.dropbox.com/s/kd5p32oeq93wmv9/SRR6044997_1P.fastq.gz?dl=0) and [2](https://www.dropbox.com/s/4r5u0wfiiu4aar5/SRR6044997_2P.fastq.gz?dl=0) after trimming 
		trimming was performed with [trimmomatic](http://www.usadellab.org/cms/?page=trimmomatic): CROP:149 HEADCROP:10 ILLUMINACLIP SLIDINGWINDOW:5:20 LEADING:3 TRAILING:3 MINLEN:55 TOPHRED33
	* [ERR840705](https://www.ebi.ac.uk/ena/data/view/ERR840705) (QC evaluation can be download from [here](https://www.dropbox.com/sh/m7rp2w5sfiypp17/AAA14MmV1m5bAH5X1hJBNLpqa?dl=0))
		* R [1](ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR840/ERR840705/ERR840705_1.fastq.gz) and [2](ftp://ftp.sra.ebi.ac.uk/vol1/fastq/ERR840/ERR840705/ERR840705_2.fastq.gz) before trimming
		* R [1](https://www.dropbox.com/s/9v9u3xllkwc7sg3/ERR840705_1P.fastq.gz?dl=0) and [2](https://www.dropbox.com/s/2hchiqtt8znf28x/ERR840705_2P.fastq.gz?dl=0) after trimming 
		trimming was performed with [trimmomatic](http://www.usadellab.org/cms/?page=trimmomatic): CROP:151 HEADCROP:3 ILLUMINACLIP SLIDINGWINDOW:5:20 LEADING:3 TRAILING:3 MINLEN:55 TOPHRED33
	* [SRR5575009](https://www.ebi.ac.uk/ena/data/view/SRR5575009) (QC evaluation can be download from [here](https://www.dropbox.com/sh/05ziuunglesym3y/AAC6zby73qOj_UjlHqJ_OA1Ca?dl=0))
		* R [1](ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR557/009/SRR5575009/SRR5575009_1.fastq.gz) and [2](ftp://ftp.sra.ebi.ac.uk/vol1/fastq/SRR557/009/SRR5575009/SRR5575009_2.fastq.gz) before trimming
		* R [1](https://www.dropbox.com/s/9jucxjms632h8jy/SRR5575009_1P.fastq.gz?dl=0) and [2](https://www.dropbox.com/s/9ksne5wcd8yvmfv/SRR5575009_2P.fastq.gz?dl=0) after trimming 
		trimming was performed with [trimmomatic](http://www.usadellab.org/cms/?page=trimmomatic): CROP:248 HEADCROP:15 ILLUMINACLIP SLIDINGWINDOW:5:20 LEADING:3 TRAILING:3 MINLEN:55 TOPHRED33
### From raw short reads to an assembly
#### Suggested readings and videos
* [M.Watson post on short proteins in long-read single molecule assembly](http://www.opiniomics.org/with-great-power-comes-great-responsibility/)
* [*Video* on Genome assembly](https://www.youtube.com/watch?v=sysnKQvqmnk)
* [*Video* of a lecture at MIT on genome assembly](https://www.youtube.com/watch?v=ZYW2AeDE6wU)
* [*Video* on Andrey Prjibelski presentation on SPAdes 3.1 (now is 3.11)](https://www.youtube.com/watch?v=vFA7BGzNMss)
###  Quality assessment of the assembly 
#### Activity 3 - Explore INNUca sample statistics report
`INNUca` offers an efficient bacterial *de novo* assembly pipeline with integrated QA/QC steps. The workflow allow the user to control the assembly process and identify reasons responsible of producing assemblies of low or not sufficient uality. For this activity you will explore the INNUca sample statistics report using the application INNUENDO platform developed within the project [INNUENDO](http://www.innuendoweb.org) which I coordinate. The platform have been developed by an amazing [team of students leaded by Dr. João Carriço from University of Lisbon](https://github.com/B-UMMI).
Access the [web application](https://192.92.149.157/app/) and login using the ID&Password I will show during the class. Download the file available at this [link](https://www.dropbox.com/s/yqq3jmn7cr1fqn3/IBM.json?dl=0). Within the platform click on `Reports`and Drag&Drop the file.

#### Activity 4 - Compare different assemblies 
For this activity you will use the web application of [QUAST](http://quast.bioinf.spbau.ru/). 
I have download the raw reads of three *C. coli* strains for which *reference* genome assemblies (hybrid assembly using Illumina and PacBio) were available (more information in this publication "[Generating tools for the molecular epidemiology of *Campylobacter coli* by next generation genome sequencing](https://www.food.gov.uk/sites/default/files/fs101087finalreport.pdf)"). Raw illumina fastQ were *de novo* assembled with `SKESA` or `SPAdes`. `SKESA`was running using default settings, while `SPAdes` was running using the QA/QC pipeline `INNUca`. The assemblies of the three samplgenomes are available at this [link](https://www.dropbox.com/sh/dopklm8cgg5g3pj/AACidpm9Do6hRi_jq8A29XK4a?dl=0). **What are the differences between SKESA and SPAdes?**  
### Linux corner - Assembly using INNUca within a Docker container 
INNUca is written in `python`and it requires a lot of dependencies. Fortunately you can run it in a [Docker](https://www.docker.com/what-docker) container. This allows you to run it in whatever platforms or computer settings. 

> ##### What's Docker? 
> A tutorial for beginners is available [here](https://docker-curriculum.com/).

I will show you how to run it using [Docker for Mac](https://docs.docker.com/docker-for-mac/install/), but please note there is also [Docker for Windows 10](https://docs.docker.com/docker-for-windows/install/) which works exactly the same (and of course you can run docker in Linux too). 
I will also give you some tips, and believe me **IT IS REALLY SIMPLE**. A [tutorial](https://github.com/INNUENDOCON/MicrobialGenomeMetagenomeCourse/blob/master/MPM_workingwithINNUCA.md) on INNUca using docker was written for a course organised last year.
Below the **INNUca** basic command using docker image.
```bash
# INNUca basic command.

# You should specify where the output goes whenever there is an option to do that.
# Whenever possible use the option to specify the number of CPUs/threads to be used
```bash
docker run --rm -u $(id -u):$(id -g) -it -v /path/to/directory/to/map~/:/data/ ummidock/innuca:3.21 \
       INNUca.py --inputDirectory /data/reads/<your_species_name>/ \
                 --speciesExpected "<your species name with space>" \
                 --genomeSizeExpectedMb <your_species_genome size> \
                 --outdir /data/genomes/<your_species_name>/innuca/ \
                 --threads 8
```

> Written with [StackEdit](https://stackedit.io/).
