Introduction
------------

The secondary metabolism of bacteria and fungi constitutes a rich source of
bioactive compounds of potential pharmaceutical value, comprising biosynthetic
pathways of many chemicals that have been and are being utilized as e.g.
antibiotics, cholesterol-lowering drugs or antitumor drugs.  Interestingly, the
genes encoding the biosynthetic pathway responsible for the production of such a
secondary metabolite are very often spatially clustered together at a certain
position on the chromosome; such a compendium of genes is referred to as a
'secondary metabolite biosynthesis gene cluster'.  This genetic architecture has
opened up the possibility for straightforward detection of secondary metabolite
biosynthesis pathways by locating their gene clusters. In recent years, the
costs of sequencing bacterial and fungi has dropped dramatically, and many
genome sequences have become available. Based on profile hidden Markov models of
genes that are specific for certain types of gene clusters, antiSMASH is able to
accurately identify the gene clusters encoding secondary metabolites of all
known broad chemical classes.  antiSMASH not only detects the gene clusters, but
also offers detailed sequence analysis.

antiSMASH input parameters
--------------------------

The ideal input for antiSMASH is an annotated nucleotide file in Genbank format
or EMBL format. You can either upload a GenBank/EMBL file manually, or simply
enter the GenBank/RefSeq accession number of your sequence for antiSMASH to
upload it. If no annotation is available, we recommend running your sequence
through an annotation pipeline like RAST to obtain GBK/EMBL files with
high-quality annotations.

