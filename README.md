# DGE analysis in Ewing sarcoma cells

Ewing sarcoma is a pediatric bone cancer which arises from the fusion of the EWSR1 and FLI1 genes ("EWSR1-FLI1" fusion oncogene).

Recently, some have proposed therapies for Ewing sarcoma which suppress EWSR1-FLI1. While these compounds are undergoing clinical trials currently, it is not clear how suppressing EWSR1-FLI1 impacts Ewing sarcoma tumor cells.

You have been provided with a Ewing sarcoma RNA-seq data set ("EwS.rds"). The data is in `RangedSummarizedExperiment` format. The metadata includes a column "condition" with two levels (1) shEF1 (EWSR1-FLI1 knock-down) and (2) shCTR (control). There are 3 shCTR samples and 4 shEF1 samples.

```R
> rse <- readRDS("EwS.rds")
> rse$condition
[1] "shCTR" "shCTR" "shCTR" "shEF1" "shEF1" "shEF1" "shEF1"
```

Your task is to perform a differential gene expression (DGE) analysis to determine what genes, and biological pathways / processes, are altered in EWSR1-FLI1 knock-down (shEF1) vs control (shCTR).

## Requirements

To complete this task, you should complete the analysis and generate an analysis report. This report can be in any format, however you are encouraged to create your report using RMarkdown and knit it to HTML (preferred) or PDF.

Minimally, the analysis report should contain all the following:

1. PCA summarizing the sample-level variance within the data set.
2. MA Plot showing the relationship between mean count and log2 fold change.
3. Table listing the differentially-expressed genes (DEGs).
4. Volcano plot showing all DGE results.
5. Heatmap showing the top 10 over- and under-expressed DEGs.
6. Enrichment analysis showing the top over- and under-expressed KEGG pathways.

## Guide


### Quick start

A minimal workflow for completing this task would involve the following steps:

1. Clone this repo

```shell
git clone https://github.com/Bishop-Laboratory/RA-Eval.git
```

2. Open the R project file (`RA-Eval.Rproj`) in RStudio
3. Set up the development environment using [renv](https://rstudio.github.io/renv/index.html) (optional)

```R
renv::restore()
```

4. Complete the task in an R script or (preferably) an RMarkdown notebook.
5. Create the report, along with figures / tables (or HTML/PDF RMarkdown report) in the repo.
6. Commit the results:

```shell
git add .
git commit -m "<some_informative_message>"
```

7. Create a repo on your personal github account called "RA-Eval".
8. Add your remote repo to your local repo as `origin`

```shell
git remote add origin https://github.com/<your_github_username>/RA-Eval.git
```

9. Push your code to the remote repo on GitHub

```shell
git push -u origin main
```

10. Send Henry the link to your GitHub repo once you are done.

### R Environment

To aid you in completing this task, we have included an R environment ('renv')
with the following packages that you are welcome to use in this task:

1. [tidyverse](https://www.tidyverse.org/)
  - Includes [ggplot2](https://ggplot2.tidyverse.org/), [dplyr](https://dplyr.tidyverse.org/), [readr](https://readr.tidyverse.org/), etc.
2. [DESeq2](https://bioconductor.org/packages/release/bioc/html/DESeq2.html)
3. [EnhancedVolcano](https://bioconductor.org/packages/release/bioc/html/EnhancedVolcano.html)
4. [pheatmap](https://cran.r-project.org/web/packages/pheatmap/index.html)
5. [enrichR](https://cran.r-project.org/web/packages/enrichR/index.html)
6. [msigdbr](https://cran.r-project.org/web/packages/msigdbr/index.html)
7. [clusterProfiler](https://bioconductor.org/packages/release/bioc/html/clusterProfiler.html)

To install the R environment with the correct packages, simply install [renv](https://rstudio.github.io/renv/index.html)

```R
install.packages("renv")
```

And then "restore" the R environment (installs all packages for the project):

```R
renv::restore()
```

### Getting help

This task is designed to test your ability to perform a basic DGE analysis, not your ability to use git, github, renv, RStudio, etc. Therefore, if you are finding difficulties setting things up or with any aspect of submitting your results, just let Henry know and he will assist you. 

If you are struggling with the DGE analysis, you are strongly encouraged to read and follow the [DESeq2 Vignette](https://bioconductor.org/packages/devel/bioc/vignettes/DESeq2/inst/doc/DESeq2.html). Here are some additional free learning resources which you may find valuable:

1. BIG Bioinformatics workshop on R and RNA-Seq: [link](https://www.bigbioinformatics.org/r-and-rnaseq-analysis)
2. Harvard training on RNA-Seq (with DESeq2): [link](https://wiki.harvard.edu/confluence/display/hbctraining/DGE+workshop)
3. Griffith Lab Training on DESeq2: [link](https://genviz.org/course/#module-04-expression)

If there are any instructions which are confusing or any questions / clarifications you want to raise, please just reach out to Henry and he will assist you.

