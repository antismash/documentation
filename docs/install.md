At the moment, there are two options available to install antiSMASH:

  - Using one of the pre-built Docker images. A slightly larger download, but
    zero-fuss install on any system that can run Docker.
  - A manual install, with three options to get the required dependencies:
      - Using the pre-built Debian installer. This obviously is limited to Debian
        and related distributions.
      - Using the [Bioconda](https://bioconda.github.io/index.html) distribution.
      - Full manual install. Most work, but most options to customise your install.


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

antiSMASH relies on a number of external tools to perform its analyses. You need to install those
before installing antiSMASH. Use one of the methods mentioned below to get all relevant dependencies,
then continue with [installing the latest antiSMASH release](#installing-the-latest-antismash-release)
to install antiSMASH itself.

### Dependencies via Debian/Ubuntu

For 64bit AMD/Intel Debian or Ubuntu machines, all the required dependencies are available
either from the official Debian repositories, or from the custom antiSMASH
repository.

First add the antiSMASH debian repository:
```bash
sudo apt-get update
sudo apt-get install -y apt-transport-https
sudo wget http://dl.secondarymetabolites.org/antismash-stretch.list -O /etc/apt/sources.list.d/antismash.list
sudo wget -q -O- http://dl.secondarymetabolites.org/antismash.asc | sudo apt-key add -
sudo apt-get update
```
then install the binaries themselves
```bash
sudo apt-get install hmmer2 hmmer diamond-aligner fasttree prodigal ncbi-blast+ muscle glimmerhmm
```
If you want to use CASSIS or the full RODEO analysis for RiPPs and agree to the [MEME license](http://meme-suite.org/doc/copyright.html), add `meme-suite` to that list.

After the dependencies are installed, [create a Python virtual environment](#create-a-python-virtual-environment).

### Dependencies via Bioconda

**Note:** Bioconda has an antiSMASH package directly, but that's still version 4.1.0, not the new version 5, so don't use that.

Bioconda is a channel for the [conda](http://conda.pydata.org/docs/intro.html)
package manager with a focus on bioinformatics software. Once you have [bioconda
installed](https://bioconda.github.io/index.html), installing antiSMASH is as
easy as running

```bash
conda create -n antismash
conda activate antismash
conda install hmmer2 hmmer diamond fasttree prodigal blast muscle glimmerhmm
```

If you want to use CASSIS or the full RODEO analysis for RiPPs and agree to the [MEME license](http://meme-suite.org/doc/copyright.html),
you should also install MEME. Unfortunately, conda does not provide a MEME 4.11.2 build that is installable in a Python3 environment.
We can't use more recent versions of MEME because the MEME developers drastically changed output formats and only the 4.11.2 version was
confirmed to work with CASSIS. You will have to install a C compiler and follow the official install instructions for
[meme](http://meme-suite.org/doc/install.html?man_type=web).

Later, if you want to run antiSMASH, simply call

```bash
conda activate antismash
antismash my_input.gbk
```

After the dependencies are installed, continue with [installing the latest antiSMASH release](#installing-the-latest-antismash-release).

### Dependencies via Homebrew

[Homebrew](https://brew.sh) is a package manager for macOS (and Linux). It comes with a
[great selection of bioinformatics packages](https://github.com/brewsci/homebrew-bio).

First, add the `brewsci/bio` tap to get access to the bioinformatics packages.
```bash
brew tap brewsci/bio
```
then install the binaries themselves
```bash
brew install hmmer2 hmmer diamond fasttree prodigal blast muscle brewsci/science/glimmerhmm
```

Unfortunately, Homebrew doesn't fix the file name conflicts between the hmmer and hmmer2 packages,
so to have both tools available, run the following:
```bash
export HMMER2_BINDIR="$(brew --prefix)/opt/hmmer2/bin"
export BREW_BINDIR="$(dirname $(brew link -n hmmer2 | head -n2 | tail -n1))"
pushd ${BREW_BINDIR}
for FNAME in ${HMMER2_BINDIR}/*; do
    BINARY=$(basename $FNAME)
    ln -s $FNAME ${BINARY/hmm/hmm2}
done
popd
unset HMMER2_BINDIR BREW_BINDIR
```

If you want to use CASSIS or the full RODEO analysis for RiPPs and agree to the [MEME license](http://meme-suite.org/doc/copyright.html), run
```bash
brew install https://raw.githubusercontent.com/brewsci/homebrew-bio/12b4ef4679c5c6ed21ab7c046c2709c4cefb4338/Formula/meme.rb
```
to install MEME in version 4.11.2

After the dependencies are installed, [create a Python virtual environment](#create-a-python-virtual-environment).

### Full manual install

Install the following dependencies:

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

After the dependencies are installed, [create a Python virtual environment](#create-a-python-virtual-environment).


### Create a Python virtual environment

Not strictly necessary, but highly recommended if you're not already using `conda`.

* Create and activate a virtual environment (this can be skipped, but is highly recommended)
```bash
virtualenv -p $(which python3) ~/as5env
source ~/as5env/bin/activate
```

Later, if you want to run antiSMASH, simply call

```bash
source ~/as5env/bin/activate
antismash my_input.gbk
```

Now, continue with [installing the latest antiSMASH release](#installing-the-latest-antismash-release).

### Installing the latest antiSMASH release

* Download and extract the antiSMASH source (using version 5.1 as an example):
```bash
wget https://dl.secondarymetabolites.org/releases/5.1.1/antismash-5.1.1.tar.gz
tar -zxf antismash-5-1-1.tar.gz
```

* Install antiSMASH (again, using 5.1 as an example, the name will match the download step):
```bash
pip install ./antismash-5.1.1
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
