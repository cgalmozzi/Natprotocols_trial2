# Selective Ribosome Profiling: a tool to study interactions of translating ribosomes in yeast	


## Contents

- [Overview](#overview)
- [Scripts](#Scripts)
- [Reference files](#Reference-files)
- [Demo](#demo)
- [Results](#results)
- [License](./LICENSE)
- [Issues](https://github.com/ebridge2/lol/issues)
- [Citation](#citation)

# Overview

Analysis of the generated SeRP data starts by employing publicly available as well as customized read processing and alignment tools that are generally used for RP analysis. SeRP-specific tools are used in subsequent steps for identifying substrates and for the characterization of factor-specific binding properties. Here we provide a number of python scripts for initial analysis of SeRP data sets, which can be run on standard desktop computers. However initial analyses can also be done using alternative tools provided by web-based platforms like RiboGalaxy (https://ribogalaxy.ucc.ie/) and Trips-Viz (https://trips.ucc.ie/). 

# Scripts

```
Supplementary script A (Ribosome_Assignment).
Supplementary script B (3_nt_Periodicity).
Supplementary script C (Footprint_Length_Distribution).
Supplementary script D (Total_Enrichment).
Supplementary script E (Gene_Profiles).
Supplementary script F (Binding_Detection).
Supplementary script G (Metagene_Profiles).
Supplementary script H build_references

```

# Reference files

```
yeast_cds_all.txt
yeast_genes_with_introns.txt
yeast_genes.pkl
yeast_introns.pkl
yeast_sequence.pkl
yeast_tRNA.pkl

```

# System Requirements

## Hardware Requirements

The `lol` package requires only a standard computer with enough RAM to support the operations defined by a user. For minimal performance, this will be a computer with about 2 GB of RAM. For optimal performance, we recommend a computer with the following specs:

RAM: 16+ GB  
CPU: 4+ cores, 3.3+ GHz/core

The runtimes below are generated using a computer with the recommended specs (16 GB RAM, 4 cores@3.3 GHz) and internet of speed 25 Mbps.

## Software Requirements

### OS Requirements

The package development version is tested on *Linux* operating systems. The developmental version of the package has been tested on the following systems:

Linux: Ubuntu 16.04  
Mac OSX:  
Windows:  

The CRAN package should be compatible with Windows, Mac, and Linux operating systems.

Before setting up the `lolR` package, users should have `R` version 3.4.0 or higher, and several packages set up from CRAN.

#### Installing R version 3.4.2 on Ubuntu 16.04

the latest version of R can be installed by adding the latest repository to `apt`:

```
sudo echo "deb http://cran.rstudio.com/bin/linux/ubuntu xenial/" | sudo tee -a /etc/apt/sources.list
gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
gpg -a --export E084DAB9 | sudo apt-key add -
sudo apt-get update
sudo apt-get install r-base r-base-dev
```

which should install in about 20 seconds.

# Installation Guide

## Stable Release

`lolR` is available in a stable release on CRAN:

```
install.packages('lolR')
```

## Development Version

### Package dependencies

Users should install the following packages prior to installing `lolR`, from an `R` terminal:

```
install.packages(c('ggplot2', 'abind', 'irlba', 'knitr', 'rmarkdown', 'latex2exp', 'MASS', 'randomForest'))
```

which will install in about 30 seconds on a recommended machine.

The `lolR` package functions with all packages in their latest versions as they appear on `CRAN` on December 13, 2017. Users can check [CRAN snapshot](https://mran.microsoft.com/timemachine/) for details. The versions of software are, specifically:
```
abind_1.4-5
latex2exp_0.4.0
ggplot2_2.2.1
irlba_2.3.1
Matrix_1.2-3
MASS_7.3-47
randomForest_4.6-12
```

If you are having an issue that you believe to be tied to software versioning issues, please drop us an [Issue](https://github.com/neurodata/lol/issues). 

### Package Installation

From an `R` session, type:

```
require(devtools)
install_github('neurodata/lol', build_vignettes=TRUE, force=TRUE)  # install lol with the vignettes
require(lolR)
vignette("lol", package="lolR")  # view one of the basic vignettes
```

The package should take approximately 40 seconds to install with vignettes on a recommended computer. 

# Demo

## Functions

For interactive demos of the functions, please check out the vignettes built into the package. They can be accessed as follows:

```
require(lolR)
vignette('lol')
vignette('pca')
vignette('cpca')
vignette('lrcca')
vignette('mdp')
vignette('xval')
vignette('qoq')
vignette('simulations')
vignette('nearestCentroid')
```

## Extending the lolR Package

The lolR package makes many useful resources available (such as embedding and cross-validation) for simple extension. 

To extend the lolR package, check out the vignettes:

```
require(lolR)
vignette('extend_embedding')
vignette('extend_classification')
```

# Results

In this [benchmark comparison](http://docs.neurodata.io/lol/lol-paper/figures/real_data.html), we show that LOL does better than all linear embedding techniques in supervised HDLSS settings when dimensionality is high (d > 100, ntrain <= d) on 20 benchmark problems from the [UCI](https://archive.ics.uci.edu/ml/index.php) and [PMLB](https://github.com/EpistasisLab/penn-ml-benchmarks) datasets. LOL provides a good tradeoff between maintaining the class conditional difference (good misclassification rate) in a small number of dimensions (low number of embedding dimensions).

# Citation

For usage of the package and associated manuscript, please cite according to the enclosed [citation.bib](./citation.bib).
