---
layout: default
title: About
permalink: /about/
---

This blog will house a number of vignettes and case studies introducing you to time resolved RNA-seq methods (trRNA-seq; also referred to as nucleotide recoding RNA-seq, or NR-seq). trRNA-seq is a collection of methods that make use of metabolic labeling to study the dynamics of RNA synthesis and degradation. RNA metabolc labeling involves feeding cells a nucleoside analog, which is a chemical compound that looks like a naturally occuring nucleoside. The most common metabolic label is 4-thiouridine, which cells will incorporate into RNA where they would normally incorporate uridine. Therefore, any RNA transcribed after the metabolic label is introduced will have some percentage of its uridines replaced with 4-thiouridine. trRNA-seq involves detecting the metabolic label in sequenced RNA via unique chemistries that either convert or disrupt the hydrogen bonding pattern of the label. This yields apparent T-to-C mutations in the RNA-seq reads that indicate sites of label incorporation. 

The first set of trRNA-seq methods were TimeLapse-seq (developed by the Simon lab; I am a PhD student in this lab), SLAM-seq (developed by the Ameres lab), and TUC-seq (developed by the Micura lab). While standard RNA-seq can identify changes in RNA levels, these methods significanlty facilitated assaying changes in RNA synthesis and degradation kinetics. In my posts, I will discuss the history of these methods, why they are useful, and recent extensions of the base methods. My personal expertise is in the analysis and interpretation of data from these methods though, so the bulk of my educational material will be in covering the modeling/bioinformatics involved in deriving useful biological insights from trRNA-seq.
