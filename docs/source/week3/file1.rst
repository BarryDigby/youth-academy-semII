RNA-Sequencing
--------------

A popular experiment in genomics is called RNA-Sequencing where the messenger RNA in a cell is captured and quantified using high throughput sequencing technologies in conjunction with computational algorithms. This allows researchers to quantify the expression of genes - seeing what genes are turned on or off, and how much of each gene is expressed:

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
###################

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
##########

The samples containing the captured RNA are then sent to a laboratory where sequencing is performed. Below is a broad schematic of how sequencing works:

.. figure:: /_static/images/god.png
   :figwidth: 700px
   :target: /_static/images/god.png
   :align: center

|

The output from the sequencing machine is a file containing all of the sequenced reads and additional information regarding how confident the machine was about each base call.

FASTQ Files
###########

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
################

The next task is to align our reads back to the genome. This is done usig alignment algorithms but is essentially like piecing a puzzle back together! 

.. figure:: /_static/images/kmers.png
   :figwidth: 700px
   :target: /_static/images/kmers.png
   :align: center

|

Viewing Alignments
##################

We can visualise sequencing reads stored in a BAM file using IGV. Follow the instruction below to download and view a BAM file in IGV:

1. Navigate to `https://igv.org/app/ <https://igv.org/app/>`_

2. In the dropdown menu, select ``Genome``, > ``sacCer3``.

3. Navigate to the following web page: `https://github.com/BarryDigby/Youth-Academy/tree/master/data <https://github.com/BarryDigby/Youth-Academy/tree/master/data>`_.

4. Download the files ``RAP1_UNINDUCED_REP1.markdup.sorted.bam`` and ``RAP1_UNINDUCED_REP1.markdup.sorted.bam.bai``.

5. In IGV, in the dropdown menu, select ``Tracks`` > ``Local File``

6. Add the two ``RAP1`` files you downloaded, they are probably under downloads.

7. Note to teacher: ``SNC1`` gene is an example of intron splicing.
