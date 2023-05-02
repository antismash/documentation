# antiSMASH Documentation

Welcome to the documentation of **antiSMASH**, the **anti**biotics & **S**econdary **M**etabolite **A**nalysis **SH**ell.

The antiSMASH framework allows the detection of clusters of co-occurring biosynthesis genes in genomes, called **B**iosynthetic **G**ene **C**lusters (**BGCs**).
BGCs often contain all the genes required for the biosynthesis of one or more **N**atural **P**roducts (**NPs**), also known as **specialized** or **secondary metabolites**.
NPs show interesting biological activities and many of them have been developed into essential medicines,
including antibiotics (*penicillin, streptomycin*), anti-cancer drugs (*bleomycin, doxorubicin*), or cholesterol-lowering agents (*lovastatin*).
This makes NPs and their encoding BGCs highly relevant from both a commercial and scientific perspective.

### How to Use antiSMASH - Public Web Version

The easiest way to get started with antiSMASH is to use [the public web
version](https://antismash.secondarymetabolites.org/).

See the *Using antiSMASH* section of this documentation for more information on how to [submit antiSMASH jobs](website_submission.md)
and [interpret the HTML output](understanding_output/index.md).

The [Glossary](glossary.md) explains some of the abbreviations used in antiSMASH and also provides an overview of the biosynthetic classes that antiSMASH can detect.

Frequently occurring questions can be found in the [FAQ](faq.md) section.
Please consult the FAQs before raising an [Issue](https://github.com/antismash/antismash/issues) on the antiSMASH GitHub page.


### How to Use antiSMASH - Local Installation

If you need to run many analyses or custom analyses, please download and install a local copy of antiSMASH.
Running large-scale analyses locally instead of on the our servers reduces the load and helps us to keep antiSMASH available for everybody.

For instructions on how to install antiSMASH locally, please see the [Install Guide](install.md).

### For developers 

This documentation is mainly addressed to users wanting to know more about the individual analyses of antiSMASH.
If you are interested in contributing to antiSMASH or in the technical design, please see the [antiSMASH GitHub Wiki](https://github.com/antismash/antismash/wiki).
