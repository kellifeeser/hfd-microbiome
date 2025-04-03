---
title: '**HFD amplicons from 02-week experiment**: Organizing Manuscript Analyses'
author: "Kelli Feeser"
date: "2025-03-05"
output:
  bookdown::html_document2:
    code_folding: hide
    css: styles.css
    number_sections: yes
    toc: yes
    toc_depth: 4
    toc_float: true
    fig.caption: yes
    keep_md: yes
  html_document:
    code_folding: hide
    css: styles.css
    number_sections: yes
    toc: yes
    toc_depth: 4
    toc_float: true
    fig.caption: yes
  html_notebook:
    code_folding: hide
    css: styles.css
    number_sections: yes
    toc: yes
    toc_depth: 4
    toc_float: true
    fig.caption: yes
editor_options:
  chunk_output_type: inline
  markdown: 
    wrap: 72
---

\

::: homelink
<a href="https://kellifeeser.github.io/hfd-microbiome/index.html" target="_blank" style="text-align:right">Back
to Home</a>
:::

\

------------------------------------------------------------------------

Document last updated: 2025-03-05

------------------------------------------------------------------------

\

# Set-up {.unlisted .unnumbered .hidden}



## load packages



## load cache



## load rds



# Data Overview

## OTU table

### **Rarefaction**

**Rarefaction threshold of 26,694 sequences per sample:**\

Loss of:

-   1
    samples overall
    (1.1%
    of the total 90 samples)
-   21
    OTUs
    (2.9%
    of the total
    728 OTUs)\
    -- 707 OTUs
    remain\

*I rarefied via subsampling WITHOUT replacement and removed OTUs no
longer in dataset.*\

\
After rarefaction:\
- 1 samples removed because they contained fewer reads than
`sample.size`.\
- 21 OTUs were removed because they are no longer present in any sample
after random subsampling\

I also removed the negative control.\
\



### Final OTU table stats

-   707 OTUs
    remain\
-   2,375,766
    total reads remain
    -   average:
        26,694

    -   sd:
        0
-   88 samples remain\
    \

## Samples & Experimental Design

Stool and luminal contents from control-diet and HFD fed mice

|                      |   Control-diet (2 wk)   |       HFD (2 wk)        | HFD (12 wk) |
|-----------------|:-----------------:|:------------------:|:---------------:|
| **Stool**            |                         |                         |             |
| Day 0                | 1 (random or composite) | 1 (random or composite) |             |
| Day 3                |            5            |            5            |             |
| Day 7                |            5            |            5            |             |
| Day 14               |            5            |            5            |             |
| **Luminal Contents** |       *(day 14)*        |       *(day 14)*        | *(week 12)* |
| *proximal gut*       |                         |                         |             |
| Jejunum              |            5            |            5            |      4      |
| Ileum                |            5            |            5            |      4      |
| *distal gut*         |                         |                         |             |
| Cecum                |            5            |            5            |      4      |
| Colon                |            5            |            5            |      4      |

: Experimental Design (number of mice per treatment).

***Stool on day 14, per protocol, was supposed to be collected just
before dissections began (i.e., not directly taken from gut).** I am not
sure how the protocol was followed however.*\
\

------------------------------------------------------------------------

# Analyses








## Temporal - Stool only

<img src="/Users/L347123/Desktop/hfd-microbiome/docs/github_OrganizingManuscriptAnalyses_wk02_files/figure-html/nmds-Stool-Diet-Day-Mouse-1.png" width="50%" style="display: block; margin: auto;" /><img src="/Users/L347123/Desktop/hfd-microbiome/docs/github_OrganizingManuscriptAnalyses_wk02_files/figure-html/nmds-Stool-Diet-Day-Mouse-2.png" width="50%" style="display: block; margin: auto;" />

\
\

------------------------------------------------------------------------

\

## Gut Location - Luminal contents only

<img src="/Users/L347123/Desktop/hfd-microbiome/docs/github_OrganizingManuscriptAnalyses_wk02_files/figure-html/nmds-Luminal-DietSubGroup-Location-1.png" width="90%" style="display: block; margin: auto;" />

\
\
\


<img src="/Users/L347123/Desktop/hfd-microbiome/docs/github_OrganizingManuscriptAnalyses_wk02_files/figure-html/nmds-Luminal-Location-facetDietSubGroup-1.png" width="50%" style="display: block; margin: auto;" />

<img src="/Users/L347123/Desktop/hfd-microbiome/docs/github_OrganizingManuscriptAnalyses_wk02_files/figure-html/nmds-Luminal-Mouse-facetDietSubGroup-1.png" width="60%" style="display: block; margin: auto;" />






