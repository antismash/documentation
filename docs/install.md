At the moment, there are three options available to install antiSMASH:

  - Using the Bioconda package.
  - Using one of the pre-built Docker images. A slightly larger download, but
    zero-fuss install on any system that can run Docker.
  - A manual install, with three options to get the required dependencies:
      - Using the pre-built Debian installer. This obviously is limited to Debian
        and related distributions.
      - Using the [Bioconda](https://bioconda.github.io/index.html) distribution.
      - Full manual install. Most work, but most options to customise your install.


## Using Bioconda

**Note**: The bioconda packages are built and updated by volunteers from the bioconda
project and might lag behind the official antiSMASH releases.

Bioconda is a channel for the [conda](http://conda.pydata.org/docs/intro.html)
package manager with a focus on bioinformatics software. Once you have [bioconda
installed](https://bioconda.github.io/index.html), install antiSMASH with the following:

```bash
conda create -n antismash antismash
conda activate antismash
download-antismash-databases
conda deactivate
```

Later, if you want to run antiSMASH, simply call

```bash
conda activate antismash
antismash my_input.gbk
```

## Using Docker (or podman)

If you're not on Debian, but don't want to bother with the full-blown manual
installation, there are two docker images you can use. To use the wrapper scripts with podman,
just replace all mentions of "docker" in the commands below with "podman".

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
curl -q https://dl.secondarymetabolites.org/releases/latest/download_antismash_databases_docker > ~/bin/download_antismash_databases
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

Bioconda is a channel for the [conda](http://conda.pydata.org/docs/intro.html)
package manager with a focus on bioinformatics software. Once you have [bioconda
installed](https://bioconda.github.io/index.html), install the dependencies:

```bash
conda create -n antismash
conda activate antismash
conda install hmmer2 hmmer diamond fasttree prodigal blast muscle glimmerhmm
```

If you want to use CASSIS or the full RODEO analysis for RiPPs and agree to the [MEME license](http://meme-suite.org/doc/copyright.html),
also run `conda install meme==4.11.2`.

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

- [diamond](https://github.com/bbuchfink/diamond) (versions 0.9.22, 0.9.24, 2.0.7, 2.0.9, and 2.0.15 tested, 2.1.7 breaks with antiSMASH 7.0.0 and older)
- [fasttree](http://www.microbesonline.org/fasttree/#Install) (versions 2.1.9 and 2.1.11 tested)
- [GlimmerHMM](https://ccb.jhu.edu/software/glimmerhmm/) (version 3.0.4 tested)
- [hmmer2](http://hmmer.janelia.org/download.html) (version 2.3.2 tested, append a 2 to all hmmer2 executables to avoid conflict with hmmer3 executable names, like hmmalign -> hmmalign2)
- [hmmer3](http://hmmer.janelia.org/download.html) (3.1b2 tested)
- [meme](http://meme-suite.org/meme-software/) (version 4.11.2 required for meme specifically, which is only used in the cassis module, fimo tested with 5.5.2)
- [NCBI blast+](ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/) (versions 2.10.0 and 2.11.0 tested)
- [prodigal](http://prodigal.ornl.gov/) (version 2.6.3 tested)
- python (versions 3.9, 3.10, and 3.11 tested, any version >= 3.9.0 should work)
- python-virtualenv (not needed, but highly recommended)

For versions of antiSMASH prior to 7.0, there are additional requirements:
- [muscle](http://www.drive5.com/muscle/downloads.htm) (versions 3.8.31 and 3.8.1551 tested, version 5 and above are not compatible)

After the dependencies are installed, [create a Python virtual environment](#create-a-python-virtual-environment).


### Create a Python virtual environment

Not strictly necessary, but highly recommended if you're not already using `conda`.

* Create and activate a virtual environment (this can be skipped, but is highly recommended)
```bash
virtualenv -p $(which python3) ~/asenv
source ~/asenv/bin/activate
```

Later, if you want to run antiSMASH, simply call

```bash
source ~/asenv/bin/activate
antismash my_input.gbk
```

Now, continue with [installing the latest antiSMASH release](#installing-the-latest-antismash-release).

### Installing the latest antiSMASH release

**See [here](https://dl.secondarymetabolites.org/releases/) for all release versions**, adjust the instructions below as required.

* Download and extract the antiSMASH source (using 6.0.0 as an example, see above for other versions):
```bash
wget https://dl.secondarymetabolites.org/releases/6.0.0/antismash-6.0.0.tar.gz
tar -zxf antismash-6.0.0.tar.gz
```

* Install antiSMASH (again, using 6.0 as an example, the name will match the download step):
```bash
pip install ./antismash-6.0.0
download-antismash-databases
```

Prepare data files and performance caches with the following (NOTE: for versions before 7.0, change `--prepare-data` to `--check-prereqs`)
```bash
antismash --prepare-data
```

If you want to see the available command line options, use
```bash
antismash --help
```
or, for a full list of all available options, including debug options
```bash
antismash --help-showall
```
