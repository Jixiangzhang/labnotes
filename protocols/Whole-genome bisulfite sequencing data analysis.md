# Whole-genome bisulfite sequencing data analysis
## Table of contents

<!-- vscode-markdown-toc -->
* 1. [Quality control of bisulfite sequencing reads](#Qualitycontrolofbisulfitesequencingreads)
* 2. [Preprocessing of raw reads](#Preprocessingofrawreads)
* 3. [Mapping reads onto a reference genome](#Mappingreadsontoareferencegenome)
* 4. [Quality control of mapped reads](#Qualitycontrolofmappedreads)
* 5. [Methylation ratio analysis](#Methylationratioanalysis)
* 6. [Use binomial distribution identified the methylated cytosines](#Usebinomialdistributionidentifiedthemethylatedcytosines)
* 7. [quality-control-of-bisulfite-sequencing-reads](#quality-control-of-bisulfite-sequencing-reads)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->

##  1. <a name='Qualitycontrolofbisulfitesequencingreads'></a>Quality control of bisulfite sequencing reads
```
fastqc -t 16 TZX-MET-S1.R1.clean.fastq.gz
```
##  2. <a name='Preprocessingofrawreads'></a>Preprocessing of raw reads
```
java -classpath trimmomatic-0.33.jar org.usadellab.trimmomatic.TrimmomaticPE -phred33 -threads 16 -trimlog r.log TZX-MET-S1.R1.clean.fastq.gz TZX-MET-S1.R2.clean.fastq.gz trimmed_TZX-MET-S1.R1.clean.fastq.gz unpaired_TZX-MET-S1.R1.clean.fast2q.gz trimmed_TZX-MET-S1.R2.clean.fastq.gz unpaired_TZX-MET-S1.R2.clean.fastq.gz LEADING:30 HEADCROP:6 TRAILING:30 ILLUMINACLIP:adapter.fa:2:40:15 SLIDINGWINDOW:4:15 MINLEN:100
```
##  3. <a name='Mappingreadsontoareferencegenome'></a>Mapping reads onto a reference genome
```
bismark_genome_preparation --path_to_bowtie bowtie2-2.2.5 --verbose --bowtie2 Gmax_275/
bismark --path_to_bowtie bowtie2-2.2.5/ --bowtie2 --samtools_path samtools-1.2/ Gmax_275/ -1 trimmed_TZX-MET-S1.R1.clean.fastq.gz -2 trimmed_TZX-MET-S1.R2.clean.fastq.gz -o work_results/
```
##  4. <a name='Qualitycontrolofmappedreads'></a>Quality control of mapped reads
##  5. <a name='Methylationratioanalysis'></a>Methylation ratio analysis
## 
```

```
##  6. <a name='Usebinomialdistributionidentifiedthemethylatedcytosines'></a>Use binomial distribution identified the methylated cytosines

##  7. <a name='quality-control-of-bisulfite-sequencing-reads'></a>quality-control-of-bisulfite-sequencing-reads
