At the moment, there are three options available to install antiSMASH:

  - Using the [Bioconda](https://bioconda.github.io/index.html) distribution.
  - Using the pre-built Debian installer. This obviously is limited to Debian
    and related distributions.
  - Using one of the pre-built Docker images. A slightly larger download, but
    zero-fuss install on any system that can run Docker.
  - Manual install. Most work, but most options to customise your install.


## Bioconda

**Note:** Bioconda at the moment still provides antiSMASH 4.1.0, not the new version 5. We are hoping to fix this soon.

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

## On Debian Linux 9

**Note:** We are still working on an antiSMASH 5 installer script.

For 64bit AMD/Intel Debian 9 machines, all the required dependencies are available
either from the official Debian repositories, or from the custom antiSMASH
repository. If you are allowed to `sudo`, installing antiSMASH is as easy as:

```bash
curl -q https://bitbucket.org/antismash/antismash/downloads/install_deb.sh > install_deb.sh
bash install_deb.sh
```

## Using Docker

If you're not on Debian, but don't want to bother with the full-blown
installation, there are two docker images you can use.

**Note:** We are still working on antiSMASH 5 docker images.

### antiSMASH standalone

This image includes all the required databases, no further configuration needed.
It is a ~7 GB download at the moment. If you have docker installed, just grab
the wrapper script and get going:

```bash
mkdir ~/bin    # not required if you already have that
curl -q https://bitbucket.org/antismash/docker/raw/HEAD/standalone/run_antismash > ~/bin/run_antismash
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
curl -q https://bitbucket.org/antismash/docker/raw/HEAD/standalone-lite/run_antismash > ~/bin/run_antismash
chmod a+x ~/bin/run_antismash
```

#### Installing the PFAM database
You need the hmmer 3.1 hmmpress tool in your path for this to work.
```bash
mkdir -p /data/databases/pfam && cd /data/databases/pfam
curl ftp://ftp.ebi.ac.uk/pub/databases/Pfam/releases/Pfam27.0/Pfam-A.hmm.gz > Pfam-A.hmm.gz
gunzip Pfam-A.hmm.gz
hmmpress Pfam-A.hmm
```

#### Installing the ClusterBlast database
You need GNU tar with xz compression support in your path for this to work.
```bash
mkdir -p /data/databases/clusterblast && cd /data/databases/clusterblast
curl https://dl.secondarymetabolites.org/releases/4.0.0/clusterblast_20170105_v8_31.tar.xz > clusterblast_20170105_v8_31.tar.xz
tar -xJf clusterblast_20170105_v8_31.tar.xz
```

Note that due to the nature of the wrapper script having to do some magic
mapping between your system and the container, you always need to provide input
file and output directory first, and in that order.

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

Then, create a python virtualenv for installing the antiSMASH python
dependencies. This is not required, but highly recommended.

```bash
virtualenv --python $(which python3) as5
source as5/bin/activate
```

Next, obtain a copy of the antiSMASH source code. We don't have any final release of antiSMASH 5 yet,
so either clone the antiSMASH 5 git repository:

```bash
git clone https://github.com/antismash/antismash.git
cd antismash
```

or grab a zip file of the development tree by opening https://github.com/antismash/antismash/ in your
browser, clicking the "clone or download" button and selecting "Download ZIP" there.


All the python dependencies are specified in the `setup.py` file, so you can just run the install
from the antiSMASH source code directory:

```bash
pip install .
```

Then, run `download-antismash-databases` to grab and prepare the
databases:

```bash
download-antismash-databases
```

To check all of the dependencies are installed and antiSMASH can find them, run:

```bash
antismash --check-prereqs
```

If antiSMASH prints "All prerequisites satisfied", you're good to go.
