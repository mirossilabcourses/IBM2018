# Introduction to bioinformatics for microbiologists

## Day 4 (Wednesday 2.05.18)

### Program of the day

* 30' - Introduction of BLAST
* 30' - Student Presentation - group 1
*   5' - Break 
* 30' - Student Presentation - group 2 
*   5' - Break
* 30' - Student Presentation - group 3
* 10' - Break
* 45' - Visualization of genomic comparisons

### Introduction of BLAST
Detailed description of the statistics of Sequence Similarity Scores in BLAST is available [here](https://www.ncbi.nlm.nih.gov/BLAST/tutorial/Altschul-1.html). A description of the BLAST result page is available in this link ftp://ftp.ncbi.nlm.nih.gov/pub/factsheets/HowTo_NewBLAST.pdf
### Student presentations
Each group will have 15 minutes for presenting their results and a summary of the resources they used. After each presentation 15 minutes of discussion will follow, covering theoretical and practical aspects of genome comparison performed by the group.
### Visualization of genomic comparisons
There are several methodologies which can be used for visualizing genome comparisons. 
#### [Artemis Comparison Tool (ACT)](http://www.sanger.ac.uk/science/tools/artemis-comparison-tool-act)
"ACT is a Java application for displaying pairwise comparisons between two or more DNA sequences. It can be used to identify and analyse regions of similarity and difference between genomes and to explore conservation of synteny, in the context of the entire sequences and their annotation. It can read complete EMBL, GENBANK and GFF entries or sequences in FASTA or raw format" (quoted from ACT website).

First you need to generate the *comparison files*. Click on [DoubleACT](http://www.hpa-bioinfotools.org.uk/pise/double_actv2.html). 
> Select among the available genomes two of your interest (for this demo I will select *C. jejuni* 11168 and *C. jejuni* RM1221), then select which BLAST approach to use (BLASTn or tBLASTx). Enter an email address and click on the “Run genome-blast” button. The results page will display the comparison file as 'genome_blast.result' by default. If the genomes were selected from the drop-down lists they will be available for download as annotated genbank files (genome1.gbk and genome2.gbk). 

If you have [Java Web Start]() installed, in the ACT webpage click `Lunch` (selecting the right memory). Alternativelly download the Java binary for your OS. 
> In `File>Open` selected the gbk file of *genome1* and of *genome2* and the load the *comparison file* (genome_blast.result) and click `Apply`. Note: all the files are available in the result page of DoubleACT.


* [Mauve](http://darlinglab.org/mauve/mauve.html)
* [BLAST Ring Image Generator (BRIG)](http://brig.sourceforge.net/)
* [Phandango](https://github.com/jameshadfield/phandango)
* [Circos Table Viewer](http://mkweb.bcgsc.ca/tableviewer/)


> Written with [StackEdit](https://stackedit.io/).
