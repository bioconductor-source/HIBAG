HLA Genotype Imputation with Attribute Bagging
===

[![Build Status](https://travis-ci.org/zhengxwen/HIBAG.png)](https://travis-ci.org/zhengxwen/HIBAG)


## Features

HIBAG is a state of the art software package for imputing HLA types using SNP data, and it relies on a training set of HLA and SNP genotypes. HIBAG can be used by researchers with published parameter estimates instead of requiring access to large training sample datasets. It combines the concepts of attribute bagging, an ensemble classifier method, with haplotype inference for SNPs and HLA types. Attribute bagging is a technique which improves the accuracy and stability of classifier ensembles using bootstrap aggregating and random variable selection.


## Bioconductor:

Development Version: v0.99.3

[http://www.bioconductor.org/packages/devel/bioc/html/HIBAG.html](http://www.bioconductor.org/packages/devel/bioc/html/HIBAG.html)

### Changes in Bioconductor Version:

* optimize the calculation of hamming distance using SSE2 and hardware POPCNT instructions if available
* hardware POPCNT: 2.4x speedup for large-scale data, compared to the implementation in CRAN v1.2.4
* optimized SSE2 instructions without hardware POPCNT: 1.5x speedup for large-scale data, compared to the implementation in v1.2.4


## License

![GPLv3](http://www.gnu.org/graphics/gplv3-88x31.png)
[GNU General Public License, GPLv3](http://www.gnu.org/copyleft/gpl.html)


## Package Maintainer

Xiuwen Zheng ([zhengxwen@gmail.com](zhengxwen@gmail.com) / [zhengx@u.washington.edu](zhengx@u.washington.edu))


## Pre-fit Model Download:

The website (Prof. Bruce S. Weir):

[http://www.biostat.washington.edu/~bsweir/HIBAG/](http://www.biostat.washington.edu/~bsweir/HIBAG/)


## Citation

Zheng, X. *et al*. HIBAG-HLA genotype imputation with attribute bagging. *The pharmacogenomics journal* 14, 192–200 (2014).
[http://dx.doi.org/10.1038/tpj.2013.18](http://dx.doi.org/10.1038/tpj.2013.18)


## Installation

* Development version from Github:
```R
library("devtools")
install_github("zhengxwen/HIBAG")
```
The `install_github()` approach requires that you build from source, i.e. `make` and compilers must be installed on your system -- see the R FAQ for your operating system; you may also need to install dependencies manually.

* Install the package from the source code:
[download the source code](https://github.com/zhengxwen/HIBAG/tarball/master)
```
wget --no-check-certificate https://github.com/zhengxwen/HIBAG/tarball/master -O HIBAG_latest.tar.gz
** Or **
curl -L https://github.com/zhengxwen/HIBAG/tarball/master/ -o HIBAG_latest.tar.gz

** Install **
R CMD INSTALL HIBAG_latest.tar.gz
```

* Install the package from the source code with the support of hardware POPCNT (requiring SSE4.2):
You have to customize the package compilation, see: [CRAN: Customizing-package-compilation](http://cran.r-project.org/doc/manuals/r-release/R-admin.html#Customizing-package-compilation)

Change "~/.R/Makevars" to, if your machine supports SSE4.2 or higher AVX:
```
## for C code
CFLAGS=-g -O3 -march=native
## for C++ code
CXXFLAGS=-g -O3 -march=native
```
Or force to create hardware POPCNT code:
```
## for C code
CFLAGS=-g -O3 -msse4.2 -mpopcnt
## for C++ code
CXXFLAGS=-g -O3 -msse4.2 -mpopcnt
```
