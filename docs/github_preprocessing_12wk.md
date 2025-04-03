---
title: "**HFD Microbiome: 16S Amplicon Pre-processing of 12-week Experiment**"
subtitle: "Raw sequence processing and OTU table generation using usearch v11, OTU table cleaning using phyloseq (R), and basic data overview"
author: "Kelli Feeser"
date: "2025-04-02"
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
  markdown: 
    wrap: 72
---

\



**16S Primers:**\
- *341F* -- 5′-CCT ACG GGN GGC WGC AG-3′\
- *805R* -- 5′-GAC TAC HVG GGT ATC TAA TCC-3′\
\


**Expected Insert Length:**\
- 465 bp\
\

# Basic Sequence Data Prep

\

## Fastq file name formatting

\

**Raw Fastqs** are in folder *0_RawFastqs/RawFastqs_nameformatted*\

-   Names are formatted so that the identifying sample label appears
    before the first underscore. This makes the downstream auto fasta
    header relabeling seemless and ensures that when the sequences
    across samples are combined into 1 file, each sequence is properly
    labeled in the headers.\

-   For this project, sample ids were numeric values [1,316], so again
    for simplifying downstream processing, I renamed each raw fastqs
    file to have the prefix 'hfd12wk' and set all numberic values to
    have 3 digits.\

    -   Having only numberic values as sample identifiers is likely to
        create issues when reading into R/phyloseq\
    -   Naming examples:\
        -   "1" → "hfd12wk001"; files = 1_S97_L001_R1_001.fastq →
            hfd12wk001_R1.fastq\
        -   "316" → "hfd12wk316"; files = 316_S337_L001_R1_001.fastq →
            hfd12wk316_R1.fastq\

-   Names are formatted so that the identifying sample label appears
    before the first underscore. This makes the downstream auto fasta
    header relabeling seemless and ensures that when the sequences
    across samples are combined into 1 file, each sequence is properly
    labeled in the headers.\

-   For this project, sample ids were numeric values [1,316], so again
    for simplifying downstream processing, I renamed each raw fastqs
    file to have the prefix 'hfd12wk' and set all numberic values to
    have 3 digits.\

    -   Having only numberic values as sample identifiers is likely to
        create issues when reading into R/phyloseq\
    -   Naming examples:\
        -   "1" → "hfd12wk001"; files = 1_S97_L001_R1_001.fastq →
            hfd12wk001_R1.fastq\
        -   "316" → "hfd12wk316"; files = 316_S337_L001_R1_001.fastq →
            hfd12wk316_R1.fastq\

\

# Read-in raw USEARCH OTU tables, taxonomy, and metadata ---- {.tabset .tabset-pills .hidden .unlisted .unnumbered}

\

## read-in raw 16S data {.unnumbered .tabset .tabset-pills}

\

### 16S otu table {.unnumbered}



\

### 16S sintax taxonomy file {.unnumbered}

16S ref db: RDP 16S v19\



\

### 16S metadata file {.unnumbered}



\

####  {.unnumbered}

## initiate phyloseq objects -----

\





# Start here {.hidden .unlisted .unnumbered}





# basic data overview -----------------------------------------------------------

phyloseq-class experiment-level object
otu_table()   OTU Table:         [ 1090 taxa and 245 samples ]
sample_data() Sample Data:       [ 245 samples by 11 sample variables ]
tax_table()   Taxonomy Table:    [ 1090 taxa by 7 taxonomic ranks ]

-   N samples:
    245\
-   N OTUs:
    1,090\
    \

**USEARCH version**\
usearch11.0.667_i86linux64



\
\

**Ref db: rdp_16s_v19**



-   24,642 sequences in taxonomic reference database\
    \
    \

## Full Datasets, unrarefied, unprunned

### Read Counts


