# SARS-CoV-2-Genomic-Surveillance-Pipeline
End-to-End Genomic Surveillance of SARS-CoV-2 From Raw NGS Reads to Metagenomic Validation and 3D Structural Modeling
# End-to-End Genomic Surveillance of SARS-CoV-2: From Raw NGS Reads to Metagenomic Validation and 3D Structural Modeling

![Status](https://img.shields.io/badge/Status-Completed-success)
![Language](https://img.shields.io/badge/Language-Python%20%7C%20Bash-blue)
![Platform](https://img.shields.io/badge/Platform-Google%20Colab-orange)
![Bioinformatics](https://img.shields.io/badge/Bioinformatics-Viral%20Genomics-green)

## 🧬 Project Overview

This project implements a comprehensive bioinformatics pipeline for the genomic surveillance of SARS-CoV-2. It processes raw Next-Generation Sequencing (NGS) data through 11 distinct phases, ranging from quality control and alignment to advanced downstream analyses like functional annotation, phylogenetics, metagenomics, and 3D structural modeling.

The workflow demonstrates a "From Reads to Ribbons" approach, characterizing a specific viral sample from its DNA sequence all the way to the atomic structure of its mutated proteins.

**Sample Analyzed:** [SRR11772244](https://trace.ncbi.nlm.nih.gov/Traces/sra/?run=SRR11772244) (Illumina Paired-End)

## 🚀 The Pipeline Workflow

The analysis is structured into **11 integrated phases**:

| Phase | Task | Tools Used | Description |
| :--- | :--- | :--- | :--- |
| **1** | **QC & Trimming** | `FastQC`, `Trimmomatic`, `Cutadapt` | Removal of adapters and low-quality bases (Phred < 30). |
| **2** | **Alignment** | `BWA-MEM`, `Samtools` | Mapping reads to the Wuhan-Hu-1 Reference (NC_045512.2). |
| **3** | **Variant Calling** | `Bcftools` | Identification of SNPs and Indels (mpileup & call). |
| **4** | **Consensus** | `Bcftools` | Generation of the specific patient viral genome (FASTA). |
| **5** | **Lineage Assignment** | `Nextclade` (CLI) | Classification of the strain (Clade/Pango Lineage). |
| **6** | **Functional Annotation**| `SnpEff` | Prediction of amino acid changes (Missense/Synonymous). |
| **7** | **Phylogenetics** | `MAFFT`, `FastTree`, `Biopython` | Construction of maximum-likelihood evolutionary trees. |
| **8** | **Structural Analysis** | `py3Dmol` | 3D Visualization of the Spike protein and D614G mutation. |
| **9** | **Reporting** | `MultiQC` | Aggregation of all QC logs into a single HTML report. |
| **10** | **Metagenomics** | `Kraken2` | Taxonomic classification to verify sample purity. |
| **11** | **Visualization** | `Plotly` | Interactive dashboard of data attrition and workflow. |

## 📊 Key Findings

* **Data Quality:** 98.24% of raw reads survived quality control.
* **Alignment:** Achieved **99.97% genome coverage** with an average depth of **2,275x**.
* **Sample Purity:** Kraken2 metagenomic analysis confirmed the sample is **99.69% pure SARS-CoV-2**, with no evidence of co-infection.
* **Lineage Identified:** **B.1 (Clade 20C)**.
* **Critical Mutation:** Identified the **S:D614G** mutation in the Spike protein, known to increase viral transmissibility.
* **Protein Impact:** Structural modeling confirmed D614G is located on the protein surface, affecting flexibility.

## 🛠️ Tools & Dependencies

The notebook automatically installs the following tools via `apt-get` and `pip` within the Colab environment:

* **SRA-Toolkit:** Data retrieval.
* **Trimmomatic / Cutadapt:** Read trimming.
* **BWA / Samtools:** Alignment and BAM processing.
* **Bcftools:** Variant calling and consensus generation.
* **SnpEff:** Variant annotation (Manual database build included).
* **Nextclade:** Lineage assignment.
* **Kraken2:** Metagenomic classification (Viral-only database).
* **MAFFT / FastTree:** Phylogenetics.
* **Py3Dmol:** Molecular visualization.
* **MultiQC:** Automated reporting.
* **Plotly / Kaleido:** Data visualization and dashboard export.

## 📂 Output Files generated

Upon successful execution, the pipeline generates a `Project_Results.zip` containing:

1.  `Genome.fasta`: The consensus sequence of the virus.
2.  `Mutations.vcf`: Annotated list of genetic variants.
3.  `Phylogeny.tree`: Newick tree file placing the sample in history.
4.  `Project_Dashboard.html`: Interactive summary dashboard.
5.  `Kraken_Report.txt`: Metagenomic purity report.
6.  `MultiQC_Report.html`: Technical quality control report.

## 💻 How to Run

1.  Open the notebook `End_to_End_Genomic_Surveillance_of_SARS_CoV_2.ipynb` in **Google Colab**.
2.  Ensure the runtime is connected (Standard CPU/RAM is sufficient; 8GB RAM safe-mode is enabled for Metagenomics).
3.  Run all cells sequentially.
4.  The final step will automatically zip and download the results to your local machine or Google Drive.

## 📜 License

This project is open-source and available for educational and research purposes.
