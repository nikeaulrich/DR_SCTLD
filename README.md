# DR Metagenomics

**Code notebook for analyzing SCTLD in Bayahiba, DR**

Samples collected 122021 (pre-SCTLD outbreak) and 072023 (post-SCTLD outbreak) from one site \

#### Species collection 
* DCYL - Dendrogyra cylindrus
* DLAB - Diploria labyrinthiformis
* MCAV - Montastraea cavernosa
* MMEA - Meandrina meandrites
* PSTR - Pseudodiploria strigosa
* SSID - Siderastrea siderea


## Workflow

### QC
DR_QC.ipynb 
- Trim Galore
- host removal (using bowtie2)
- symbiont removal (fastq-screen)

### Assembly
DR_Assembly.ipnyb 
- Re-pair reads 
- Co-assemble by coral species - concatenated F and R reads for each species and assembled with megahit
- Map sample reads on to assembly (bowtie2)
- Binning (Metabat2, Concoct, Maxbin2)
- De-replication of bins (Das Tool)
- Classification of MAGs (gtdbtk)


### Analyzing reads
**Taxonomy** \
DR_kraken_abundances.ipnyb - Kraken2 and Bracken \
DR_bracken_abundances_to_ASV.ipnyb - normalizing ASV abundances \
DR_phyloseq.ipnyb - phyloseq, DESeq, LDA enrichment \
DR_taxa_plots.ipnyb - ASV abundance plots \
DR_taxa_plots_family.ipnyb - ASV abundance plots at family level \
DR_viral_content: genomad

**Functional** \
DR_humann_analysis.ipnyb - HUMaN3 analysis to explore pathways and gene families
DR_functional_visualization.ipnyb - ordination and heatmaps


### Analyzing MAGs
- Annotation tools: Bakta, eggnog, RAST, prokka (uses Bakta annotation) 
- Functional pathways: GhostKOALA, Kegg Decoder, COGclassifier