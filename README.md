# CD177 modulates the functions and homeostasis of tumor-infiltrating regulatory T cell

## Abstract: 

Regulatory T (Treg) cells are one of the major immunosuppressive cell types in cancer and a potential target for immunotherapy, 
but targeting tumor-infiltrating (TI) Treg cells has been challenging. Here we perform single-cell RNA sequencing of immune cells 
from renal clear cell carcinoma (ccRCC) patients and identify two distinct transcriptional fates for TI Treg cells, Fate-1 and Fate-2. 
The Fate-1 signature associates with poorer ccRCC prognosis; meanwhile, CD177, normally expressed on neutrophils, is specifically 
expressed on Fate-1 TI Treg cells in solid cancer types including renal, liver, breast, and colon but not other TI or peripheral Treg cells. 
Mechanistically, blocking CD177 reduces the suppressive activity of Treg cells in vitro, while Treg-specific deletion of Cd177 leads to 
decreased tumor growth and reduced TI Treg frequency in mice. Our results thus uncover a functional CD177+ TI Treg population that may serve as 
a target for TI Treg-specific immunotherapy.

## Methods: 

Briefly, we prepared single-cell libraries as per the 10X Genomics Chromium 5ʹ library and Gel Bead Kit Version 2 (10X Genomics, Pleasanton, CA). 
Pooled libraries were sequenced using the Illumina HiSeq 4000 in the University of Iowa Genomics Division. Basecalls were converted to FASTQ 
files using the Illumina bcl2fastq software and aligned to the human genome (GRCh38) using the CellRanger v2.2 pipeline. Cell quality 
was checked for the total expression of mitochondrial reads. Cells with <200 or >5000 unique genes were filtered out. After processing, 
clustering was performed using the Seurat R package (v2.3.4), correcting for patient variability using canonical correlation analysis (CCA). 
The single-cell RNA sequencing data were first normalized to correct for sequencing depth by scaling the total UMI counts per cell to 10,000. 
The normalized data were then log-transformed after adding a pseudo count of one. Finally, each gene’s log normalized counts were z-score transformed 
to have mean zero and a standard deviation of one. The Seurat V2 package was used to align data from the three patients by using CCA on 1,000 
highly variable genes identified using the built-in FindVariableGenes function. The top 20 dimensions of the aligned CCA were then used to 
cluster cells with resolution/granularity set to 1.2. Cells and clusters are visualized using t-Distributed Stochastic Neighbor Embedding (t-SNE). 
Differential gene expression analysis was performed using the Wilcoxon rank-sum test comparing TI versus PB Treg cells. 
The p-values from the Wilcoxon rank-sum test are adjusted using Bonferroni correction. For the cell trajectory analysis 
and pseudo-time estimates, we utilized the Monocle 2 R package (v2.8.0) which is based on the reverse graph embedding algorithm. 
The DifferentialGeneTest function in Monocle v2 was used to identify genes differing between PB and TI Treg cells. 
Genes with a q-value (adjusted p-value) < .01 were used to construct the trajectory. Branched expression analysis modeling (BEAM) 
was performed using the default settings of the Monocle 2 R package. Single-sample gene set enrichment analysis utilized the singleR R 
package (v0.2.0) for naïve, exhausted, cytotoxicity and cell cycle gene sets that are relevant to T cells. 
The gene sets consisted of 1) Cytotoxicity: NKG7, CCL4, PRF1, GZMA, GZMB, IFNG, CCL3;  2) Exhaustion: PDCD1, TIGIT,  LAG3,   HAVCR2, CTLA4; 
3) naïve CCR7, TCF7, LEF1, SELL; 4) Effector/memory: CD27, CD28, CCR7, CCR5, SELL and FAS. 
Cell cycle regression for individual Treg cells was performed with the Seurat p Package, as previously described40. 
For ccRCC data, the quantified gene expression counts and V(D)J T cell receptor sequences for single-cell RNA sequencing are available 
at the Gene Expression Omnibus (GEO) at [GSE121638](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE121638). The same processing 
and quality control procedures were applied to count-level data from the HCC SCRC dataset: [GSE98638](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE98638).

## Processed Data

Due to space limitations of a github repo, full outputs of alignments are available [10.5281/zenodo.4311824](https://zenodo.org/record/4311825). Monocle embedding of the renal clear cell carcinoma Tregs, can be accessed ProcessedData folder under ccRCCTregs.monocle.rds.

## Contact
Questions, comments, suggestions, please feel free to contact Nick Borcherding via this repository, [email](mailto:ncborch@gmail.com), or using [twitter](https://twitter.com/theHumanBorch). 
