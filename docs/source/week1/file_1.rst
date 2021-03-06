Introduction
------------

DNA is the genetic material of all organisms on Earth. When DNA is transmitted from parents to children, it can determine some of the children's characteristics (such as their eye color or hair color). How does the sequence in our DNA (A, T, G, C) actually affect humans or organisms features?

.. figure:: /_static/images/chromosomes_and_DNA.png
   :figwidth: 700px
   :target: /_static/images/chromosomes_and_DNA.png
   :align: center

|

Genes Specify Proteins
######################

Within the vast stretches of DNA in our genome are biologically functional stretches of DNA called genes. 

Each gene provides instructions for a functional product, that is, a molecule needed to perform a job in the cell. In many cases, the functional product of a gene is a protein.

Visualising the human genome
#############################

To help you visualise these functional regions of the human genome, we will use an application called the Integrative Genomics Viewer (IGV) which is a high-performance, easy-to-use, interactive tool for the visual exploration of genomic data. Once we have selected the genome to view, an annotation track is automatically loaded in the browser (you may have to zoom in to view it).

The annotation track marks the start and end coordinates of (known) genes in our DNA. The vast majority of functional products listed in the annotation tracks are proteins, which is the main job of genes: to produce proteins. Such genes are known as protein-coding genes.

1. Navigate to the IGV application using a web browser: `https://igv.org/app/ <https://igv.org/app/>`_.

2. Select the ``Genome`` tab and select ``Human (GRCh38/hg38)`` which is the most current version of the human genome.

3. In the search bar, you can enter the specific coordinates of a gene, or the gene name. Enter ``PTEN`` to view the PTEN gene which is located at ``chr10:87,862,624-87,972,930``.

4. You will notice that there are two blue lines representing PTEN. These are two isoforms of the PTEN gene. This means that the PTEN gene can produce two proteins of similar function ??? but they will differ slightly in composition.

5. Google the PTEN gene - you will discover it is a very important gene in our genome!


Central Dogma
#############

How does a sequence of DNA nucleotides produce a protein? The figure below shows the transfer of information from DNA > RNA > Protein which is known as the ``central dogma`` of biology. 

.. figure:: /_static/images/kahn_dogma.png
   :figwidth: 700px
   :target: /_static/images/kahn_dogma.png
   :align: center

|

* In **transcription**, the DNA sequence of a gene is copied to make an RNA molecule. This step is called transcription because it involves rewriting, or transcribing, the DNA sequence in a similar RNA "alphabet." In eukaryotes, the RNA molecule must undergo processing to become a mature messenger RNA (mRNA).

* In **translation**, the sequence of the mRNA is decoded to specify the amino acid sequence of a polypeptide. The name translation reflects that the nucleotide sequence of the mRNA sequence must be translated into the completely different "language" of amino acids.

RNA polymerase
##############

The main player in transcription is an enzyme called ``RNA polymerase``, which uses a single stranded DNA template to synthesize a complementary strand of RNA. 

RNA polymerase builds the new RNA strand in the 5' to 3' direction.

.. figure:: /_static/images/kahn_rnapol.png
   :figwidth: 700px
   :target: /_static/images/kahn_rnapol.png
   :align: center

|

Transcription Produces Genetic Messages
#######################################

Transcription begins when the double stranded DNA is unwound and one strand is used as a template for making pre-mRNA. It involves several steps:

1. ``Initiation`` : The enzyme RNA polymerase binds to a specific location in DNA called a promoter region - telling the enzyme ???this is where the gene starts???.

.. figure:: /_static/images/kahn_initiation.png
   :figwidth: 700px
   :target: /_static/images/kahn_initiation.png
   :align: center

|

2. ``Elongation`` : RNA polymerase reads the nucleotide sequence of the template DNA strand. As it moves along, it inserts and links together complementary RNA nucleotides to form a pre-mRNA molecule.

.. note::

    The new RNA transcript carries the same information as the ``coding strand`` of the DNA, resulting in an identical copy with ``thymine (T)`` substituted for ``uracil (U)``.

.. figure:: /_static/images/kahn_elongation.png
   :figwidth: 700px
   :target: /_static/images/kahn_elongation.png
   :align: center

|

3. ``Termination`` : The RNA polymerase breaks the link between the template DNA strand and the pre-mRNA molecule, releasing the pre-mRNA. The DNA reforms it's double helix.

.. figure:: /_static/images/kahn_termination.png
   :figwidth: 700px
   :target: /_static/images/kahn_termination.png
   :align: center

|

Messenger RNA Processing
########################

pre-mRNAs are processed in the nucleus to remove introns (nucleotide sequences present in genes that are not translated into the amino acid sequence of a protein). Introns occur between exons, the nucleotide sequences that remain in the mRNA and are translated into the amino acid sequence of a protein.

As introns are removed, the exons are spliced together to form mature mRNA molecules.

.. figure:: /_static/images/kahn_splicing.png
   :figwidth: 700px
   :target: /_static/images/kahn_splicing.png
   :align: center

|

.. admonition:: \ \

   Go back to ``IGV`` and look at the ``DHDH`` gene. Notice that this gene produces two transcripts. How many exons are in each transcript variant of the ``DHDH`` gene?

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

.. figure:: /_static/images/translation_table.png
   :figwidth: 700px
   :target: /_static/images/translation_table.png
   :align: center

|