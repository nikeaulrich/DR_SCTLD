# DR Metagenomics

**Code notebook for analyzing SCTLD in Bayahiba, DR**

Samples collected 122021 (pre-SCTLD outbreak) and 072023 (post-SCTLD outbreak) from one site \
Sample and monitoring information in [SCTLD_samples](https://github.com/sagw/SCTLD_samples/tree/main/Sample_Data)

#### Species collection 
* DCYL - Dendrogyra cylindrus
* DLAB - Diploria labyrinthiformis
* MCAV - Montastraea cavernosa
* MMEA - Meandrina meandrites
* PSTR - Pseudodiploria strigosa
* SSID - Siderastrea siderea


## Workflow

### QC
[DR_QC.ipynb](https://github.com/nikeaulrich/DR_SCTLD/blob/main/DR_QC.ipynb) 
- Trim Galore
- host removal (using bowtie2)
- symbiont removal (fastq-screen)

### Assembly
[DR_Assembly.ipnyb](https://github.com/nikeaulrich/DR_SCTLD/blob/main/DR_Assembly.ipynb) 
- Re-pair reads 
- Co-assemble by coral species - concatenated F and R reads for each species and assembled with megahit
- Map sample reads on to assembly (bowtie2)
- Binning (Metabat2, Concoct, Maxbin2)
- De-replication of bins (Das Tool)
- Classification of MAGs (gtdbtk)


### Analyzing reads
**Taxonomy** \
[DR_kraken_abundances.ipnyb](https://github.com/nikeaulrich/DR_SCTLD/blob/main/analysis/DR_kraken_abundances.ipynb) - Kraken2 and Bracken \
[DR_bracken_abundances_to_ASV.ipnyb](https://github.com/nikeaulrich/DR_SCTLD/blob/main/analysis/bracken_abundances_to_ASV.ipynb) - normalizing ASV abundances \
[DR_phyloseq.ipnyb](https://github.com/nikeaulrich/DR_SCTLD/blob/main/analysis/DR_phyloseq.ipynb) - phyloseq, DESeq, LDA enrichment \
[DR_taxa_plots.ipnyb](https://github.com/nikeaulrich/DR_SCTLD/blob/main/analysis/DR_taxa_plots.ipynb) - ASV abundance plots \
[DR_taxa_plots_family.ipnyb](https://github.com/nikeaulrich/DR_SCTLD/blob/main/analysis/DR_taxa_plots_family.ipynb) - ASV abundance plots at family level \
[DR_viral_content](https://github.com/nikeaulrich/DR_SCTLD/blob/main/analysis/DR_viral_content.ipynb): Genomad

**Functional** \
[DR_humann_analysis.ipnyb](https://github.com/nikeaulrich/DR_SCTLD/blob/main/analysis/DR_humann_analysis.ipynb) - HUMaN3 analysis to explore pathways and gene families
[DR_functional_visualization.ipnyb](https://github.com/nikeaulrich/DR_SCTLD/blob/main/analysis/DR_functional_visualization.ipynb) - ordination and heatmaps


### Analyzing MAGs
- Annotation tools: Bakta, eggnog, RAST, prokka (uses Bakta annotation) 
- Functional pathways: GhostKOALA, Kegg Decoder, COGclassifier, Metabolic