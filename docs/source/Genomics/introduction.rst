Introduction
------------

DNA is the genetic material of all organisms on Earth. When DNA is transmitted from parents to children, it can determine some of the children's characteristics (such as their eye color or hair color). How does the sequence in our DNA (A, T, G, C) actually affect humans or organisms features?

Genes Specify Proteins
----------------------

Within the vast stretches of DNA in our genome are biologically functional stretches of DNA called genes. 

Each gene provides instructions for a functional product, that is, a molecule needed to perform a job in the cell. In many cases, the functional product of a gene is a protein.

This can be hard to conceptualise. Follow the instructions below to load the human genome in a web browser so you can see how genes are interspersed amongst the genome:

View the human genome
#####################

1. Navigate to the website https://igv.org/app/ in a new tab.

2. In the dropdown menus, select 'Genome' > 'GRCh38/hg38'.

3. Select any of the 23 Chromosomes and zoom in to view the biotypes produced by our genome. (If you can't see anything, zoom out and navigate left or right). 

The blue track is known as an annotation track, which marks the start and end coordinates of (known) genes in our DNA. The vast majority of functional products listed in the annotation track are proteins, which is the main job of genes - to produce proteins. Such genes are known as protein-coding genes. 

Genes can code for additional molecules such as tranfer RNAs and ribosomal RNAs which we will come across in the following sections.

Central Dogma
-------------

How does a sequence of DNA nucleotides produce a protein? The figure below shows the transfer of information from DNA > RNA > Protein which is known as the central dogma of biology. 

.. figure:: /_static/images/central-dogma.png
   :figwidth: 700px
   :target: /_static/images/central-dogma.png
   :align: center

|

* In **transcription**, the DNA sequence of a gene is copied to make an RNA molecule. This step is called transcription because it involves rewriting, or transcribing, the DNA sequence in a similar RNA "alphabet." In eukaryotes, the RNA molecule must undergo processing to become a mature messenger RNA (mRNA).

* In **translation**, the sequence of the mRNA is decoded to specify the amino acid sequence of a polypeptide. The name translation reflects that the nucleotide sequence of the mRNA sequence must be translated into the completely different "language" of amino acids.

The process of activating a gene to produce a fucntional protein is known as **gene expression**.

RNA-Sequencing
--------------

A popular experiment in genomics is called RNA-Sequencing where the messenger RNA in a cell is captured and quantified using hight throughput sequencing technologies and comptational algorithms. This allows researchers to quantify the expression of genes - seeing what genes are turned on or off, and how much of each gene is expressed:

.. figure:: /_static/images/tumor_norm.png
   :figwidth: 700px
   :target: /_static/images/tumor_norm.png
   :align: center

|

RNA-Seq is divided into three steps:

1. Library preparation.

2. Sequencing.

3. Data Analysis (that's us!).

Library Preparation
-------------------

Library preparation involves capturing the RNA in cells and preparing the sample for sequencing. It can be divided into 6 steps:

1. Cells are burst open, and RNA is isolated and DNA is removed.

2. We need to cut the RNA into smaller fragments - the sequencing machine can only handle sizes of 200-300 nucleotides.

3. The fragmented RNA is converted to DNA (DNA is more stable than RNA, and we do not lose any information).

4. Sequencing adapters (human designed sequences) are added to the newly synthesized DNA.

5. PCR is used to make millions of copies of the fragmented sequences.

6. The sample is checked - are the lenghts of the amplified fragments ok? (200-300nt) and do we have enough RNA for the experiemnt.

.. figure:: /_static/images/prep.png
   :figwidth: 700px
   :target: /_static/images/prep.png
   :align: center

|

Sequencing
----------

The samples containing the captured RNA are then sent to a laboratory where sequencing is performed. Below is a broad schematic of how sequencing works:

.. figure:: /_static/images/god.png
   :figwidth: 700px
   :target: /_static/images/god.png
   :align: center

|

The output from the sequencing machine is a file containing all of the sequenced reads and additional information regarding how confident the machine was about each base call.

FASTQ Files
-----------

FASTQ files are used to store the output from sequencing machines. See below for the first 4 sequences stored in a FASTQ file:

.. code-block:: console

   @SRR6357073.31043222 31043222/1 kraken:taxid|4932
   GTTTTCGATTTCGAATTATTTGTTTTTTGAGGATTCCGAGCTATAACTTTGGGTTTGGTTGTATTCGTATAGCTGCGAGAATCATTCTTCTCATCACTCGG
   +
   BBBBBFFFFFFFF/FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF<<FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
   @SRR6357073.8331722 8331722/1 kraken:taxid|4932
   ATTGGATTGCATGCCTGAGTCGTAAGTGTCAGGATGCTGAATATCACCTCTTGCAACAAATCTAGCTTTATGAGTACCGTCACGTTTCTTGTTGAAGAGAT
   +
   <BBBBFB/FF<B/<BB//B/</<<FFFFFFB/B</<F<FFFFFBF<BFFFB<F<FBFB<BFBBB</FF/FFFFFF/<FBFFFFF<FFFBFFFFBFBBB/FB
   @SRR6357073.7254397 7254397/1 kraken:taxid|4932
   CTTGCAACAAATCTAGCTTTATGAGTACCGTCACGGTTCTTGTTGAAGATAAACATTGAGTTTATTACTCTTTTAGGGTCTATTTCTGTTCTGTCATAATA
   +
   BBBB<FFFFFFF<FFFFFF<FFFBF/B/FFFFBFF///<FFFFFFBFF<FFFFFFFFB//</FBFFF<BFFFFFFFFFFFFFFFFF//B<FBFFF<<<F//
   @SRR6357073.19215418 19215418/1 kraken:taxid|4932
   ATTTTACAGGGCGATCGCTAAGCTTAATCAACTTCTTCGACAGTTGGACCTTCAGCTTCTGGAGCTGGAGGAGCACCACCTGGGAAACCACCTGGAGCTGC
   +
   BBBBBFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFBFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF

1. Line 1 always begins with a @ indiciating the sequencng run (google SRR6357073 to find out more about the origin of this run), sequencing machine and cluster information.

2. Line 2 is the cDNA sequence that was derived from the original RNA template.

3. Line 3 is always a + - probably used as a delimiter.

4. Line 4 are the base quality scores, i.e how confident the machine was in calling each base. See the figure below for the probability scores (of an incorrectly called base) associated with each ASCII character.

.. figure:: /_static/images/ASCII.png
   :figwidth: 700px
   :target: /_static/images/ASCII.png
   :align: center

|

Genome Alignment
----------------

The next task is to align our reads back to the genome. This is done usig alignment algorithms but is essentially like piecing a puzzle back together! 

.. figure:: /_static/images/kmers.png
   :figwidth: 700px
   :target: /_static/images/kmers.png
   :align: center

|

Viewing Alignments
------------------

Once more, this is difficult to conceptualise so let's get some hands on experience with a file containing aligned reads. 

1. Navigate to https://igv.org/app/

2. In the dropdown menu, select 'Genome', > 'sacCer3'

3. Navigate to the following web page: https://github.com/BarryDigby/Youth-Academy/tree/master/data.

4. Download the files ``RAP1_UNINDUCED_REP1.markdup.sorted.bam`` and ``RAP1_UNINDUCED_REP1.markdup.sorted.bam.bai``.

5. In the dropdown menu, select 'Tracks' > 'Local File'

6. Upload the two files you downloaded, they are probably under downloads. 

Data Analysis
-------------

Examples of data analysis that can be performed on RNA-Seq data will be provided in worksheets throughout the workshop. 