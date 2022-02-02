Introduction
------------

DNA is the genetic material of all organisms on Earth. When DNA is transmitted from parents to children, it can determine some of the children's characteristics (such as their eye color or hair color). How does the sequence in our DNA (A, T, G, C) actually affect humans or organisms features?

Genes Specify Proteins
######################

Within the vast stretches of DNA in our genome are biologically functional stretches of DNA called genes. 

Each gene provides instructions for a functional product, that is, a molecule needed to perform a job in the cell. In many cases, the functional product of a gene is a protein.

Visualising the human genome
#############################

To help you visualise these functional regions of the human genome, we will use an application called the Integrative Genomics Viewer (IGV) which is a high-performance, easy-to-use, interactive tool for the visual exploration of genomic data. Once we have selected the genome to view, an annotation track is automatically loaded in the browser (you may have to zoom in to view it).

The annotation track marks the start and end coordinates of (known) genes in our DNA. The vast majority of functional products listed in the annotation tracks are proteins, which is the main job of genes – to produce proteins. Such genes are known as protein-coding genes.

1. Navigate to the IGV application using a web browser: `https://igv.org/app/ <https://igv.org/app/>`_.

2. Select the ``Genome`` tab and select ``Human (GRCh38/hg38)`` which is the most current version of the human genome.

3. In the search bar, you can enter the specific coordinates of a gene, or the gene name. Enter ``PTEN`` to view the PTEN gene which is located at ``chr10:87,862,624-87,972,930``.

4. You will notice that there are two blue lines representing PTEN. These are two isoforms of the PTEN gene. This means that the PTEN gene can produce two proteins of similar function – but they will differ slightly in composition.

5. Google the PTEN gene - you will discover it is a very important gene in our genome!

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

Transcription Produces Genetic Messages
#######################################

Transcription begins when the double stranded DNA is unwound and one strand is used as a template for making pre-mRNA. It involves several steps:

#. ``Initiation`` : The enzyme RNA polymerase binds to a specific location in DNA called a promoter region - telling the enzyme “this is where the gene starts”.

#. ``Elongation`` : RNA polymerase reads the nucleotide sequence of the template DNA strand. As it moves along, it inserts and links together complementary RNA nucleotides to form a pre-mRNA molecule.

#. ``Termination`` : The RNA polymerase breaks the link between the template DNA strand and the pre-mRNA molecule, releasing the pre-mRNA. The DNA reforms it’s double helix.

.. figure:: /_static/images/transcription.png
   :figwidth: 700px
   :target: /_static/images/transcription.png
   :align: center

|

Messenger RNA Processing
########################

pre-mRNAs are processed in the nucleus to remove introns (nucleotide sequences present in genes that are not translated into the amino acid sequence of a protein). Introns occur between exons, the nucleotide sequences that remain in the mRNA and are translated into the amino acid sequence of a protein.

As introns are removed, the exons are spliced together to form mature mRNA molecules. I will show you an example of this later with real sequencing reads from yeast, but for now a diagram will suffice:

.. figure:: /_static/images/splicing.png
   :figwidth: 700px
   :target: /_static/images/splicing.png
   :align: center

|

Messenger RNA Translation
#########################

.. note:: 
   Some definitions are required before describing translation:

   #. **Ribosomes**: A complex (made of ribosomal RNA units) that aid in the production of proteins.
   
   #. **transfer RNA (tRNA)**: A small RNA unit that contains a specific binding site for each amino acid. The binding site is determined by the anticodon.
   
   #. **anticodon**: 3 nucleotide molecules that bind in complimentary fashion to the mRNA codons (3 bases).
   Translation, like transcription, has three steps: initiation, elongation, and termination:

#. ``Initiation`` : The tRNA carrying the amino acid methionine (and the complimentary anticodon to AUG) binds to the mRNA. AUG signals the start site of protiens, and is the first amino acid in all proteins (the figure below does not show the start of the polypeptide..)

#. ``Elongation`` : As new tRNA molecules are recruited to the ribosome, the amino acids form a peptide bond, forming a chain of amino acids (i.e a poly peptide chain).

#. ``Termination`` : Termination occurs when the ribosome reaches a stop codon. The mature peptide is relased, and folded into a 3-D structure.

.. figure:: /_static/images/translation_med.jpeg
   :figwidth: 700px
   :target: /_static/images/translation_med.jpeg
   :align: center

|

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

Once more, this is difficult to conceptualise so let's get some hands on experience with a file containing aligned reads. 

1. Navigate to `https://igv.org/app/ <https://igv.org/app/>`_

2. In the dropdown menu, select ``Genome``, > ``sacCer3``.

3. Navigate to the following web page: `https://github.com/BarryDigby/Youth-Academy/tree/master/data <https://github.com/BarryDigby/Youth-Academy/tree/master/data>`_.

4. Download the files ``RAP1_UNINDUCED_REP1.markdup.sorted.bam`` and ``RAP1_UNINDUCED_REP1.markdup.sorted.bam.bai``.

5. In IGV, in the dropdown menu, select ``Tracks`` > ``Local File``

6. Add the two ``RAP1`` files you downloaded, they are probably under downloads.

7. Note to teacher: ``SNC1`` gene is an example of intron splicing.
