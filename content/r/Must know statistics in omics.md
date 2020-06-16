---
title: "Must know statistics in omics"
author: "Runhang"
date:  '2020-06'
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
- Parameter optimization: set a customized paramater is important;
Whether the peak detection is reliable, how to reduce noise for extracting real
compound signals
- Batch effect: Samples may change over time, needs quality control (EigenMS)
- pathway activity predition: needs to annoate metabolites first
