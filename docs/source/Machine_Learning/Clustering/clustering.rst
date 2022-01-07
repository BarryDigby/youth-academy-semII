Introduction
============

Clustering is a technique used to group samples together based on the similarity of their variables. This is useful to identify underlying patterns in our dataset and is an example of **unsupervised machine learning**.

Firstly we will use a toy dataset so you can identify patterns by eye before applying the principles to a larger dataset where patterns are not as obvious. 

Toy Dataset
-----------

Please run the block of code below. This dataset contains the expression levels of 3 genes for 4 patients:

.. code-block:: R

    df=data.frame(IRX4=c(11,13,2,1),
                  OCT4=c(10,13,4,3 ),
                  PAX6=c(1 ,3 ,10,9),
                  row.names=c("patient1",
                              "patient2",
                              "patient3",
                              "patient4"))

Visualise Toy Dataset
=====================

We will begin by making a barplot of the gene epxression data. 

Firstly we need to reformat the data (do not worry about this) but you should recognise the ``facet.by`` parameter in ``ggpubr`` to produce plots for each patient:

.. code-block:: R

    df2=tidyr::gather(cbind(patient=rownames(df),df),key="gene",value="expression",IRX4,PAX6,OCT4)

    ggbarplot(df2, x="gene", y="expression", fill="patient", facet.by = "patient")

.. figure:: /_static/images/toy_dat_barplot.png
   :figwidth: 700px
   :target: /_static/images/toy_dat_barplot.png
   :align: center

|

ScatterPlotMatrix
=================

Recall we used scatterplots to assess relationships between two variables. Scatter plots that have been coloured by groupings can also tell us which variables are good at delineating samples. 

Manually plotting each combination of variables in a dataframe is tedious, we can use a ``ScatterPlotMatrix`` to do this automatically:

.. code-block:: R

    # Telling R that each patient ID is a unique name
    id <- as.factor(rownames(df))

    # Base R plotting
    pairs(df, col=id, lower.panel = NULL, cex = 2, pch = 20)
    par(xpd = TRUE)
    legend(x = 0.05, y = 0.4, cex = 1, legend = id, fill = id)

.. figure:: /_static/images/splom.png
   :figwidth: 700px
   :target: /_static/images/splom.png
   :align: center

|

A guide on how to interpret the plot has been provided below: 

.. figure:: /_static/images/splom_exp.png
   :figwidth: 700px
   :target: /_static/images/splom_exp.png
   :align: center

|

Distance Metrics
================

The human eye is extremely efficient at recognising patterns in plots, which we have demonstrated using barplots and scatter plots. But how does a computer 'see' these patterns? It does not have eyes so it must use a different method to define how similar (or dissimilar) samples are. 

We will use the ``Manhattan Distance`` to compute sample similarity mathematically.

.. figure:: /_static/images/manhat_form.png
   :figwidth: 700px
   :target: /_static/images/manhat_form.png
   :align: center

|

Using patient 1 and patient 2 from our toy dataset, let's work the solution by hand: 

.. code-block:: console

   Patient 1 vector (x): 11, 10, 1
   Patient 2 vector (y): 13, 13, 3

   Formula: sum|((X1 - Y1)) , (X2 - Y2), (X3 - Y2))|

   Fill in: sum|((11 - 13), (10 - 13), (1 - 3))|

   Solve: sum|-2, -3, -2 |

   Solve: sum(2, 3, 2)

   Answer: Manhattan Distance( Patient 1, Patient 2) = 7

Dist() function
===============

Solving the distance metrics by hand is a useful exercise to understand how distance metrics are generated, but for obvious reasons, cumbersome. 

To automate this, use the ``dist()`` function in R. Pass the dataframe (which must only contain numerics) and select the distance metric you want to use (manhattan):

.. code-block:: R

   dist(df, method="manhattan", diag=TRUE, upper=TRUE)

.. code-block:: console

   ##          patient1 patient2 patient3 patient4
   ## patient1        0        7       24       25
   ## patient2        7        0       27       28
   ## patient3       24       27        0        3
   ## patient4       25       28        3        0

Sample Heatmaps
===============

The table of results generated from the ``dist()`` function are tedious to interpret - instead, we can use data visualisations to quickly convey this information.

.. code-block:: R

   # Load library for heatmaps
   library(pheatmap)

   # use Manhattan distance (store in matrix)
   d <- as.matrix(dist(df, method="manhattan"))

   # add patient ID to rows & columns for the heatmap
   rownames(d) <- rownames(df)
   colnames(d) <- rownames(df)

   pheatmap(d, cluster_rows = F, cluster_cols = F,
            show_rownames = T, show_colnames = T, display_numbers = TRUE)

.. figure:: /_static/images/heatmap_manhat.png
   :figwidth: 700px
   :target: /_static/images/heatmap_manhat.png
   :align: center

|

We can see the results for each sample comparison and once again, visually, we can see clusters beginning to form. The next step is to perform clustering via computational methods.

Hierarchical Clustering
=======================

The hierarchical clustering algorithm works by:

1. Calculating the distance between all samples.

2. Join the two 'closest' (smallest distance metric) samples together to form the first cluster.

3. Re-calculate distances between all samples (and the new cluster) and repeat the process until every sample has been added to a cluster.

.. figure:: /_static/images/hier.gif
   :figwidth: 700px
   :target: /_static/images/hier.gif
   :align: center

|

How can we visualise this GIF in a plot? By using a ``dendogram`` which looks like a tree with branches. Each branch represents a cluster, until you work all the way down to the bottom in which case each branch represents a sample:

.. figure:: /_static/images/hierarchical.gif
   :figwidth: 700px
   :target: /_static/images/hierarchical.gif
   :align: center

|

We will add a dendogram to our toy dataset heatmap to define clusters:

.. code-block:: R

   # Plot the distance matrix using a heatmap
   pheatmap(d, cluster_rows = T, cluster_cols = T,
            show_rownames = T, show_colnames = T,
            treeheight_row = 100, treeheight_col = 100)

   
.. figure:: /_static/images/heatmap_hier.png
   :figwidth: 700px
   :target: /_static/images/heatmap_hier.png
   :align: center

|

Feature heatmaps
================

Sample heatmaps are used to assess sample heterogeneity. Feature heatmaps are representations of the values present in each of the variables in the dataset for each sample. 

Using feature heatmaps in conjunction with clustering, we can identify the underlying variables that differentiate samples.

You do not need to compute any distance metric here, simply pass the numeric dataframe to the ``pheatmap`` function:

.. code-block:: R

   # rotate the dataframe to make plot easier to interpret. 
   df_t <- as.data.frame(t(df))

   pheatmap(df_t, cluster_cols = TRUE, 
            cluster_rows = TRUE, 
            treeheight_row = 100, 
            treeheight_col = 100,
            display_numbers = TRUE)

.. figure:: /_static/images/feature_hm.png
   :figwidth: 700px
   :target: /_static/images/feature_hm.png
   :align: center

|