# Introduction to bioinformatics for microbiologists

## Day 3 (Friday 20.04.18)

### Program of the day

* 10'  - What have you learn from day 2?
* 35' - What species did I sequence?
* 15' - Break
* 45' - Variant calling 
* 15' - Break
* 45' - Functional annotation of genes and orthology definition
* 10' - Homework 
*  5' - Self-assessment 
### What species did I sequence?
Frequently the first action you would like to perform after receiving the sequences is checking the species of your sample, or in case you are studying a novel taxon, you would like to compare the samples with known species. Some pipelines, such as `INNUca`, have implemented several modules including species confirmation steps. For example, you might infer the species by calling (or try to) the MLST type (if a schema is available). For doing that `INNUca` call a very nice software designed by T. Seemann: [*mlst*](https://github.com/tseemann/mlst). The software scans contig files against traditional [PubMLST](https://pubmlst.org/databases/) typing schemes and giving the ST. The software it is very easy to use also in command line just by typing `% mlst contigs.fa` after you have installed it in a Linux OS. You can do manually what *mlst* does by e.g. going to one of the available PubMLST database and call the ST of your sample after uploading the contig file. 

Calling MLST schemas implies the existence of a schema for a particular species and the fact that you know (or at least you think to know) the species you are looking for. However, in several projects the species is unknown and even more frequently a MLST schema is not available. In this case you need to [*classify*](http://www.bacterio.net/-classification.html) your strain within a [*Taxonomy group*](http://www.bacterio.net/-classifphyla.html). Before genomic-era classification was mainly based on phylogenetic analysis of 16S rRNA gene sequence. This method is still widely used (especially for metagenomic analyses) since 16S rRNA sequence databases are usually more populated then genomic databases (or at least was); among several databases I recommend the [RDP](https://rdp.cme.msu.edu/misc/contacts.jsp) hosted at the Michigan State University, US. However, since genome sequencing data is now required with [Taxonomic Descriptions](http://ijs.microbiologyresearch.org/content/Genome_data_required_IJSEM) and the sequencing costs are affordable nowadays, in the near future classification will be based on genomic comparison. At the moment more then 90000 genome sequences of prokaryotic are available but still from a limited number of species.

There are several methods now you can use for inferring genomic similarity between two strains and, those, if they belong to the same species. Among them Average Nucleotide Identity ([Goris  _et al._, 2007](http://www.ncbi.nlm.nih.gov/pubmed/17220447)) is widely acknowledged as a robust measure of genomic relatedness. The standard ANI computation uses BLASTn to align conserved regions between genomes. Organisms belonging to the same species typically show >95% ANI among themselves. An alternative method developed by the Leibniz Institute DSMZ (German Collection of Microorganisms and Cell Cultures) is the [Genome Blast Distance Phylogeny (GBDP)](https://ggdc.dsmz.de/docs/Slides_about_GGDC_from_Hans-Peter_Klenk_as_used_in_his_2014_Bergey_Award_acceptance_speak.pdf). This approach yields high correspondence to wet-lab DDH (which was the gold-standard for bacterial species delineation).
In addition to alignment based method, classification of isolates can be performed using alignment-free methods. These methods are based on counting frequencies and distributions of k-mers. These approaches provide pairwise distances between genomes based on shared k-mers which can be directly used in deriving a phylogenomic networkhttp://. It is a very quick method (much faster then ANI or GBDP). A very interesting website with a super fast method for comparing sequence using oligonucleotide is [GScompare](http://gscompare.ehu.eus/). Even more reductive approach is the transformation of the genome sequence in *hash*. [MASH](http://mash.readthedocs.io/en/latest/) *..uses the MinHash dimensionality-reduction technique to reduce large genomes into compressed sketches. A sketch is based on a hash function applied to a k-mer representation of a genome, and compression is achieved by only including the `s` smallest hash values of all k-mers in the genome in the  sketch. Comparing the sketches of two genomes, MASH defines a distance measure under a simple Poisson process of random site mutation that approximates ANI values* (quoted from [Zhou et al, 2017](https://www.biorxiv.org/content/biorxiv/early/2017/11/09/215707.full.pdf)). The best implementation of MinHash for taxonomy is [FastANI](https://github.com/ParBLiSS/FastANI) which produces an accurate ANI estimate three orders of magnitude faster when compared to an alignment (e.g., BLAST)- based approach.
#### Activity 1 - Classify the genome using ANI and GBDP
Compare genome using ANI and GBDP of the *C. coli* you used yesterday. You can either calculate ANI using [ANI calculator](http://enve-omics.ce.gatech.edu/ani/) from Kostas Lab or the one in [EZ BioCloud](https://www.ezbiocloud.net/tools/ani) (which is using an USEARCH version of the original ANI).
#### Activity 2 - Classify the genome using kmer based method as in GScompare
Download genomes of your interest from [Genome Information by Organism](https://www.ncbi.nlm.nih.gov/genome/browse/). Open an account in [GScompare](http://gscompare.ehu.eus/) and follow the instructions. 
### Variant calling
Similarly to what discussed above, frequently we need to measure how much two or more samples are different, when they belong to the same species. Variant calling is the process by which we identify variants from individuals of the same species. The process is also called *genotyping*. It has an important implication for e.g. understanding the course of an epidemic or for identifying specific "types" with important characteristics (e.g. more virulent, able to transform specific compound useful in food production or in other industrial application, etc..). Frequently those samples shared a similar set of genes, but small variation within these genes might be responsible for important *phenotypes* (e.g. single nucleotide substitution leads to antimicrobial resistance). You can calculate the variation between individuals in three different ways:
1. k-mer based methods
2. SNP approaches
3. MultiLocus Sequence Typing 
#### Activity 3 - Explore EnteroBase resources
EnteroBase is a fantastic resource for who is interested in exploring diversity of *Salmonella enterica*, *Escherichia coli* and *Yersinia*. Go to [EnteroBase website](http://enterobase.warwick.ac.uk/species/index/senterica) and sign-up. Click on `Escherichia/Shigella`. Click `Load Workspace` from the red box on top-right of the site. Load the dataset 4395. Perform `cgMLST` and `SNP analysis`. Compare the results.
### Functional annotation of genes and orthology definition
*working in progress* 
### Homework
Select one of the resources listed below and perform comparative analysis on a group of bacteria or virus of your choice.
Prepare a 15 minute presentation including:
1. Research question and aim of the analysis
2. Methods used and a summary of the workflow applied to the analysis
3. Results 
4. Share your comments on the resource you used for performing the analysis
5. One question for discussing in class
#### Suggested reading
[Paper comparing platform for bacterial annotation and comparative genomics](https://www.sciencedirect.com/science/article/pii/S0168165617315225?via%3Dihub)
#### Online resources
* [Ortholugedb](http://www.pathogenomics.sfu.ca/ortholugedb/)
* [Edgar](https://edgar.computational.bio.uni-giessen.de/cgi-bin/edgar_login.cgi?cookie_test=1&open=1)
* [Patric](https://www.patricbrc.org/)
* [Microbial Genome Database for Comparative Analysis](http://mbgd.genome.ad.jp/)
* [MicrobesOnline](http://www.microbesonline.org/)
* [MicroScope](http://www.genoscope.cns.fr/agc/microscope/home/index.php)
* [EZbiocloud](https://www.ezbiocloud.net/)
* [viruSITE—integrated database for viral genomics](http://www.virusite.org/)

> Written with [StackEdit](https://stackedit.io/).
