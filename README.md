# Relative Abundance of Transcripts (rats)

## Description

#### Who it is for

Anyone working in transcriptomics, analysing gene expression and transcript abundances.

#### What it does

It provides a method to detect changes in the relative abundance of the alternative transcripts (isoforms) of genes. 
This is called **Differential Transcript Usage (DTU)**.  

`Rats` differs from the other tools that call DTU, because it is tailored to alignment-free quantifications. It operates solely on
numerical abundances. This makes it independent of the quantification method, although it is originally meant to be used in workflows that use [Kallisto](http://pachterlab.github.io/kallisto/), [Sailfish](http://github.com/kingsfordgroup/sailfish) or [Salmon](https://github.com/COMBINE-lab/salmon) 
as isoform quantification tools, as output from these quantifiers is not compatible with the existing alignment-based DTU callers.

Detecting DTU is supplementary to the quantification of transcripts by tools like [Salmon](http://combine-lab.github.io/salmon/), 
[Sailfish](http://www.cs.cmu.edu/~ckingsf/software/sailfish/) and [Kallisto](http://pachterlab.github.io/kallisto/) and the detection 
of Differential Transcript Expression (DTE) by tools such as [Sleuth](http://pachterlab.github.io/sleuth/).

#### What it needs

This is an R source package, and will run on any platform with an R engine.

As input, `rats` requires transcript abundance estimates with or without bootstrapping. For convenience, these can also be extracted directly
from the output of [Sleuth](http://pachterlab.github.io/sleuth/). It also requires a look-up table matching transcript identifiers to 
respective gene identifiers.  

The package makes use of the [data.table](https://cran.r-project.org/web/packages/data.table/index.html) and 
[matrixStats](https://cran.r-project.org/web/packages/matrixStats/index.html) packages, as well as 
[ggplot2](https://cran.r-project.org/web/packages/ggplot2/index.html) and [shiny](https://cran.r-project.org/web/packages/shiny/shiny.pdf) for visualisations. All these are
available from CRAN.


## How to use rats


A full **tutorial vignette** is included in the package, explaining the input, output, commands and options. 
The vignette should be available locally by calling:

`browseVignettes("rats")`

We recommend studying the vignette before using `rats`.

### Dependencies

The package depends on a few third-party packages, which you may need to install first, 
if they are not present already:

`install.packages(c("data.table", "matrixStats", "ggplot2", "shiny"), dependencies=TRUE)`

If you have trouble installing these dependencies, your system could be missing source compilers for C and/or Fortran, and possibly other libraries, which you can see by scrolling back through the installation output to look for the errors. Please refer to the R manual for help.


### Installation

Platform-independent package releases are available from the [releases section](https://github.com/bartongroup/Rats/releases) on **Github**.
Download the latest release and then install it using:

`install.packages("<path/to/downloaded/package>", repos = NULL, type="source")`

Eventually, we aim to make `rats` available through **Bioconductor** as well.


### Differential Transcript Usage

A typical command to call DTU looks like this:

`results <- call_DTU(annot = my_identifiers_table, slo = my_sleuth_object,  name_A = "Condition-1", name_B = "Condition-2")`

Mandatory parameters:

* a data frame matching unique transcript identifiers to gene identifiers
* a sleuth object
* the names of two conditions recorded in the sleuth object

`rats` also accepts data input in **generic format** that does not depend on Sleuth. A function for creating the IDs table from a GTF file
is also provided. Please consult the vignette for syntax and formats specifications.

The output is a list containing two tables that list the final results as well as the intermediate calculations and decisions.
For details on the parameters, input and output, please refer to the tutorial vignette.


## Contact information

The `rats` R package was developed within [The Barton Group](http://www.compbio.dundee.ac.uk) at [The University of Dundee](http://www.dundee.ac.uk)
by Dr. Kimon Froussios, Dr. Kira Mourão and Dr. Nick Schurch.

To **report problems** or **ask for assistance**, please raise a new issue [on the project's support forum](https://github.com/bartongroup/Rats/issues).
Providing a *reproducible working example* that demonstrates your issue is strongly encouraged. Also, be sure to **read the vignette(s)**, and browse/search
the support forum before posting a new issue, in case your question is already answered there.

Enjoy!
