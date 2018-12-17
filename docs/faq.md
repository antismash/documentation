Frequently Asked Questions
--------------------------

### Can I run antiSMASH locally as a stand-alone program?

Yes. A stand-alone version of antiSMASH is available from the [download page](https://antismash.secondarymetabolites.org/#!/download).

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
