## Overview page

The overview page contains a summary of all regions found in all records/contigs within the input given to antiSMASH.

![Region overview](img/cluster_overview.png)

At the top left of the page is the antiSMASH version information (**1**).
Direct comparisons between antiSMASH results should use the same version for consistency, as results can change between versions.

At the top right of the page are ancillary links that may be useful.
`Download` allows you to download various parts of the results.
`About` links to information about antiSMASH (including publications).
`Help` links to these documentation pages.
Finally, `Contact` links to a page with a form to send feedback or questions to the antiSMASH developers.

Under the top bar are region buttons (**2**).
These buttons are visible on all antiSMASH HTML pagesand can be used to quickly jump between regions.
If a region is being viewed, the matching button for that region will be highlighted.
Region buttons are in the form `X.Y`. For example, `5.7` would be the seventh region within the fifth record.
Region buttons are color coded by predicted secondary metabolite type.
Clicking the `Overview` button will bring you back to this page.

Under these buttons are a summary of each record, each starting the name of the record (**3**) as given in the input file.
At the top of the summary is an image (**4**) showing where the regions are located in the record.
Following that is a table with a summary of each region found in the record, with each row (**5**) having the following fields:

* **Region**: the region number
* **Type**: the product types as detected by antiSMASH (clicking the types will take you to their description in these help pages)
* **From**, **To**: the location of the region (in nucleotides)
* **Most similar known cluster**: the closest compound from the MiBIG database (clicking this will take you to the MiBIG entry), along with its type (e.g. `t1pks+t3pks`)
* **Similarity**: a percentage of genes within the closest known compound that have a significant BLAST hit to genes within the current region

The last two columns containing comparisons to the MiBIG database will only be shown if antiSMASH was run with the *KnownClusterBlast* option.

Clicking anywhere in the row that is not already an external link will take you to the detailed results for that region.

## The antiSMASH 5 region concept

Currently, there is no good method available to accurately predict gene cluster borders based purely on the submitted sequence data (with the exception of the CASSIS algorithm, which is able to detect co-regulated genes in fungal genomes).
In antiSMASH5, the display of gene clusters change to reflect the fact that the BGC borders are just offsets defined in the cluster detection rules, we renamed the highest level that is displayed to “Region”.

A *region* in antiSMASH 5 corresponds to the *gene cluster* annotation in antiSMASH 4 and earlier.

###How are antiSMASH 5 regions defined?

In the first step, all gene products of the analyzed sequence are searched against a database of highly conserved enzyme HMM profiles (core-enzymes), which are indicative of a specific BGC type.
In a second step, pre-defined cluster rules are employed to define individual *protoclusters* encoded in the region.
These make up a *core*, which is extended by its *neighbourhood*, which constiutes of genes encoded up- and downstream of the *core*.

Here is an example of a rule for detecting a protocluster for a type I PKS:

![Example cluster rule](img/clusterrules.png)

