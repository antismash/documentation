## Overview page

The overview page contains a summary of all regions found in all records/contigs within the input given to antiSMASH.

![Region overview](/img/cluster_overview.png)

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

The last two columns containing comparisons to the MiBIG database will only be shown if antiSMASH was run with the [KnownClusterBlast](/modules/clusterblast/) option.

Clicking anywhere in the row that is not already an external link will take you to the detailed results for that region.