```{=html}
<table class="huxtable" data-quarto-disable-processing="true" style="border-collapse: collapse; border: 0px; margin-bottom: 2em; margin-top: 2em; ; margin-left: auto; margin-right: auto;  " id="tab:raw-read-count-echo">
<caption style="caption-side: top; text-align: center;">(#tab:raw-read-count-echo) </caption><col><col><tr>
<th style="vertical-align: top; text-align: left; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0.4pt 0pt;    padding: 10pt 6pt 6pt 10pt; font-weight: bold; font-size: 10pt;">Seqs per sample</th><th style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0.4pt 0pt;    padding: 10pt 10pt 6pt 6pt; font-weight: bold; font-size: 10pt;">Full 16S OTU table</th></tr>
<tr>
<td style="vertical-align: top; text-align: left; white-space: normal; border-style: solid solid solid solid; border-width: 0.4pt 0pt 0pt 0pt;    padding: 6pt 6pt 6pt 10pt; font-weight: normal; font-size: 10pt;">min</td><td style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0.4pt 0pt 0pt 0pt;    padding: 6pt 10pt 6pt 6pt; font-weight: normal; font-size: 10pt;">226</td></tr>
<tr>
<td style="vertical-align: top; text-align: left; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0pt 0pt;    padding: 6pt 6pt 6pt 10pt; font-weight: normal; font-size: 10pt;">max</td><td style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0pt 0pt;    padding: 6pt 10pt 6pt 6pt; font-weight: normal; font-size: 10pt;">32,036</td></tr>
<tr>
<td style="vertical-align: top; text-align: left; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0pt 0pt;    padding: 6pt 6pt 6pt 10pt; font-weight: normal; font-size: 10pt;">mean</td><td style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0pt 0pt;    padding: 6pt 10pt 6pt 6pt; font-weight: normal; font-size: 10pt;">20,585</td></tr>
<tr>
<td style="vertical-align: top; text-align: left; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0.1pt 0pt;    padding: 6pt 6pt 6pt 10pt; font-weight: normal; font-size: 10pt;">sd</td><td style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0.1pt 0pt;    padding: 6pt 10pt 6pt 6pt; font-weight: normal; font-size: 10pt;">3,467</td></tr>
<tr>
<td style="vertical-align: top; text-align: left; white-space: normal; border-style: solid solid solid solid; border-width: 0.1pt 0pt 0pt 0pt;    padding: 6pt 6pt 10pt 10pt; font-weight: normal; font-size: 10pt;">total</td><td style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0.1pt 0pt 0pt 0pt;    padding: 6pt 10pt 10pt 6pt; font-weight: normal; font-size: 10pt;">5,043,233</td></tr>
</table>

```

\

### Unique Domains detected {.tabset .tabset-pills}

\

#### 16S {.unnumbered}


```
## [1] "Bacteria"    "uncl_Domain" "Eukaryota"
```

\

### Reads per Domain {.tabset .tabset-pills}

\

#### 12-week {.unnumbered}




```{=html}
<table class="huxtable" data-quarto-disable-processing="true" style="border-collapse: collapse; border: 0px; margin-bottom: 2em; margin-top: 2em; ; margin-left: auto; margin-right: auto;  " id="tab:unique-domain-reads-table">
<caption style="caption-side: top; text-align: center;">(#tab:unique-domain-reads-table) </caption><col><col><col><tr>
<th style="vertical-align: top; text-align: left; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0.4pt 0pt;    padding: 10pt 6pt 6pt 10pt; font-weight: bold; font-size: 10pt;">Domain</th><th style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0.4pt 0pt;    padding: 10pt 6pt 6pt 6pt; font-weight: bold; font-size: 10pt;">reads_assigned</th><th style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0.4pt 0pt;    padding: 10pt 10pt 6pt 6pt; font-weight: bold; font-size: 10pt;">percentage_all_reads</th></tr>
<tr>
<td style="vertical-align: top; text-align: left; white-space: normal; border-style: solid solid solid solid; border-width: 0.4pt 0pt 0pt 0pt;    padding: 6pt 6pt 6pt 10pt; font-weight: normal; font-size: 10pt;">Bacteria</td><td style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0.4pt 0pt 0pt 0pt;    padding: 6pt 6pt 6pt 6pt; font-weight: normal; font-size: 10pt;">5,042,647</td><td style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0.4pt 0pt 0pt 0pt;    padding: 6pt 10pt 6pt 6pt; font-weight: normal; font-size: 10pt;">99.99%</td></tr>
<tr>
<td style="vertical-align: top; text-align: left; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0pt 0pt;    padding: 6pt 6pt 6pt 10pt; font-weight: normal; font-size: 10pt;">uncl_Domain</td><td style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0pt 0pt;    padding: 6pt 6pt 6pt 6pt; font-weight: normal; font-size: 10pt;">437</td><td style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0pt 0pt;    padding: 6pt 10pt 6pt 6pt; font-weight: normal; font-size: 10pt;">0.01%</td></tr>
<tr>
<td style="vertical-align: top; text-align: left; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0.1pt 0pt;    padding: 6pt 6pt 10pt 10pt; font-weight: normal; font-size: 10pt;">Eukaryota</td><td style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0.1pt 0pt;    padding: 6pt 6pt 10pt 6pt; font-weight: normal; font-size: 10pt;">149</td><td style="vertical-align: top; text-align: right; white-space: normal; border-style: solid solid solid solid; border-width: 0pt 0pt 0.1pt 0pt;    padding: 6pt 10pt 10pt 6pt; font-weight: normal; font-size: 10pt;">0.00%</td></tr>
</table>

```

