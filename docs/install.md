At the moment, there are three options available to install antiSMASH:

  - Using the [Bioconda](https://bioconda.github.io/index.html) distribution (currently limited to version 4.1).
  - Using the pre-built Debian installer. This obviously is limited to Debian
    and related distributions.
  - Using one of the pre-built Docker images. A slightly larger download, but
    zero-fuss install on any system that can run Docker.
  - Manual install. Most work, but most options to customise your install.


## Bioconda

**Note:** Bioconda at the moment still provides antiSMASH 4.1.0, not the new version 5.

Bioconda is a channel for the [conda](http://conda.pydata.org/docs/intro.html)
package manager with a focus on bioinformatics software. Once you have [bioconda
installed](https://bioconda.github.io/index.html), installing antiSMASH is as
easy as running

```bash
conda create -n antismash antismash
source activate antismash
download-antismash-databases
source deactivate antismash
```

This will install antiSMASH in a dedicated conda environment and download the
PFAM and ClusterBlast databases required for antiSMASH.

Then, if you want to run antiSMASH, simply call

```bash
source activate antismash
antismash my_input.gbk
```

You can use `antismash --help` to show all available options.

## On Debian/Ubuntu Linux

For 64bit AMD/Intel Debian or Ubuntu machines, all the required dependencies are available
either from the official Debian repositories, or from the custom antiSMASH
repository.

* Install binary dependencies:
   First add the antiSMASH debian repository:
```bash
sudo apt-get update
sudo apt-get install -y apt-transport-https
sudo wget http://dl.secondarymetabolites.org/antismash-stretch.list -O /etc/apt/sources.list.d/antismash.list
sudo wget -q -O- http://dl.secondarymetabolites.org/antismash.asc | apt-key add -
sudo apt-get update
```
then install the binaries themselves
```bash
sudo apt-get install hmmer2 hmmer diamond-aligner fasttree prodigal ncbi-blast+ muscle glimmerhmm
```
If you want to use CASSIS or the full RODEO analysis for RiPPs and agree to the [MEME license](http://meme-suite.org/doc/copyright.html), add `meme-suite` to that list.

* Download and extract the antiSMASH source (using version 5.1 as an example):
```bash
wget https://dl.secondarymetabolites.org/releases/5.1.0/antismash-5.1.0.tar.gz
tar -zxf antismash-5-1-0.tar.gz
```

* Create and activate a virtual environment (this can be skipped, but is highly recommended)
```bash
virtualenv -p $(which python3) as5env
source as5env/bin/activate
```
* Install antiSMASH (again, using 5.1 as an example, the name will match the download step):
```bash
pip install antismash-5-1-0
download-antismash-databases
```

We recommend running the prerequisite check to make sure everything is as expected with
```bash
antismash --check-prereqs
```

If you want to see the available command line options, use
```bash
antismash --help
```
or, for a full list of all available options, including debug options
```bash
antismash --help-showall
```

## Using Docker

If you're not on Debian, but don't want to bother with the full-blown manual
installation, there are two docker images you can use.

### antiSMASH standalone

This image includes all the required databases, no further configuration needed.
It is a ~9 GB download at the moment. If you have docker installed, just grab
the wrapper script and get going:

```bash
mkdir ~/bin    # not required if you already have that
curl -q https://dl.secondarymetabolites.org/releases/latest/docker-run_antismash-full > ~/bin/run_antismash
chmod a+x ~/bin/run_antismash
run_antismash <input file> <output directory> [antismash options]
```

Note that due to the nature of the wrapper script having to do some magic
mapping between your system and the container, you always need to provide input
file and output directory first, and in that order.

### antiSMASH standalone-lite

This image includes everything but the PFAM and ClusterBlast databases, meaning
you still have to install those. The wrapper script assumes those databases will
live in `/data/databases`, make sure to tweak the script and the rest of the
install instructions if you want to change this location.

First, grab the wrapper script:

```bash
mkdir ~/bin    # not required if you already have that
curl -q https://dl.secondarymetabolites.org/releases/latest/docker-run_antismash-lite > ~/bin/run_antismash
chmod a+x ~/bin/run_antismash
```

The easiest way to download the antiSMASH databases is using the database downloader script.
Again the wrapper script assumes your databases live in `/data/databases`. If you want to use
a different location, just provide that to the `download_antismash_databases` script as the parameter.

```bash
curl -q https://dl.secondarymetabolites.org/releases/latest/download_antismash_databases > ~/bin/download_antismash_databases
chmod a+x ~/bin/download_antismash_databases
download_antismash_databases
```

Note that due to the nature of the wrapper script having to do some magic
mapping between your system and the container, you always need to provide input
file and output directory first, and in that order:

```bash
run_antismash <input file> <output directory> [antismash options]
```

## Manual install

First, make sure you have the following antiSMASH dependencies installed:

- [diamond](https://github.com/bbuchfink/diamond) (versions 0.8.36, 0.9.17, and 0.9.24 tested, we recommended the 0.9 series)
- [fasttree](http://www.microbesonline.org/fasttree/#Install) (version 2.1.9 tested)
- [GlimmerHMM](https://ccb.jhu.edu/software/glimmerhmm/) (version 3.0.4 tested)
- [hmmer2](http://hmmer.janelia.org/download.html) (version 2.3.2 tested, append a 2 to all hmmer2 executables to avoid conflict with hmmer3 executable names, like hmmalign -> hmmalign2)
- [hmmer3](http://hmmer.janelia.org/download.html) (3.1b2 tested)
- [meme](http://meme-suite.org/meme-software/) (version 4.11.2 tested. **Version 4.11.4 changes output file formats, so don't use that.**)
- [muscle](http://www.drive5.com/muscle/downloads.htm) (version 3.8.31 tested)
- [NCBI blast+](ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/) (version 2.6.0 tested)
- [prodigal](http://prodigal.ornl.gov/) (version 2.6.3 tested)
- python (version 3.5.3 tested, any version >= 3.5.0 should work)
- python-virtualenv (not needed, but highly recommended)

Then follow the instructions from the Debian install section,
starting after the binary installation step.