Whenever antiSMASH finds a gene coding for a protein that has as PKS\_AT domain and a PKS\_KS domain of various sub-types, a new “Type I PKS *protocluster*” feature is generated within the region; this feature comprises the *core* gene-product(s) that trigger the rule (i.e. the PKS encoding genes and extends the *neighborhood* to the left and right of the core genes by 20 kb to the left and right (as defined by the EXTENT parameter in the rule definition).
The values for the different cluster types are empirically determined and generally tend to overpredict, i.e. included also adjacent genes.
After the *protocluster* features are assigned (note: there can be multiple protocluster features within a single *region*), they are checked for overlaps (as defined by the CUTOFF parameter) and are grouped into several types of *candidate clusters* to reflect the observation that many BGCs actually comprise several classes of biosynthetic machinery. For example glycopeptides like vancomycin or balhimycin (shown) are synthesized via NRPS, but also contain a type III PKS as a precursor pathway.


![Balhimycin biosynthetic gene cluster](img/bal-cluster.png)

Thus, the displayed region contains the `NRPS` *protocluster* (green bar) and a `T3PKS` *protocluster* yellow bar.
As their neighbourhoods overlap, they are assigned to a *candidate cluster*.

###Candidate cluster types
![Figure candidate clusters](img/regionLogic.png)


####Chemical hybrid
These candidate clusters contains protoclusters which share cluster-defining CDS/genes/gene products.
They will also include protoclusters within that shared range that do
not share a CDS, provided that they are completely contained within the supercluster border.
For example, case **A** in the image above.

In the example, CDS 1 and 2 define the protocluster of type A, and CDS 2 and 4 define the protocluster of type B.
Since both protoclusters share a CDS that defines those protoclusters, a *chemical hybrid* candidate cluster is created.
If CDS 4 and some later CDS were also contributing to a third protocluster type, it would be merged into this same candidate cluster.
If CDS 3 defined another protocluster which did not extend past CDS 1 or 4, then that new protocluster would also be included in the chemical hybrid,
under the assumption that it is relevant to the other protoclusters.


####Interleaved
These candidate clusters contain protoclusters which do not share cluster-defining CDS features,
but their core locations overlap, e.g. case **B** in the image above.
 
####Neighbouring
These candidate clusters are the weakest form of hybrid candidates.
They contain protoclusters which do not match either *chemical* or *interleaved* variants,
but transitively overlap in their neighbourhoods.
Every protocluster in a "neighbouring candidate cluster" will also belong to one of the other kinds of candidate clusters, including the *single* kind, described below.

####Single
This kind of candidate clusters exists where only one protocluster is contained, e.g. case **D**.
It exists only for internal consistency.
A `single` candidate cluster will not exist for a protocluster which is contained in either a chemical hybrid or an interleaved candidate cluster,
but will exist for each inside a `neighbouring` candidate.
For example, both protoclusters in case **C** will have an independent `single` candidate, along with the `neighbouring`.

## Region Results page

![Region display](img/region_display.jpg)

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
be displayed above the gene.

### Gene details

![Gene details display](/img/gene_details.jpg)

Clicking the gene will provide more information on
the gene: its annotation, its smCOG (secondary metabolism gene family), its
location, and cross-links specific to that gene.

### Detailed annotation for PKS/NRPS domains

![Region display](img/DetailedDomainAnnotation.png)


In the middle panel, "Detailed annotation", you can find more in-depth
information on the selected gene cluster.  For predicted modular polyketide
synthase (PKS) and/or nonribosomal peptide synthetase (NRPS) proteins, you will
find the domain annotations.

Clicking on a domain image will prompt more
information to be displayed, such as the name of the detected domain, its
precise location, any substrate specificites predicted, and a link to run Blast
on the domain.  For predicted Lantipeptide clusters, the predicted core peptide
sequences of all identified prepeptides is displayed.
A list of detected domains can be found [here](modules/nrps_pks_domains.md).

### Identifying similar BGCs

The tab "Homologous gene clusters", displays the top ten gene clusters
from the internal antiSMASH database that are most similar to a detected gene
cluster, visually aligned to it. The drop-down selection menu can be used to
browse through the gene clusters. Genes with the same colour are putative
homologs based on significant Blast hits between them.
Similar information is provided in the "KnownCluserBlast folder", which detects BGCs included in the curated MIBiG dataset.
"SubClusterBlast" provides information about conserved operons, which, for example are involved in precursor biosynthesis of non-proteinogenic amino acids.

### Prediction of putative core sturctures

![Structure Prediction](img/StructurePrediction.png)

In the upper side panel
on the right. "Predicted core structure", a rough prediction of the overall
chemical structure of a the product of a detected nonribosomal peptide or
polyketide biosynthesis gene cluster is given. The second folder "PKS/NRPS monomers" displays detailed predictions for
all monomers.  Prediction details are available for multiple methods.

PKS type I AT domain specificities are predicted using a twenty-four amino acid signature sequence of the active site (Yadav et al., 2003), as well as with pHMMs based on the method of Minowa et al. (Minowa et al., 2007), which is also used to predict co-enzyme A ligase domain specificities. NRPS A domain specificities are predicted using both the signature sequence method and the support-vector machines-based method of NRPSPredictor2 (Rausch et al., 2005 & Röttig et al., 2011), and the method of Minowa et al. (Minowa et al., 2007).
Ketoreductase domain-based stereochemistry predictions for PKSs (Starcevic et al., 2008) are also performed.

For PKS type II clusters, the side panel shows a list of the predicted starter units along with bitscores, a list of the predicted number of malonyl elongations along with bitscores, the predicted product class, a list of product molecular weights predictions for each combination of starter unit and number of malonyl elongations.
Furthermore, it displays each gene/protein that is involved in the polyketide biosynthesis of the cluster.
For each gene/protein the type is indicated and for some a prediction of function is displayed.
More details on the predictions can be found [here](modules/t2pks.md).

A chemical structure is displayed for NRPS and Type I PKS metabolites, which is derived by combining the results of the domain analyses.

**IMPORTANT NOTE: This is a structure prediction of the core structure of the molecule; it is very likely the final molecule will be different!**

### Downloading results

![Main menu](img/download_results.jpg)

In the upper right, a small list of buttons offers further functionality. The
question-mark button will get you to this help page. The exclamation-mark button
leads to a page explaining about antiSMASH. The downward-pointing arrow will
open a menu offering to download the complete set of results from the antiSMASH
run, a summary GenBank output file, or a log file for debug purposes.
The GenBank file can be viewed in a genome browser such as Artemis.

**Results on the public webserver are only kept for ONE month and will be deleted afterwards. It is highly recommended that you download the full result set before they expire.**
