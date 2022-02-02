Introduction
============

In this section we will cover plots that can be used to describe the distribution of variables in our dataset and in the case of scatter plots, assess if there is a relationship between two variables. 

For this section we will continue to use the ``Iris`` dataset from the previous section.

Visualising Distributions
=========================

There are two common methods to visualise the distribution of a single variable: using ``boxplots`` or ``histograms`` - both portray the same information.

To make the plot, simply pass the variable (column) of interest to the ``hist()`` or ``boxplot()`` function:

.. code-block:: R

    boxplot(iris$Sepal.Width, horizontal = TRUE)
    plot(density(iris$Sepal.Width))
    hist(iris$Sepal.Width)

I have included a density plot to help you interpret the plots:

.. figure:: /_static/images/distro.png
   :figwidth: 700px
   :target: /_static/images/distro.png
   :align: center

|

.. figure:: /_static/images/boxplots.png
   :figwidth: 700px
   :target: /_static/images/boxplots.png
   :align: center

|

Visualising Relationships
=========================

To assess the relationship between two continuous variables, use a **scatterplot**. Simple pass the two variables to the ``plot()`` function which accepts as inputs vectors to plot ``x`` and ``y`` coordinates.

.. code-block:: r

    plot(iris$Petal.Length, iris$Petal.Width)

.. figure:: /_static/images/scat_1.png
   :figwidth: 700px
   :target: /_static/images/scat_1.png
   :align: center

|

We can see that there is a positive relationship between the two variables - that is to say, as ``Petal.Width`` increases, so does ``Petal.Length``. They have a positive correlation.

Visualising Nested Groups
=========================

In the previous example using boxplots, we viewed the distribution of one variable ``Sepal.Width`` **for every sample** in the Iris dataset. What if we wanted to compare ``Sepal.Width`` across the 3 flower species? 

We will use the library ``ggpubr`` to do this - the code is relatively intuitive. By passing the column ``Species`` to the x-axis, the plot will automatically divide our data according to the three flower species:

.. code-block:: R

    ggboxplot(iris, x = "Species", y = "Sepal.Width", bxp.errorbar = TRUE)

.. figure:: /_static/images/boxplot_species.png
   :figwidth: 700px
   :target: /_static/images/boxplot_species.png
   :align: center

|

For histograms and scatter plots, use the parameter ``facet.by`` to create faceted plots - one plot for each grouping variable in a panel.

.. code-block:: r

    gghistogram(iris, x = "Sepal.Width", y = "..density..", facet.by = "Species")

.. figure:: /_static/images/hist_facet.png
   :figwidth: 700px
   :target: /_static/images/hist_facet.png
   :align: center

|

.. code-block:: R

    ggscatter(iris, x = "Petal.Length", y = "Petal.Width", facet.by = "Species")

.. figure:: /_static/images/scat_facet.png
   :figwidth: 700px
   :target: /_static/images/scat_facet.png
   :align: center

|

Enhancing Plots
===============

Adding colors to plots make groups instantly stand out. To do this in ``ggpubr``, you will need to specify the ``fill`` parameter with the grouping variable. This will fill in your histogram bars/boxplots with a unique color according to the number of unique groups in the variable (for the iris dataset this is 'Setosa', 'Versicolor' and 'Virginica').

.. code-block:: R

    gghistogram(iris, x = "Sepal.Width", y = "..density..", add_density = T, fill = "Species", add = "median")

.. figure:: /_static/images/histo_groups.png
   :figwidth: 700px
   :target: /_static/images/histo_groups.png
   :align: center

|

.. code-block:: R

    ggboxplot(iris, x = "Species", y = "Sepal.Width", fill = "Species", bxp.errorbar = T)

.. figure:: /_static/images/boxplot_group.png
   :figwidth: 700px
   :target: /_static/images/boxplot_group.png
   :align: center

|

.. note::

    For scatterplots, use ``color`` instead of ``fill``. 

.. code-block:: R

    ggscatter(iris, x = "Petal.Length", y = "Petal.Width", color = "Species")

.. figure:: /_static/images/scat_col.png
   :figwidth: 700px
   :target: /_static/images/scat_col.png
   :align: center

|