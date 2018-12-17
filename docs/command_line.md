Command Line Use
----------------

**Note**: These are instructions for the soon-to-be-released antiSMASH version
5. antiSMASH 4 command line options are slightly different. Use `antismash
--help-showall` to get help for version 4.


The antiSMASH command line tool comes with a built-in help system. Use
`antismash --help` to display help for the most common options, or `antismash
--help-showall` to get a description of all possible options.


### Fast run

Running antismash without parameters will run the core detection modules and all
fast cluster-specific analysis steps. More time-consuming options such as the
ClusterBlast analyses, cluster-based PFAM annotations, smCoG tree generation,
etc. will not be run. On a quad-core machine, running the *Streptomyces
coelicolor* genome with these options will take about two minutes.

This is how the antiSMASH web service runs fast mode jobs from
https://fast.antismash.secondarymetabolites.org/

Example:

```bash
antismash streptomyces_coelicolor.gbk
```


### Minimal run

Running antismash with the `--minimal` parameter will only run the core
detection modules, none of the cluster-specific analysis steps. On a quad-core
machine, running the *Streptomyces coelicolor* genome in minimal mode will take
about one minute. In general, we recommend running without the `--minimal`
option, as a default fast run will generate much more useful results for only
one additional minute of runtime.

Example:

```bash
antismash --minimal streptomyces_coelicolor.gbk
```

### Full-featured run


On a quad core machine, running all these options for the *Streptomyces
coelicolor* genome will take a bit over 20 minutes.


```bash
antismash --cb-general --cb-knownclusters --cb-subclusters --asf --pfam2go --smcog-trees streptomyces_coelicolor.gbk
```
