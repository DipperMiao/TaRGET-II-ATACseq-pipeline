# TaRGET-II-ATACseq-pipeline

The TaRGET II ATAC-seq pipeline is designed for standardized data processing of mouse ATAC-seq samples. It incorporates automatic quality control, generates user friendly files for computational analysis and outputs genome browser tracks for data visualization. To ensure consistent and reproducible data processing, the entire workflow, associated software and libraries are built into a singularity image, which can be run on computational clusters with job submission as well as on stand-alone machines. Pipeline installation requires minimal user input. All the software and genome references used for TaRGET II ATAC-seq data processing are included in the pipeline image. The pipeline supports both single- and paired-end data, it accepts FASTQ files, performs alignments, peak calling and signal track generation. 


# Usage:

**2-step guideline for pipeline usage:**

**step.1** Download the singularity image [here](http://brc.wustl.edu/SPACE/shaopengliu/Singularity_image/rna-seq/rna-seq_mm10_v4.simg):
```
# download image from local server:
wget http://brc.wustl.edu/SPACE/shaopengliu/Singularity_image/rna-seq/rna-seq_mm10_v4.simg  
```
**step.2** Process ATAC-seq data with the image: 

Please Run at same directory with your data OR the soft link of your data
```
singularity run -B ./:/process <path-to-image> -r <SE/PE> -g <mm10 > -o <read_file1> -p <read_file2>
```
**soft link introduction:** For soft link of data, need to add one bind option for singularity, which is ```-B <full-path-of-original-position>:<full-path-of-original-position>```. 
For example:
soft link the data from /scratch to run on folder /home/example. **Please make sure you use the absolute path.**
```
ln -s /scrach/mydata.fastq.gz /home/example;
cd /home/example
singularity run -B ./:/process -B /scratch:/scratch /home/image/ATAC_IAP_v1.00.simg -r PE -g mm10 -o read1.fastq.gz -p read2.fastq.gz
```
**parameters:**

`-h`: help information.

`-r`: SE for single-end, PE for paired-end.

`-g`: genome reference, one simg is designed for ONLY one species due to the file size. For now the supported genoms are mm10.

`-o`: reads file 1 or the SE reads file, must be ended by .fastq or .fastq.gz or .sra (for both SE and PE). 

`-p`: reads file 2 if input PE data, must be ended by .fastq or .fastq.gz.

`-c`: (optional) specify read length minimum cutoff for methylQA filtering, default 38.

`-t`: (optional) specify number of threads to use, default 24.

`-i`: (optional) insertion free region finding parameters used by Wellington Algorithm (Jason Piper etc. 2013), see documentation for more details.

# Output files

The major outputs produced by the pipeline are:
   1)	JSON file with quality control measurement of user supplied dataset. Quality control measurement of ENCODE dataset is  provided for references. 
   2)	Log file with processing status of each step 
   3)	Processed files after alignment (.bam) and peak calling (.narrowPeak) 
   4)	Bigwig file for visualization purpose

# Quailty Control Parameters




