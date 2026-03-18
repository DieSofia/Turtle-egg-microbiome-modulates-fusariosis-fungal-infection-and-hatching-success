# Turtle-egg-microbiome-modulates-fusariosis-fungal-infection-and-hatching-success

Code used for the publication *Turtle-egg-microbiome-modulates-fusariosis-fungal-infection-and-hatching-success* submitted to the journal of *Communications Biology*. Authored by [Ana Sofia Carranco](https://www.uni-ulm.de/en/nawi/evolutionary-ecology-and-conservation-genomics/prof-dr-simone-sommer/phd-candidates/ana-sofia-carranco-msc/), [David Romo](https://www.usfq.edu.ec/en/profiles/david-romo), [Maria de Lourdes Torres](https://www.usfq.edu.ec/en/profiles/maria-de-lourdes-torres-proano), [Kerstin Wilhelm](https://www.uni-ulm.de/en/nawi/evolutionary-ecology-and-conservation-genomics/prof-dr-simone-sommer/secretary-and-technical-staff/dipl-biol-kerstin-wilhelm/), [Mark A. F. Gillingham](https://www.bi.mpg.de/staff/127952), [Simone Sommer](https://www.uni-ulm.de/en/nawi/evolutionary-ecology-and-conservation-genomics/prof-dr-simone-sommer/)


In this repo, you will find the code used for this manuscript. The code was created and updated by Ana Sofía Carranco and Mark A. F. Gillingham. 
For questions and requests, please contact me at ana.carranco-narvaez@uni-ulm.de or anasoficarranco@gmail.com

What this repository contains: 
1. **Essentials** — all files needed to run analyses from scratch
2. **QIIME2 pipeline** — raw amplicon processing (16S, ITS, TEF-1α)
3. **R analyses** — diversity, differential abundance,
   functional inference, and network analysis



## Repository Overview

This repository contains all bioinformatics scripts and metadata 
to reproduce the analyses in Carranco et al. (202X). 
The workflow is divided into two major stages:

1. **QIIME2 pipeline** — raw amplicon processing (16S, ITS, TEF-1α)
2. **R analyses** — diversity, differential abundance, 
    functional inference, and network analysis

---

## Data Availability

- Raw 16S, ITS and TEF-1α sequences: 
  NCBI SRA, BioProject [PRJNA######](https://www.ncbi.nlm.nih.gov/bioproject/)
- Processed feature tables and metadata: `data/`
- All paths in R scripts are **relative** to the repo root

---

## QIIME2 Pipeline

All scripts are in `qiime2/` and were run using 
**QIIME2 version 202X.X** (see `envs/qiime2_env.yml`).

### 16S rRNA (Bacteriome)
| Script | Description |
|--------|-------------|
| `qiime2/16S/01_import_denoise_16S.sh` | Import paired-end reads, DADA2 denoising, chimera removal |
| `qiime2/16S/02_taxonomy_16S.sh` | Taxonomic classification against SILVA 138 |
| `qiime2/16S/03_phylogeny_16S.sh` | Rooted phylogenetic tree (MAFFT + FastTree) |
| `qiime2/16S/04_export_16S.sh` | Export feature table, rep-seqs and taxonomy to R-ready formats |

### ITS (Mycobiome)
| Script | Description |
|--------|-------------|
| `qiime2/ITS/01_import_denoise_ITS.sh` | Import reads, ITSxpress trimming, DADA2 denoising |
| `qiime2/ITS/02_taxonomy_ITS.sh` | Taxonomic classification against UNITE |
| `qiime2/ITS/03_export_ITS.sh` | Export feature table and taxonomy |

### TEF-1α (Fusarium / FSSC identification)
| Script | Description |
|--------|-------------|
| `qiime2/TEF/01_import_denoise_TEF.sh` | Import reads, DADA2 denoising |
| `qiime2/TEF/02_taxonomy_TEF.sh` | Taxonomic classification against custom FSSC reference |
| `qiime2/TEF/03_export_TEF.sh` | Export feature table and rep-seqs |

To reproduce, activate the QIIME2 environment and run:
```bash
conda activate qiime2-202X.X
bash qiime2/16S/01_import_denoise_16S.sh