Alternatively, you can provide a FASTA file containing a single sequence.
antiSMASH will generate a preliminary annotation using Prodigal, and use that to
run the rest of the analysis. You can also provide gene annotations in GFF3
foramt.
Input files should be properly formatted. If you are creating your
GBK/EMBL/FASTA file manually, be sure to do so in a plain text editor like
Notepad or Emacs, and saving your files as "All files (*.*)", ending with the
correct extension (for example ".fasta", ".gbk", or ".embl".

There are several optional analyses that may or may not be run on your sequence.
Highly recommended is the Gene Cluster Blast Comparative Analysis, which runs
BlastP using each amino acid sequence from a detected gene cluster as a query on
a large database of predicted protein sequences from secondary metabolite
biosynthetic gene clusters, and pools the results to identify the gene clusters
that are most homologous to the gene cluster that was detected in your query
nucleotide sequence.  This analysis is selected by default

Also available is the analysis of secondary metabolism gene families (smCOGs).
This analysis attempts to allocate each gene in the detected gene clusters to a
secondary metabolism-specific gene family using profile hidden Markov models
specific for the conserved sequence region characteristic of this family.
Additionally, a phylogenetic tree is constructed of each gene together with the
(max. 100) sequences of the smCOG seed alignment.  This analysis is selected by
default

antiSMASH output
----------------

The output of the antiSMASH analysis pipeline is organized in an interactive
HTML page with SVG graphics, and different parts of the analysis are displayed
in different panels for every gene cluster (see [example output file of
Streptomyces coelicolor A3(2)
genome](https://antismash.secondarymetabolites.org/upload/example/index.html)).


Initially, a list of identified clusters is displayed in the results page. A
gene cluster can be selected for viewing by clicking its number (gene clusters
are numbered in the order in which they appear on the input nucleotide sequence)
in the "Select Gene Cluster" panel just below the top banner or by clicking on
the colored "Cluster XX" boxes. A click on "Overview" brings you back to the
overview list.  Gene cluster buttons are color coded by predicted secondary
metabolite type.


In the upper panel, "Gene cluster description", information is given about each
gene cluster that was detected. In the upper line, the biosynthetic type and
location of the gene cluster are displayed. Underneath this title line, all
genes present in a detected gene cluster are outlined. The borders of the gene
clusters have been estimated using different greedily chosen cut-offs specified
per gene cluster type.  Genes are color coded by predicted function. Putative
biosynthetic genes are colored red, transport-related genes are colored blue,
and regulation-related genes are colored green. These predictions depend on the
smCOG functionality an will be missing if you chose to not run smCOG
predictions.  Hovering over a gene with the mouse will prompt the gene name to
be displayed above the gene. Clicking the gene will provide more information on
the gene: its annotation, its smCOG (secondary metabolism gene family), its
location, and cross-links specific to that gene.


In the middle panel, "Detailed annotation", you can find more in-depth
information on the selected gene cluster.  For predicted modular polyketide
synthase (PKS) and/or nonribosomal peptide synthetase (NRPS) proteins, you will
find the domain annotation. Clicking on a domain image will prompt more
information to be displayed, such as the name of the detected domain, its
precise location, any substrate specificites predicted, and a link to run Blast
on the domain.  For predicted Lantipeptide clusters, the predicted core peptide
sequences of all identified prepeptides is displayed.


The lower panel. "Homologous gene clusters", displays the top ten gene clusters
from the internal antiSMASH database that are most similar to a detected gene
cluster, visually aligned to it. The drop-down selection menu can be used to
browse through the gene clusters. Genes with the same colour are putative
homologs based on significant Blast hits between them.  In the upper side panel
on the right. "Predicted core structure", a rough prediction of the overall
chemical structure of a the product of a detected nonribosomal peptide or
polyketide biosynthesis gene cluster is given, along with prediction details for
all monomers.  Prediction details are available for multiple methods. PKS AT
domain specificities are predicted using a twenty-four amino acid signature
sequence of the active site (Yadav et al., 2003), as well as with pHMMs based on
the method of Minowa et al. (Minowa et al., 2007), which is also used to predict
co-enzyme A ligase domain specificities. NRPS A domain specificities are
predicted using both the signature sequence method and the support-vector
machines-based method of NRPSPredictor2 (Rausch et al., 2005 & Röttig et al.,
2011), and the method of Minowa et al. (Minowa et al., 2007). Ketoreductase
domain-based stereochemistry predictions for PKSs (Starcevic et al., 2008) are
also performed.


In the upper right, a small list of buttons offers further functionality. The
house-shaped button will get you back on the antiSMASH start page. The
question-mark button will get you to this help page. The exclamation-mark button
leads to a page explaining about antiSMASH. The downward-pointing arrow will
open a menu offering to download the complete set of results from the antiSMASH
run, a summary Excel file and to the summary EMBL/GenBank output file. The
EMBL/GenBank file can be viewed in a genome browser such as Artemis.

Frequently Asked Questions
--------------------------

### Can I run antiSMASH locally as a stand-alone program?

Yes. A stand-alone version of antiSMASH is available from the download section of this website.

### Why doesn't antiSMASH detect my gene cluster?

Some gene clusters, such as fatty acid or cofactor biosynthesis gene clusters are not identified by antiSMASH, as they are
categorized as primary metabolism instead of secondary metabolism. If you are
aware of a true secondary metabolite biosynthesis gene cluster that escapes
detection by antiSMASH, please contact us, and we will add the models necessary
to detect it.

### In some cases, two or three gene clusters appear to be fused into one gene cluster by antiSMASH while they are in fact separate gene clusters. Why is this?

Currently, it is not possible to judge on the basis of sequence
information only whether a large cluster of secondary metabolite biosynthesis
genes of different types is either a hybrid gene cluster or comprises multiple
separate gene clusters that are located very close to one another. A careful
manual study of the provided comparative gene cluster analysis results may
provide hints on solving this question.

### Why are several genes upstream and downstream of gene clusters included, even though they do not seem to be part of the gene cluster?

In designing antiSMASH, we tried to be very conservative in
cutting gene cluster borders, leaving this to the expert eye of the user, as it
is better to show some extra genes than to leave out key genes.

### Can I also submit an unannotated genome sequence in FASTA format?

Yes. We offer integrated preliminary gene prediction by Prodigal or GlimmerHMM based on a FASTA input.
If you want the highest possible quality of results, we recommend you to use an annotation
pipeline like RAST first to obtain high-quality gene predictions in GBK format.
You can also upload annotations in GFF3 format.

### What is the privacy policy of antiSMASH concerning my sequence data?

We try to keep this
site and the data that it analyzes as safe and secure as possible. Your output
files will be deleted from our server within one month. However, sending your
data to the web site is at your own risk. If you are concerned about the
sensitivity of your data, please use the stand-alone version of our
tool.
