# Cirrhotic-Liver-Dataset-Analysis
# ------------------------------------------------------------------------
# 1. Install CRAN Packages (Core Processing, Tidyverse, ML Framework)
# ------------------------------------------------------------------------
cran_packages <- c(
  "tidyverse",   # Data manipulation and visualization (ggplot2, dplyr, etc.)
  "tidymodels",  # Comprehensive machine learning framework
  "rsample",     # Data splitting and resampling infrastructure
  "recipes",     # Data preprocessing tools for modeling
  "parsnip",     # A unified interface to various machine learning models
  "workflows",   # Bundle preprocessing and modeling steps together
  "yardstick",   # Model performance metrics
  "harmony",     # Fast and scalable batch effect correction
  "patchwork"    # Complex plot layouts and multi-panel alignment
)

new_cran <- cran_packages[!(cran_packages %in% installed.packages()[,"Package"])]
if(length(new_cran)) install.packages(new_cran)

# ------------------------------------------------------------------------
# 2. Install Bioconductor Packages (Functional Annotation & Reference DBs)
# ------------------------------------------------------------------------
if (!requireNamespace("BiocManager", quietly = TRUE)) install.packages("BiocManager")

bioc_packages <- c(
  "clusterProfiler", # Statistical analysis and visualization of functional profiles
  "org.Hs.eg.db"     # Genome-wide annotation database for Human
)

new_bioc <- bioc_packages[!(bioc_packages %in% installed.packages()[,"Package"])]
if(length(new_bioc)) BiocManager::install(new_bioc)

# ------------------------------------------------------------------------
# 3. Install Developer/GitHub-Specific Packages
# ------------------------------------------------------------------------
if (!requireNamespace("remotes", quietly = TRUE)) install.packages("remotes")

# scCustomize: Optimized plotting utilities built over Seurat
if (!requireNamespace("scCustomize", quietly = TRUE)) remotes::install_github("samuel-marsh/scCustomize")

# DoubletFinder: Computational doublet identification and removal
if (!requireNamespace("DoubletFinder", quietly = TRUE)) remotes::install_github("chris-mcginnis-ucsf/DoubletFinder")
