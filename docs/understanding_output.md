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
all monomers.  Prediction details are available for multiple methods.

PKS type I AT domain specificities are predicted using a twenty-four amino acid
signature sequence of the active site (Yadav et al., 2003), as well as with
pHMMs based on the method of Minowa et al. (Minowa et al., 2007), which is also
used to predict co-enzyme A ligase domain specificities. NRPS A domain
specificities are predicted using both the signature sequence method and the
support-vector machines-based method of NRPSPredictor2 (Rausch et al., 2005 &
Röttig et al., 2011), and the method of Minowa et al. (Minowa et al., 2007).
Ketoreductase domain-based stereochemistry predictions for PKSs (Starcevic et
al., 2008) are also performed.

For PKS type II clusters, the side panel shows a list of the predicted starter
units along with bitscores, a list of the predicted number of malonyl
elongations along with bitscores, the predicted product class, a list of
product molecular weights predictions for each combination of starter unit and
number of malonyl elongations. Furhtermore, it displays each gene/protein which
are involved in the polyketide biosynthesis of the cluster. For each
gene/protein the type is indicated and for some a prediction of function is
displayed.

In the upper right, a small list of buttons offers further functionality. The
house-shaped button will get you back on the antiSMASH start page. The
question-mark button will get you to this help page. The exclamation-mark button
leads to a page explaining about antiSMASH. The downward-pointing arrow will
open a menu offering to download the complete set of results from the antiSMASH
run, a summary Excel file and to the summary EMBL/GenBank output file. The
EMBL/GenBank file can be viewed in a genome browser such as Artemis.
