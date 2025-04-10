
# Example Files for Target-Enrichment Sequence Data Analyses

To help with file sizes, most of the example files for the target-enrichment sequence data analyses use sequences from the **Barnadesieae** subset, which includes the following ten taxa:

- *Barnadesia arborea*
- *Fulcaldea stuessyi*
- *Scaveola tomentosa*
- *Chuquiraga* sp.
- *Gongylolepis benthamania*
- *Schlechtendalia luzulaefolia*
- *Dasyphyllum reticulatum*
- *Hyalis argentea*
- *Famatinanthus* sp.
- *Nastanthus patagonicus*

For the transcriptome data, files are only provided for the *Schlechtendalia* sample. More files are available upon request.

---

## INPUT

### 4_Generating_Species_Phylogenies

#### 4-1_PHYLUCE

```
/contigs                          # from SPAdes output (also found in /OUTPUT/3-1_SPAdes)
/datasets.conf                   # list of species used in the analysis, separated by “_”
/phyluce_cos1061_probes.fasta   # probe file with gene names and sequences
```

#### 4-2_ModelSelection

```
/partition_finder.cfg           # configuration file for PartitionFinder
```

#### 4-4_RAxML_ASTRAL

```
/batch_exports/uce-*.fas        # converted from nexus to fasta format
/bs-files                       # locations of bootstrap gene trees (output of RAxML)
/concat_best.tre                # concatenated gene tree file
```

### 5_Phylogenetic_discordance

#### 5-3_PhyParts

```
Astral_best_rooted.tre          # rooted ASTRAL tree from /OUTPUT/4-4_RAxML_ASTRAL
```

---

## OUTPUT

### 2_Preparing_sequence_data

#### 2-1_FastQC

```
*.html                          # quality reports from FastQC on trimmed sequence data
```

### 3_Assembling_sequence_data

#### 3-1_SPAdes

```
/Barnadesia                     # individual folders per species (only Barnadesia included)
/contigs/*.fasta                # main SPAdes output for use in PHYLUCE
```

#### 3-3_GetOrganelle

```
/Barnadesia_arborea_plastome   # includes *.jpg Bandage plots; others available on request
```

### 4_Generating_Species_Phylogenies

#### 4-1_PHYLUCE

```
/taxon_set_all/
  all.conf                                # logs of recovered taxa and genes
  all.fasta                               # multifasta of matched gene sequences
  all.incomplete                          # loci not matched per taxon
  /mafft-nexus-trimmed/                   # aligned sequences (edge trimmed)
  /mafft-nexus-trimmed-clean/            # same as above with locus names removed
  /mafft-nexus-trimmed-clean-genes/      # for pseudo-coalescent analysis
  /mafft-nexus-trimmed-raxml/            # concatenated matrix with charsets
  /mafft-fasta/                          # same as above, in phylip-relaxed format

/log                                      # log files
/output                                   # lastz files
/exploded_fastas                          # unaligned sequences for summary stats
fasta_lengths.csv                         # summary stats
```

#### 4-2_ModelSelection

```
best_scheme.txt                # best model per gene (in analysis/ folder)
best_scheme_uce_table.txt     # output from tutorial loop
log.txt                        # log file
```

#### 4-3_RAxML_concat

```
RAxML_bipartitionsBranchLabels.out
RAxML_bootstrap.out
RAxML_bestTree.out
RAxML_bipartitions.out
RAxML_info.out
```

#### 4-4_RAxML_ASTRAL

```
/bootTree/
  RAxML_bootstrap*             # gene trees with bootstrap values
/bestTree/
  RAxML_bestTree*              # gene trees for ASTRAL
Astral_best.tre                # final ASTRAL tree (no support values)
Astral_lpp.tre                 # final ASTRAL tree (with LPP support)
Astral_bootcount.tre
*.log                          # associated log files
```

#### 4-5_OrthoFinder

```
SpeciesTree_rooted.txt         # rooted transcriptome species tree
```

#### 4-6_Chloroplast

```
/consensus_fastas              # consensus fastas (unaligned)
all_cns.fasta                  # concatenated aligned plastid matrix
all_cns_aligned.fasta          # aligned input for IQTree
```

### 5_Phylogenetic_discordance

#### 5-1_PhyParts

```
/root                          # rooted gene trees from /OUTPUT/4-4_RAxML_ASTRAL/bestTree
Astral_best_rooted.tre         # rooted to Scaevola_tomentosa
```

### 6_Hybridization

#### 6-1_PhyloNetworks

```
barnadesioideae_noBS_net2.png  # network output from Julia
```

### 7_WGD

#### 7-1_wgdv2

```
Schlechtendalia.fasta.transdecoder.pep   # final ORF peptides
Schlechtendalia.fasta.transdecoder.cds   # nucleotide coding sequences
Schlechtendalia.fasta.transdecoder.gff3  # ORF positions within transcripts
Schlechtendalia.fasta.transdecoder.bed   # BED file of ORF positions
/wgd_ELMM                               # wgdv2 output
```
