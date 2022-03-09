Worksheet 
---------

Part I
++++++

Your task is to translate the following DNA sequence into a protein sequence.

DNA to RNA
##########

Convert the sequence below to RNA.

.. note::

    Recall in RNA that ``thyime (T)`` is substituted for ``uracil (U)``. 

.. code-block:: bash

    ATGGCCCTGTGGATGCGCCTCCTGCCCCTGCTG

RNA to Protein
##############

Once you have correctly converted the sequence to RNA, translate it into a protein sequence.

Use the following table as a guide to converting your RNA sequence into a protein sequence.

.. figure:: /_static/images/translation_table.png
   :figwidth: 700px
   :target: /_static/images/translation_table.png
   :align: center

|

.. note::

    Recall that a ``triplet`` of RNA is translated to one amino acid. The first triplet ``AUG`` becomes ``Methionine (M)``.

Part II
+++++++

What organism does this sequence belong to? 

* Copy the DNA sequence and go to `NCBI BLAST <https://blast.ncbi.nlm.nih.gov/Blast.cgi?PROGRAM=blastn&PAGE_TYPE=BlastSearch&LINK_LOC=blasthome>`_.

* Paste the sequence into the box under ``Enter Query Sequence`` and click ``BLAST``.

* When your results load, pay attention to the ``Scientific Name`` column. What species does the sequence belong to?

Part III
++++++++

What gene does the sequence belong to?

* In your ``BLAST`` results, the gene name is given in the ``Description`` column in parentheses ``()``. (Use the top hit for this).

Part IV
+++++++

* Go to the IGV browser (`https://igv.org/app/ <https://igv.org/app/>`_).

* In the search bar, enter the name of the gene our sequence belongs to. 

1. What chromosome is the gene located on? 

2. Is the gene located on the forward or reverse strand? (see below)

|

Recall that DNA is a double stranded molecule, containing both a ``forward strand`` and a ``reverse strand``:

.. code-block:: bash

    5' A G T G C T A G G G T 3' (forward strand)
       | | | | | | | | | | |
    3' T G C T G A T C C C A 5' (reverse strand)

.. note::

    The arrows ``>`` or ``<`` indicate if the gene is on the forward or reverse strand, respectively.

