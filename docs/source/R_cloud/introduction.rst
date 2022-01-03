Introduction
============

During the workshop, we will be using the statistical computing software called ``R`` to perform calculations and produce data visualisations.

Fortunately, we have a cloud-based version of R available to us at the following website: `R Studio Cloud <https://rstudio-cloud.com/>`_.

Please follow the steps below to:

1. Create an account

2. Create a project

3. Install some packages

Create Account
==============

Navigate to the `R Studio Cloud <https://rstudio-cloud.com/>`_ website and click on the ``GET STARTED FOR FREE`` button.

.. figure:: /_static/images/r_cloud_1.png
   :figwidth: 700px
   :target: /_static/images/r_cloud_1.png
   :align: center

|

Select a free acount. This will provide us with enough resources for the workshop (1 GB RAM, 1 CPU and 25 hours per month). In reality this is a tiny resource allocation - many computational operations in genomics require exponentially more resources which are performed on high performance compute (HPC) clusters or more recently, on the cloud. 

.. figure:: /_static/images/r_cloud_2.png
   :figwidth: 700px
   :target: /_static/images/r_cloud_2.png
   :align: center

|

Enter a valid email address and fill out the rest of the information (password, name). ``R Studio Cloud`` will send you an email with a link to verify your email address. Click on the link to verify your email address - you should now be able to log into ``R Studio Cloud``.

Select ``R Studio Cloud``from the options listed below:

.. figure:: /_static/images/r_cloud_3.png
   :figwidth: 700px
   :target: /_static/images/r_cloud_3.png
   :align: center

Create Project
==============

Once your account has been created, you need to create a project for the workshop. This is to let ``R Studio Cloud`` know what type of environment you want to work in, and allows them to track your resource usage. 

Select New Project > New R Studio Project.

.. figure:: /_static/images/r_cloud_4.png
   :figwidth: 700px
   :target: /_static/images/r_cloud_4.png
   :align: center

R Markdown
==========

During the workshop we want to be able to create ``PDF`` or ``HTML`` documents containing our code and code outputs. To do this, we will be using the ``R Markdown`` document type.

In your project workspace, select File > New File > R Markdown...

You will be prompted to install packages, select yes. 

.. figure:: /_static/images/r_cloud_5.png
   :figwidth: 700px
   :target: /_static/images/r_cloud_5.png
   :align: center

| 

You can now make ``R Markdown`` documents, which we will return to later in the workshop. 

Install Packages
================

In your project workspace, you have some very basic packages that come pre-installed. We will need to install more packages for the workshop. 

Installing packages to your workspace is analogous to installing apps on your phone via the App Store / Google Play except we are installing packages from ``Bioconductor`` - a home for open source bioinformatics software.

In the ``console``, please insert the following lines of code to install the required packages:

... code-block:: R

    install.packages("ggplot2")
    install.packages("pheatmap")
    install.packages("ggpubr")
    install.packages("rcolorbrewer")
    install.packages("cluster")
    install.packages("gplots")
    install.packages("caret")
    install.packages("e1071")

