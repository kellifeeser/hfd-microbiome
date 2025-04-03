---
title: '**Taxonomy Set-Up**'
author: "Kelli Feeser"
date: "2025-02-04"
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
  html_notebook:
    code_folding: hide
    css: styles.css
    number_sections: yes
    toc: yes
    toc_depth: 4
    toc_float: true
    fig.caption: yes
  html_document:
    code_folding: hide
    css: styles.css
    number_sections: yes
    toc: yes
    toc_depth: 4
    toc_float: true
    fig.caption: yes
editor_options:
  chunk_output_type: inline
---

\

::: homelink
<a href="https://kellifeeser.github.io/hfd-microbiome/index.html" target="_blank" style="text-align:right">Back to Home</a>
:::

\

------------------------------------------------------------------------

Document last updated: 2025-02-04

------------------------------------------------------------------------

\

# Set-up project naming from reproducible code {.unlisted .unnumbered .hidden}



# Set-up {.unlisted .unnumbered .hidden}






## load packages



## load cache



## load rds





\
\

# OTU table stats

\

OTU tables rarefied to the following sequencing depths:

-   16S: 26,694 sequences per sample
\

**Bacterial & Archaeal Dataset:**

- 707 OTUs
- 89 samples
\

Available metadata:


```
##  [1] "SampleID"                           "Old_SampleID"                       "Experiment"                         "R1_fastq_filename"                 
##  [5] "Group"                              "Diet"                               "Day"                                "DietSubGroup"                      
##  [9] "SampleType"                         "Location"                           "Mouse"                              "MouseNumber"                       
## [13] "Cluster"                            "Diet_Day"                           "DietSubGroup_Day"                   "Diet_Day_SampleType"               
## [17] "Diet_Day_SampleType_Location"       "Diet_Day_SampleType_Location_Mouse"
```

\

# Set-up taxonomy for plotting {.unlisted .unnumbered .hidden}

\

## Global: Calculate  mean relative abundance by tax rank and export csv of relative abundance 

### merge samples within dataset 



### tax glom and export 

(no generating code just copy and replace)



## Samples: Calculate relative abundance by tax rank and export csv of relative abundance {.unlisted .unnumbered .hidden} 


1. create vectors of top 10 taxa names to plot for all ranks
  - auto-generated code found: 
  a. set minimum threshold of 0.5% all-sample (a.k.a global) mean relative abundance
    - (so that taxa below this threshold won't get plotted)
2. tax glom by each rank
3. transform to relative abundance
3. psmelt
4. add column "[rank]_all" to preserve names not in top 10 
5. recode all taxa not in top 10 to by "LowAbundance" & revalue with specifics later (in dat_Bac.[rank].r ~~and in dat_Fun.[rank].r~~)


### generating code: 


```r
Bac.rank.names<-rank_names(Bac)[2:6]
# add this line to beginning
  #  cat('\n # Set min plotting threshold to 0.5% relative abundance (all-sample a.k.a global mean) \n')

#also adding psmelt step

for(rank in Bac.rank.names) {

  cat('\n## \n')

  cat('################## \n')

  cat('# Bac:', rank, '# \n')

  cat('################## \n')

  cat('\n')
  
   cat('min_nname_Bac_', rank, '<-length(unique(Bac_', rank, '_Mean_Abund$', 
       rank, '[Bac_', rank, '_Mean_Abund$Bac_', rank, '_Mean > 0.5]))',
       sep = '')
  
  cat('\n \n ')

    cat('if (min_nname_Bac_', rank, ' < 10){
  Bac.', rank, '.names.to.plot<-top_n(Bac_', rank, '_Mean_Abund, min_nname_Bac_', rank, ', Bac_', rank, '_Mean)$',rank, ' 
} else {
  Bac.', rank, '.names.to.plot<-top_n(Bac_', rank, '_Mean_Abund, 10, Bac_', rank, '_Mean)$', rank, '
}', sep = '')

  cat('\n# \n')
  
  cat('\nBac.',rank,'.A <- tax_glom(Bac, taxrank="',rank,'")\n',sep = '')
  
  cat('Bac.',rank,' <- prune_taxa(taxa_sums(Bac.',rank,'.A) > 0, Bac.',rank,'.A)\n',sep = '')

  cat('Bac.',rank,'.r  = transform_sample_counts(Bac.',rank,', function(x) x / sum(x) )\n',sep = '')

  cat('dat_Bac.',rank,'.r <- psmelt(Bac.',rank,'.r)\n',sep = '')

  cat('dat_Bac.',rank,'.r$',rank,' <- as.character(dat_Bac.',rank,'.r$',rank,') \n',sep = '')

  cat('dat_Bac.',rank,'.r$',rank,'_all <- dat_Bac.',rank,'.r$',rank,' \n',sep = '')
  
  cat('dat_Bac.',rank,'.r$',rank,' <- if_else(dat_Bac.',rank,'.r$',rank,' %in% Bac.',rank,'.names.to.plot, dat_Bac.',rank,'.r$',rank,', "LowAbundance") \n',sep = '')

  cat('\n## \n')

  cat('\n \n')

}
```


### create vectors of top 10 taxa names

#### Bac

(paste in previous generated code)



## Group low abundance (!%inc% top 10 taxa)

(no generating code just copy paste)

### Bac



