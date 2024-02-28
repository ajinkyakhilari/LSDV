Reference-Guided Assembly Pipeline for LSDV virus
This pipeline is designed for processing Oxford Nanopore Technologies sequencing data through reference-guided assembly. It includes steps for quality control, alignment, primer clipping, consensus sequence generation, variant calling, and coverage analysis.

Prerequisites
Before running this pipeline, ensure you have the following software installed on your system:

fastp: For quality control and read trimming.
minimap2: For aligning reads to the reference genome.
samtools: For manipulating alignments (sorting, indexing).
bedtools: For coverage analysis and manipulation of genomic intervals.
bamclipper: For clipping primer sequences from aligned reads.
medaka: For consensus sequence and variant calling.
longshot: For variant calling using phased haplotypes.
bcftools: For consensus sequence generation and VCF file manipulation.
multiqc: For aggregating results into a single report.
Installation instructions for each software package can be found on their respective websites or GitHub repositories.

Installation
This pipeline is provided as a Bash script, requiring no special installation. Simply download the script to your local machine or server where all the required software is installed. Ensure the script has execute permissions:

bash
Copy code
chmod +x virAssem.sh
Usage
To run the pipeline, use the following command:

bash
Copy code
./virAssem.sh [options]
Options
-i: Input directory containing barcode folders with FASTQ files.
-o: Output directory for processed data.
-r: Reference genome file path.
-p: BEDPE file path with primer positions.
-t: Number of threads (default: 4).
-m: Maximum read length (default: 5000).
-l: Minimum read length (default: 150).
-h: Display help and exit.
Example
bash
Copy code
./virAssem.sh -i /path/to/input -o /path/to/output -r /path/to/reference.fasta -p /path/to/primers.bedpe -t 8 -m 5000 -l 150
This command processes sequencing data located in /path/to/input, using /path/to/reference.fasta as the reference genome and /path/to/primers.bedpe for primer positions, with 8 threads, and filters reads to those between 150 and 5000 bases long. The processed data and reports will be saved in /path/to/output.

Output
The pipeline will generate the following outputs for each barcode processed:

Quality controlled and trimmed FASTQ files.
BAM files of aligned reads, both raw and primer-clipped.
BED and BEDGRAPH files for coverage analysis.
VCF files for variant calls.
Consensus sequences in FASTA format, including sequences with low-coverage regions masked.
MultiQC report aggregating quality control results and statistics in the specified output directory.
Troubleshooting
Ensure all the required software is correctly installed and accessible from your PATH. If you encounter errors related to specific tools, consult the documentation or support forums for those tools for guidance.

Support
For questions or issues related to the pipeline, please open an issue on the GitHub repository where this pipeline is hosted.
