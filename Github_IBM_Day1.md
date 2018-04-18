
# Introduction to bioinformatics for microbiologists

## Day 1 (Wednesday 18.04.18)

### Program of the day

 - 5' - Presentation of the teacher and the course content; learning outcomes and what is expected from the students 
- 15' - Presentation of the students 
- 10' - Class discussion on the preparatory work 
- 15' - Break 
- 45' - From wet to dry: step by step from DNA to sequence?
- 15' - Break 
- 30' - Where can I find genome sequences? introduction of sequence repositories and sequence file format
- 20' - Linux corner: A quick tour on downloading raw reads using command line 

### From wet to dry: step by step from DNA to sequence
#### Suggested videos
* [Best Practices for Nextera Library Prep, Illumina Support Video ](https://www.youtube.com/watch?v=UOn50ND7T78)
* [ Illumina MiSeq Workflow Overview](https://www.youtube.com/watch?v=JA6mofeuntk)
#### Sequence technology, suggested reading
* [Head et al., 2014 *Library construction for next-generation sequencing: overviews and challenges*](https://www.ncbi.nlm.nih.gov/pubmed/24502796)
* [Mardis 2017 *DNA sequencing technologies: 2006–2016*](https://www.nature.com/articles/nprot.2016.182)
* [Loman et al., 2012 *Performance comparison of benchtop high-throughput sequencing platforms*](https://www.nature.com/articles/nbt.2198)
* [Glossary of commonly used terms and catch-phrases in the field of bacterial whole genome sequencing](http://www.clinicalmicrobiologyandinfection.com/action/showFullTableImage?isHtml=true&tableId=tbl1&pii=S1198743X18302064)
* [Illumina guideline for Nextera library preparation](https://support.illumina.com/content/dam/illumina-support/documents/documentation/chemistry_documentation/samplepreps_nextera/nextera-xt/nextera-xt-library-prep-reference-guide-15031942-03.pdf)
* [Illumina guideline for Nextera library preparation troubleshooting](https://support.illumina.com/content/dam/illumina-support/documents/documentation/chemistry_documentation/samplepreps_nextera/nextera-xt/nextera-xt-troubleshooting-guide.pdf)

#### Infectious disease bacterial genomics, suggested reading
* [Lynch et al., 2016 *A Primer on Infectious Disease Bacterial Genomics*](https://www.ncbi.nlm.nih.gov/pubmed/28590251)
* [Mellmann et al., 2017 *High Interlaboratory Reproducibility and Accuracy of Next-Generation-Sequencing-Based Bacterial Genotyping in a Ring Trial*](http://jcm.asm.org/content/55/3/908.full)
* [Quainoo et al., 2017 *Whole-Genome Sequencing of Bacterial Pathogens: the Future of Nosocomial Outbreak Analysis*](http://cmr.asm.org/content/30/4/1015.long)
* [Holmes et al., 2018 *Validation of Whole-Genome Sequencing for Identification and Characterization of Shiga Toxin-Producing Escherichia coli To Produce Standardized Data To Enable Data Sharing*](http://jcm.asm.org/content/56/3/e01388-17.short)
* [PulseNet International](https://www.cdc.gov/pulsenet/next-generation.html)

### Where can I find genome sequences? introduction of sequence repositories and sequence file format

#### Activity 1 -  exploring the BioSamples Databases
* [EBI BioSamples](https://www.ebi.ac.uk/biosamples/)
* [NCBI BioSample](https://www.ncbi.nlm.nih.gov/biosample/)

Search for `gastroenteritis` in both databases and compare the two results. Refine the search by filtering for specific pathogen or host. What type of information are you visualizing?

#### Activity 2 - quick tour of EBI and NCBI resources 
Don't get lost, below the list of resources from EBI and NCBI
* [List of EBI resources](https://www.ebi.ac.uk/services)
* [List of NCBI resources](https://www.ncbi.nlm.nih.gov/guide/all/)

Identify the relevant resources for microbiological research

#### Activity 3 - SRA and ENA Run entries
Let's check together the entry structure of a submitted strain *Campylobacter coli* 817/2007 – run accession number SRR4252351

* [NCBI SRA](https://www.ncbi.nlm.nih.gov/Traces/study/?acc=SRP090008)
* [EBI ENA](https://www.ebi.ac.uk/ena/data/view/SRR4252351)

#### Activity 4 - Search and download raw reads of a taxon
The best way to download fastQ of your interest is programmatically using software designed for accessing ENA or SRA thorugh REST-API. An example is [getSeqENA - Get fastq files from ENA using Run IDs](https://github.com/B-UMMI/getSeqENA). However, for small batches the ENA or SRA browser are good tools. For this exercise we will use the ENA browser but similar search can be done in SRA browser.

Let's find the identification number of the taxon (a.k.a. Taxonomy ID). Go to [NCBI Taxonomy portal](https://www.ncbi.nlm.nih.gov/taxonomy) and search for a bacterial species of your choice. Take note of Taxonomy ID of the species. 

Now move to [EBI ENA Browser](https://www.ebi.ac.uk/ena/data/warehouse/search). Select `Read`. In `Taxon name` type the Taxonomy ID. Then scroll the list and select the right features for this exercise which aim in searching `paired`reads produced only with `Illumina MiSeq` .

On the result page you can refine the search by clicking `Edit query`. If you are satisfied with the search you can edit what to visualize on the page by clicking `Select columns`. Finally you can download a `txt`file which you can edit e.g. using `excel`. You can dowloand the `fastQ`manually by clicking on the link (i.e. `FASTQ files (FTP)`). You can also download them using an FTP client through `ftp.sra.ebi.ac.uk` using the following credentials: 
```
Name: anonymous
Password: _enter your e-mail address_
```
More information available [here](https://www.ebi.ac.uk/ena/browse/read-download)

#### Activity 5 -  Search and download assemblies and annotation by organism
For this activity we will use the resources available at NCBI. Similar search can be perform using ENA browser. 
We will use the [Frequently asked questions](https://www.ncbi.nlm.nih.gov/genome/doc/ftpfaq/) on  downloading genome in NCBI as general guidelines. 

For the first part of the exercise you will download the `assembly`genomes of your interest in `FASTA` format. For this part we will use the [Assembly resource](https://www.ncbi.nlm.nih.gov/assembly/?term=all%5Bfilter%5D) starting with `all[filter]`. 
* Select `Bacteria` from the `Organism group` facet in the left-hand sidebar and then select `Complete genome` from the `Assembly level` facet. How many complete bacterial genomes are available?
* Refine the search by inserting in the `Organism group`a bacteria group of your interest. For example add `Campylobacterales`and refine the search. Limit the search only to `Reference`.
* Click on the `Download Assemblies` button to open the download menu. From the `File type` select `Genomic FASTA` and click download, you may get a pop-up window asking if/where you want to save the `genome_assemblies.tar` archive file. After the download has finished, expand the tar archive.
* Take some time to explore the content of the file. 
**Note: you can select as many genomes you like, but it is best for small to moderately sized data sets**

In the second part of the exercise, you will browse the genome by organism and collect information on `genome size`, `number of CDS`,  presence of `plasmids`, etc... 
* Go to the [Genome Information by Organism](https://www.ncbi.nlm.nih.gov/genome/browse/). Click on `Prokaryotes`. Then refine the search by writing the species name on the search bar.  
* You can refine further the search by selecting several options in `Filter` (for example you might prefer to visualise only the complete genomes).
* You can change the content of the table and download the table in CSV format for further investigation. 
* Under the column `FTP`click on `R`and you will be redirected to the ftp directory of the selected genome containing a core set of files and formats plus additional files relevant to the data content of the specific assembly.
*  `README.txt` contains all the information for understanding the files in the directory.

####  Activity 6 - File formats for annotation
* [GenBank Flat File Format](https://www.ncbi.nlm.nih.gov/Sitemap/samplerecord.html)
* [EMBL Flat File Format](https://www.ebi.ac.uk/ena/submit/flat-file)
* [GFF3](http://gmod.org/wiki/GFF3)

Using the [Assembly resource](https://www.ncbi.nlm.nih.gov/assembly/?term=all%5Bfilter%5D). Download a set of GFF3 files by selecting it from the `File type` on the `Download Assemblies` button.
You can open the `GFF3`using [Artemis](http://www.sanger.ac.uk/science/tools/artemis).
### Linux corner: Get the data
Let's download *fastQ* files of 10 *Streptococcus agalactiae* strains
* Organize the data
```bash
# Create a folder to store the HTS reads

mkdir ~/reads
mkdir ~/reads/<your_species_name>

# Create a folder for Streptococcus agalactiae example
mkdir ~/reads/streptococcus_agalactiae_example
```

* Get the file with IDs
```bash
wget -O ~/reads/streptococcus_agalactiae_example/MPM_GBS_samples.tab https://raw.githubusercontent.com/INNUENDOCON/MicrobialGenomeMetagenomeCourse/master/MPM_GBS_samples.tab
```
* Produce a clean file by removing the header line (first line) and containing only the first column
```
# The next command pipes two different commands and redirects the output to a file
sed 1d ~/reads/streptococcus_agalactiae_example/MPM_GBS_samples.tab | cut -f 1 > ~/reads/streptococcus_agalactiae_example/ids.txt
```
* Clone getSeqENA 
```
git clone https://github.com/B-UMMI/getSeqENA.git 
```
* Download data with getSeqENA
```
getSeqENA.py --listENAids ~/reads/streptococcus_agalactiae_example/ids.txt \
             --outdir ~/reads/streptococcus_agalactiae_example/ \
             --asperaKey  ~/NGStools/aspera/connect/etc/asperaweb_id_dsa.openssh \
             --downloadLibrariesType PAIRED \
             --downloadInstrumentPlatform ILLUMINA \
             --threads 8 \
             --SRAopt

# Runtime :0.0h:2.0m:10.12s
```
#### Extra activities - The 10th anniversary of EMBL-EBI training treasure hunt

In August 2017 EMBL-EBI training celebrated 10 years of. As part of the anniversary celebrations, trainers across EMBL-EBI created a [10th anniversary treasure hunt](https://www.ebi.ac.uk/training/online/course/10th-anniversary-treasure-hunt) that allows users to travel across the various databases and discover the breadth of data available to them


> Written with [StackEdit](https://stackedit.io/).
