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
