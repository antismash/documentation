Setting up your antiSMASH job
=============================

This page describes all relevant steps to get to interpretable antiSMASH output using the web server. 
It covers everything from the correct input data to what all settings and parameters mean. 
[Here](https://antismash.secondarymetabolites.org/#!/start) is the latest stable bacterial
version of antiSMASH available of which a screenshot is provided below:

![alt text][Fig1]

Registering your antiSMASH job
===========================

Please make sure that if you have fungal or plant sequence data that you click on the appropriate tab in 
the top bar as some settings are dedicated to either bacterial or fungal data and to upload plant sequences
you are redirected to PlantiSmash. 

In case you would like to get an email alert upon completion of your job you can optionally 
provide your email address in the "Notification settings" panel. You will then receive an email 
with a link to your completed job once it finished okay or if any error would have unfortunately occurred. 
Please note that if you did not provide an email address, you should bookmark the link to the job submission page, 
as otherwise you will not be able to access the results anymore.

![alt text][Fig2]


antiSMASH input data
====================

The ideal input for antiSMASH is an annotated nucleotide file in Genbank format
or EMBL format. You can either upload a local GenBank/EMBL file manually, or simply
enter the GenBank/RefSeq accession number of your sequence for antiSMASH to
upload it. You can toggle the option in the "Data input" panel where default is the accession number 
entry where antiSMASH will attempt to download the data directly from NCBI.

![alt text][Fig3]

In case no gene annotations are available for your sequence, we recommend running your sequence
through an annotation pipeline like RAST to obtain GBK/EMBL files with
high-quality annotations.
Alternatively, you can provide a FASTA file containing a single sequence. In that case, 
antiSMASH will generate a preliminary annotation using Prodigal, and use that to
run the rest of the analysis. You can also provide gene annotations in GFF3
format.

In any case, it is very important that input files are properly formatted. If you are creating your
GBK/EMBL/FASTA file manually, be sure to do so in a plain text editor like
Notepad or Emacs, and saving your files as "All files (*.*)", ending with the
correct extension (for example ".fasta", ".gbk", or ".embl".

antiSMASH default and extra features
====================================

Before pressing the submission button, you will have to indicate which antiSMASH features 
you like to run. 

Default antiSMASH features
--------------------------

The following options are run by default if you do not toggle them off as can be seen in the 
screenshot from the "Extra features" panel:

![alt text][Fig4]

**KnownClusterBlast analysis**: the identified clusters are searched against the [MIBiG repository](https://mibig.secondarymetabolites.org). 
MIBiG is a hand curated data collection of biosynthetic gene clusters, which have been experimentally characterized.

**Subcluster Blast analysis**: the identified clusters are searched against a [database](https://bitbucket.org/antismash/antismash/src/bfa2f1c0fe97de910c19ee2be241b415e6fa97bd/antismash/generic_modules/subclusterblast/subclusters.txt?at=master&fileviewer=file-view-default) containing 
operons involved in the biosynthesis of common secondary metabolite building blocks 
(e.g. the biosynthesis of non-proteinogenic amino acids).

The following antiSMASH features always run on the background:

**smCOG analysis**: the analysis of secondary metabolism gene families (smCOGs) attempts to allocate each gene 
in the detected gene clusters to a secondary metabolism-specific gene family using profile 
hidden Markov models specific for the conserved sequence region characteristic of this family. 
In other words, each gene of the cluster is compared to a database of clusters of orthologous 
groups of proteins involved in secondary metabolism. Additionally, a phylogenetic tree is constructed of each gene together with the
(max. 100) sequences of the smCOG seed alignment. This information can then be used to provide an annotation of 
the putative function of the gene products. smCOG analysis results can be used for functional prediction and phylogenetic analysis of genes.

**Active site finder**: active sites of several highly conserved biosynthetic enzymes are detected and variations of the active sites are reported.

**Detect TTA codons**: high-GC containing bacterial sequences (by default in antiSMASH >65%), for example from *Streptomycetes*, 
contain the rare Leu-codon “TTA” as a mean for post-transcriptional regulation by limiting/controlling the 
amount of TTA-tNRA in the cell. This type of regulation is commonly found in secondary metabolite BGCs. 
This feature will annotate such TTA codons in the identified BGCs.

Advanced antiSMASH features
---------------------------

As can be seen in the screenshot above, all features can be easily toggled off or on in one click on 
the top of the "Extra features" panel. The following three features are off by default and are considered to be useful for 
advanced users or in case interesting biosynthetic gene clusters were found that warrant further detailed analysis.

**ClusterBlast analysis**: the identified clusters are searched against a comprehensive gene cluster database and 
similar clusters are identified. The algorithm used here is inspired by [MultiGeneBlast](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3670737/). 
It runs BlastP using each amino acid sequence from a detected gene cluster as a query on
a large database of predicted protein sequences from secondary metabolite
biosynthetic gene clusters, and pools the results to identify the gene clusters
that are most homologous to the gene cluster that was detected in your query
nucleotide sequence.
Please note that selecting this option increases the runtime significantly.

**Cluster Pfam analysis**: each gene product encoded in the detected BGCs is analyzed against [the PFAM database](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4702930/). 
Hits are annotated in the final Genbank/EMBL files that can be downloaded after the analysis is finished. 
Please note that these results are not displayed on the antiSMASH HTML results page but they are present in the results genbank file that can be downloaded. 
Also, selecting this option normally increases the runtime.

**Pfam-based GO term annotation**: this is annotating the Cluster Pfam analysis described above with [GO term annotations](http://www.geneontology.org). 
Please note that these results are not displayed on the antiSMASH HTML results page but they are present in the results genbank file that can be downloaded 
(see "Understanding the output" section of the documentation for instructions on how to download the results). 
Also, selecting this option normally increases the runtime. 

Note on ClusterFinder
---------------------
Due to very high runtime requirements and our observation that results generated with the ClusterFinder 
option were often misinterpreted, we no longer support [ClusterFinder](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4123684/) via the antiSMASH web interface. 
If you are interested in ClusterFinder (and are aware on how to interpret the data), it still is 
included in the download version of antiSMASH that runs locally.

FungiSMASH
----------
The fungal version of AntiSmash is [FungiSMASH](https://fungismash.secondarymetabolites.org/#!/start) and it contains one 
extra fungal sequence specific feature:

![alt text][Fig5]

**Cluster-border prediction based on transcription factor binding sites (CASSIS)**: In fungi, 
it is possible to predict clustered genes by identifying highly conserved regulator binding motifs in the promotor 
regions of the biosynthesis genes. The Cluster Assignment by Islands of Sites or [CASSIS algorithm](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4824125/) 
can detect such motifs and thus predict core-regions of fungal BGCs. 
In bacteria, these motifs unfortunately are less conserved, thus this approach only works on fungal sequences.

Submitting your query
---------------------
After you set up your online antiSMASH job, you can click on submit on the bottom of the page and 
the calculations for the identification and analysis of the gene clusters will be carried out on our servers. 
When the job is finished – and an email address was provided – the user gets a notification email that the results are available. 
Otherwise, you will need to go to the bookmarked link to check if the analysis has finished.

[Fig1]:img/antiSMASHentrypage.png
[Fig2]:img/notifications.png
[Fig3]:img/datatype.png
[Fig4]:img/parameters.png
[Fig5]:img/fungismash.png

