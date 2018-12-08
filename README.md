# Aligning-ONS-Data-for-Alanine-Mutants-of-PKS
Analyzing Oxford Nanopore DNA Sequencing Data to locate Alanine Substitution Mutants of a Polyketide Synthase

For decades, baker’s yeast has been known to be a good host and model organism for
expressing biosynthetic genes from other organisms. Furthermore, fungi have long been
producers of secondary metabolites, an important resource for the design and development of
therapeutic new drugs like penicillin or the statin drugs. However, the lengthy process of
harvesting compounds from fungi and the inability of some to grow in a lab environment
bottlenecks the discovery of new compounds that could potentially be of medicinal value. By
focusing on the class of polyketide synthase (PKS) enzymes from fungi, this work aimed to
better understand the formation of two natural products, disorbly cysteine (DSC) and disorbly
homocysteine (DSH), as both of these contained amino acids as part of their structure, something
very unusual for compounds produced by PKS enzymes. Genome-editing methods were used to
introduce mutations in a PKS that resulted in alanine amino acid substitutions. Each mutant will
ultimately be analyzed for compound production capacity. Using Oxford Nanopore Sequencing
and overcoming the barriers of high error-prone DNA produced by this technology, this project
developed a novel pipeline in order to identify the plate, position, and unknown mutant of each
fungal gene that was genetically engineered by insertion into the yeast genome, which
accelerated the process of harvesting compounds from fungi. The results and conclusions of this
experiment could lead to a better understanding of the class of PKS enzymes that could uncover
hidden genomic pathways towards novel chemical compounds. This pipeline can also be applied
to study any other proteins or enzymes rapidly and can be widely beneficial in the
pharmaceutical market as it increases the candidates for drug discovery by allowing scientists to
genetically engineer potential medicinal drugs more rapidly than ever before.


# How-to run Alignment
1. Download and install bowtie2 onto Command Line (Unix)
2. Convert fasta txt file into FASTA File through http://sequenceconversion.bugaco.com

### Create Bowtie2 index
1. mkdir bowtie2index_foldername
2. mv fastafile.fasta bowtie2index_foldername
3. bowtie2-build bowtie2index_foldername/fastafile.fasta bowtie2index_foldername/bowtie2index_foldername

### Alignming through Bowtie2 
1. mkdir output_folder
2. bowtie2 --score-min L,-12,-12 --all -x bowtie2index_foldername/bowtie2index_foldername fastqfile_withBarcodes.fastq > output_folder/output_folder.sam

### Convert results sam file to bam file, and then bed file
1. samtools view -Sb output_folder/output_folder.sam > output_folder/output_folder.bam
2. bedtools bamtobed -cigar -i output_folder.bam > output_folder.bed

##### Authors: Reet Mishra, Dr. Bob St. Onge, Davis Lab, Stanford Genome Technology Center
