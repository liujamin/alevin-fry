<img alt="logo" src="https://github.com/COMBINE-lab/alevin-fry/raw/master/docs/logo.png" width="200">

# alevin-fry ![Rust](https://github.com/COMBINE-lab/alevin-fry/workflows/Rust/badge.svg) [![Anaconda-Server Badge](https://anaconda.org/bioconda/alevin-fry/badges/platforms.svg)](https://anaconda.org/bioconda/alevin-fry) [![Anaconda-Server Badge](https://anaconda.org/bioconda/alevin-fry/badges/license.svg)](https://anaconda.org/bioconda/alevin-fry) ![GitHub tag (latest SemVer)](https://img.shields.io/github/v/tag/combine-lab/alevin-fry?style=flat-square)

`alevin-fry` is a suite of tools for the rapid, accurate and memory-frugal processing single-cell and single-nucleus sequencing data.  It consumes RAD files generated by `salmon alevin`, and performs common operations like generating permit lists, and estimating the number of distinct molecules from each gene within each cell.  The focus in `alevin-fry` is on safety, accuracy and efficiency (in terms of both time and memory usage).

You can read the paper describing alevin fry, "Alevin-fry unlocks rapid, accurate, and memory-frugal quantification of single-cell RNA-seq data" [here](https://www.nature.com/articles/s41592-022-01408-3), and the pre-print [on bioRxiv](https://www.biorxiv.org/content/10.1101/2021.06.29.450377v1).

### Getting started with `alevin-fry` and dedicated documentation

While this `README` contains some useful information to get started and some pointers, `alevin-fry` has it's own dedicated documentation site, hosted on `ReadTheDocs`, that you can find [here](https://alevin-fry.readthedocs.io/en/latest/).

### More information 

* [**Quickstart guide using the `simpleaf` wrapper**](https://combine-lab.github.io/alevin-fry-tutorials/2023/simpleaf-piscem/)

* **Relationship to alevin**: Alevin-fry has been designed as the successor to alevin. It subsumes the core features of alevin, while also providing important new capabilities and considerably improving the performance profile. We anticipate that new method development and feature additions will take place primarily within the alevin-fry codebase.  Thus, we encourage users of alevin to migrate to alevin-fry when feasible.  That being said, alevin is still actively-maintained and supported, so if you are using it and not ready to migrate you can continue to ask questions and post issues in [the salmon repository](https://github.com/COMBINE-lab/salmon).

## FAQs 

Are you curious about processing details like [whether to use a sparse or dense index](https://github.com/COMBINE-lab/alevin-fry/discussions/38)? Do you have a question that isn't necessarily a bug report or feature request, and that isn't readily answered by the documentation or tutorials?  Then please feel free to ask over in the [Q&A](https://github.com/COMBINE-lab/alevin-fry/discussions/categories/q-a).

## Sister repositories

* The generation of the reduced alignment data (RAD) files processed by alevin-fry is done by either [piscem](https://github.com/COMBINE-lab/piscem) or [salmon](https://github.com/COMBINE-lab/salmon). The latest version of both are available on GitHub and via bioconda. 

* The [`simpleaf`](https://github.com/COMBINE-lab/simpleaf) repository contains a dedicated wrapper / workflow runner for processing data with `alevin-fry` that vastly simplifies both the creation of extended references and the subsequent quantification of samples. If you find that `simpleaf` is missing a feature that you'd like to have, please consider submitting a feature request in the [`simpleaf` repository](https://github.com/COMBINE-lab/simpleaf/issues).

* The [`pyroe`](https://github.com/COMBINE-lab/pyroe) repository provides tools to help easily construct an enhanced (_spliced + intronic_ or _spliced + unspliced_) transcriptome from a reference genome and GTF file.

* The [`fishpond`](https://github.com/mikelove/fishpond) package — maintained by @mikelove and his lab — contains the recommended relevant functions for reading `alevin-fry` output (particularly USA-mode output) into the R ecosystem, in the form of a [`singleCellExperiment`](https://bioconductor.org/packages/release/bioc/html/SingleCellExperiment.html) object.

* The [`alevinqc`](https://github.com/csoneson/alevinQC) package — maintained by @csoneson — provides tool and functions for performing quality control and assessment downstream of `alevin-fry`.

## Installing from bioconda

Alevin-fry is available for both x86 linux and OSX platforms [using bioconda](https://anaconda.org/bioconda/alevin-fry). On Apple silicon, you can either build (easily) from source (see below) or run `alevin-fry` under the rosetta 2 emulation layer.

With `bioconda` in the appropriate place in your channel list, you should simply be able to install via:


```{bash}
$ conda install alevin-fry
``` 

## Installing from crates.io

Alevin-fry can also be installed from [`crates.io`](https://crates.io/crates/alevin-fry) using `cargo`.  This can be done with the following command:

```{bash}
$ cargo install alevin-fry
```

## Building from source

If you want to use features or fixes that may only be available in the latest develop branch (or want to build for a different architecture), then you have to build from source.  Luckily, `cargo` makes that easy; see below.

Alevin-fry is built and tested with the latest (major & minor) stable version of [Rust](https://www.rust-lang.org/). While it will likely compile fine with slightly older versions of Rust, this is not a guarantee and is not a support priority.  Unlike with C++, Rust has a frequent and stable release cadence, is designed to be installed and updated from user space, and is easy to keep up to date with [rustup](https://rustup.rs/). Thanks to cargo, building should be as easy as:

```{bash}
$ cargo build --release
```

subsequent commands below will assume that the executable is in your path.  Temporarily, this can 
be done (in bash-like shells) using:

```{bash}
$ export PATH=`pwd`/target/release/:$PATH
```

## Citing alevin-fry

If you use `alevin-fry` in your work, please cite:

> He, D., Zakeri, M., Sarkar, H., Soneson, C., Srivastava, A., and Patro, R. Alevin-fry unlocks rapid, accurate and memory-frugal quantification of single-cell RNA-seq data. Nat Methods 19, 316–322 (2022). https://doi.org/10.1038/s41592-022-01408-3

**BibTeX:**

```
@Article{He2022,
author={He, Dongze and Zakeri, Mohsen and Sarkar, Hirak and Soneson, Charlotte and Srivastava, Avi and Patro, Rob},
title={Alevin-fry unlocks rapid, accurate and memory-frugal quantification of single-cell RNA-seq data},
journal={Nature Methods},
year={2022},
month={Mar},
day={01},
volume={19},
number={3},
pages={316-322},
issn={1548-7105},
doi={10.1038/s41592-022-01408-3},
url={https://doi.org/10.1038/s41592-022-01408-3}
}
