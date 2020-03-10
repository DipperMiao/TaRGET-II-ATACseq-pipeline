# TaRGET-II-ATACseq-pipeline

The TaRGET II ATAC-seq pipeline is designed for standardized data processing of mouse ATAC-seq samples. It incorporates automatic quality control, generates user friendly files for computational analysis and outputs genome browser tracks for data visualization. To ensure consistent and reproducible data processing, the entire workflow, associated software and libraries are built into a singularity image, which can be run on computational clusters with job submission as well as on stand-alone machines. Pipeline installation requires minimal user input. All the software and genome references used for TaRGET II ATAC-seq data processing are included in the pipeline image. The pipeline supports both single- and paired-end data, it accepts FASTQ files, performs alignments, peak calling and signal track generation. The major outputs produced by the pipeline are:
   1)	JSON file with quality control measurement of user supplied dataset. Quality control measurement of ENCODE dataset is  provided for references. 
   2)	Log file with processing status of each step 
   3)	Processed files after alignment (.bam) and peak calling (.narrowPeak) 
   4)	Bigwig file for visualization purpose


# Usage:

**2-step guideline for pipeline usage:**

step.1 Download the singularity image of the pipeline:
```
# download image from local server:
wget http://brc.wustl.edu/SPACE/shaopengliu/Singularity_image/rna-seq/rna-seq_mm10_v4.simg  
```
step.2 Process ATAC-seq data with the image: 
Please Run at same directory with your data OR the soft link of your data
