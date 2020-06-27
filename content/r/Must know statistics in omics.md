---
title: "Must know statistics in omics"
author: "Runhang"
date:  '2020-06-19'
output: html_document
---

## Introduction

  Many people working on omics have a strong background about the biological
pipeline and principle of NGS. But many at least folks around me seems like lack a
solid background about statistics to handle and interpret the sequencing results.
Here, I would like to highlight the statistical and computational skills we need
for analyzing amplicon data, RNA-seq data and Metabolomic data.


## Metabolomic

Workflow: spectra collection, raw data processing, statistical and functional analysis

**Things to consider when doing analysis**

- Parameter optimization: set a customized parameter is important;
Whether the peak detection is reliable, how to reduce noise for extracting real
compound signals

- Batch effect: Samples may change over time, needs quality control (EigenMS)

- pathway activity prediction: needs to annotate metabolites first (mummichog)

When we do an untargeted LC-MS, we often want to identify the molecule and then do
the downstream enrichment and pathway analysis. The common used database is [METLIN](https://metlin.scripps.edu/landing_page.php?pgcontent=mainPage). However determining molecule simply based on molecular mass (m/z)
is controversial because with one m/z, you often get several matched chemical compounds.
Secondly, selecting candidate features (m/z) is required good statistical skills.
Imagine you have 3 samples for each of two treatments, adjusted p-value (FRD) from t test or log fold change
,which is one should we look? Assume the concentrations of a metabolite in the control are 19000,
700, and 1000, contrasting to treatment A that does not have the metabolite.

```
t.test(c(19000,700,1000,9000),c(0,0,0,0))
```
Surprisingly, the unadjusted p-value from the t-test is 0.37.

```
t.test(c(log(19000),log(700),log(1000),log(9000)),c(0,0,0,0))
```

After the log-transformation, the unadjusted p-value  is 0.002. Therefore, log-transformation is critical for

getting a better candidate, otherwise, some good candidate might be omitted by huge standard deviation.

In other words, you might find a feature with 30,31,29,31 which significantly differs from control group
of 0,1,0,1, but this feature probably is not the feature you are trying to find.