\

***For now, only continuing with reads assigned at \>= 80% confidence to
domain = Bacteria or Archaea***\
\
\
\

# Clean OTU table



## Prune taxa





**Domain-level:**\

1.  Remove anything unclassified at Domain-level
    (437
    reads;
    69
    OTUs)

2.  Remove Domain = Eukaryota
    (149
    reads;
    1
    OTUs)

**Phylum-level:**\







3.  Remove Phylum = "uncl_Bacteria"
    (12,991
    reads;
    357
    OTUs)

4.  Remove Phylum = "uncl_Archaea"
    (0
    reads;
    0
    OTUs)

5.  Look at Phylum "Cyanobacteriota"

    -   It contains these Classes:
        Cyanophyceae, Chloroplast

**Class-level:**\







6.  Remove Class = "Chloroplast"
    (122
    reads;
    4
    OTUs)

7.  Remove Class = "uncl_Cyanobacteria/Chloroplast"
    (0
    reads;
    0
    OTUs)

**Family-level:**\



8.  Remove Family = "Mitochondria"
    (0
    reads;
    0
    OTUs)\



**Remaining data:**\
- 5,029,534
total reads\
- 20,528.71
average reads/sample\
- 659 OTUs\
- 245 samples\
\
\

## Removing singleton OTUs

At this point, the unrarefied **12wk** 16S dataset with unwanted taxa
prunned has 659
OTUs and a total of
5,029,534
reads.\
\





## **12wk**

32
singleton OTUs were present and removed (corresponding to
32
reads)\

-   627 OTUs
    remain\

-   5,029,502
    total reads remain\

    -   average:
        20,528.58\

    -   sd:
        3,460.712\

\

## BacArch OTU Rarefaction Curves

\

### 12wk samples with highest read count





\

### All samples, full depth range


``` r
par(mar = c(5.1, 4.1, 5.1, 2.1)) # c(bottom, left, top, right)

dev.copy(png,'/Users/L347123/Desktop/hfd-microbiome/docs/figures/rarefaction/Rarecurve_12wk_fullrange.png',width = 650)

plot_rarecurves((phylo2vegan_OTU(hfd_12wk_unrare_min2)), step = 1000,xlim=c(0,max(sample_sums(hfd_12wk_unrare_min2)*1.1)),ylim=c(0,350),
  title(main="Rarefaction Curves for all 12wk samples\nDomain=Bacteria or Archaea, taxa prunned", adj=0),
   label=T,cex.main=1.2)

dev.off()
```

![](/Users/L347123/Desktop/hfd-microbiome/docs/figures/rarefaction/Rarecurve_12wk_fullrange.png){width="90%"}

### All samples, max 15k seqs/samples



![](/Users/L347123/Desktop/hfd-microbiome/docs/figures/rarefaction/Rarecurve_12wk_nolabs_max15k.png){width="90%"}

### All samples, max 20k seqs/samples



![](/Users/L347123/Desktop/hfd-microbiome/docs/figures/rarefaction/Rarecurve_12wk_wlabs_max20k.png){width="90%"}

## Rarefying 12wk OTU table to 13,006 seqs/sample



\



**Rarefaction threshold of 13,006 sequences per sample -\> we'd lose:**\

-   
    samples overall
    (%
    of the total 245 samples)\
    --
    3
    OTUs
    (0.5%
    of the total
    627 OTUs)\
    -- 624 OTUs
    remain\

*Of note, I am rarefying via subsampling WITHOUT replacement and
removing OTUs no longer in dataset*\

\
Indeed:\
- 2 samples removed because they contained fewer reads than
`sample.size`.\
- 3 OTUs were removed because they are no longer present in any sample
after random subsampling\

# Final OTU table stats

-   624 OTUs
    remain\

-   3,160,458
    total reads remain\

    -   average:
        13,006\

    -   sd:
        0\

\


