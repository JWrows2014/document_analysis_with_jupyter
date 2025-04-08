---
marp: true
---

<!-- _backgroundColor: maroon
_color: white -->

## <!-- .element: class="slideshow-title" --> Documenting Analysis with Jupyter Lab

by Joe Wu, PhD (BTEP)

---

## How Users Interface with Jupyter Lab

Jupyter Lab is a software that users install on personal computer and interact with through a web browser!

---

## Why use Jupyter Lab

* Analyzing large genomic datasets will likely require scientist to code and thus, require a tool that enables researchers to organize and maintain analysis steps, code, and output in an analysis notebook (sort of like a lab notebook for data analysis), which is what Jupyter Lab is.
* Additional benefits to using Jupyter Lab is that it
    * Facilitates sharing and publishing of analysis in many formats including `html`, `pdf`, and `markdown`
    * Ensures analysis reproducibility because the steps and tools used to generate the results are there and available others to reference
* Share on GitHub or [Binder](https://mybinder.org).
* Extensions for making notebook interactive (ie. [ipywidgets](https://ipywidgets.readthedocs.io/en/stable/)).
* For more on Jupyter Lab, read [https://en.wikipedia.org/wiki/Project_Jupyter](https://en.wikipedia.org/wiki/Project_Jupyter).

---

## Disclaimer

* This class: 
  * will not make participants experts in using Jupyter Lab or scripting. 
  * is a demo
    * experience using or installation onto personal computer of Jupyter Lab is not required to participate. 
    * BTEP staff will be happy to meet with participants to discuss installing or accessing Jupyter Lab after the class, as they are many options. Just email us at ncibtep@nih.gov if you need help!
* Do not worry about the coding part of this class but focus more on what Jupyter Lab can do in terms of organizing analysis steps

---

## Learning Objectives

After this class, participants will

* Have obtained an appreciation for Jupyter Lab as a one-stop shop for organizing analysis steps, code, and output.
* Be aware of or able to describe the steps involved in using Jupyter Lab for documenting data analysis including:
  * Starting a language specific notebook.
  * Writing formatted text and code.

---

## Ways to Access Jupyter Lab

* Biowulf ([https://hpc.nih.gov/apps/jupyter.html](https://hpc.nih.gov/apps/jupyter.html)). Biowulf is the NIH Unix-based high performance computing system.
  * Requires getting a [Biowulf account](https://hpc.nih.gov/docs/accounts.html)
      * Jupyter is available through [Biowulf's Open On Demand](https://hpcondemand.nih.gov/). Open On Demand enables users to run interactive applications such as Jupyter Lab through a web browser.
* [NIH Anaconda Professional](https://nih.sharepoint.com/sites/CIT-ApplicationRepository/SitePages/Anaconda.aspx){target=_blank}. This the way to go if users want to use Jupyter locally on government issued computer. Click [here](https://forms.office.com/g/CArrnuE4cD){target=_blank} to request access.

---

## Checklist for Running Jupyter Lab Locally

1. Python
  * Comes with [Anaconda](https://nih.sharepoint.com/sites/CIT-ApplicationRepository/SitePages/Anaconda.aspx){target=_blank} OR
  * Install as stand alone ([https://www.python.org/downloads/](https://www.python.org/downloads/){target=_blank})
2. Jupyter Lab
  * Included full Anaconda.
  * Requires separate install if using Miniconda ([https://jupyter.org/install](https://jupyter.org/install){target=_blank})
  * Users will install Jupyter through `conda` (`anaconda` or `mini conda`), `mamba`, or `pip` (the package installer for Python)
* Have Jupyter Lab installed
* Install languages and language specific packages. For instance
  * R
  * Julia
  * C++
* Add the languages to Jupyter Environment (Python is automatically added)
* Jupyter Lab is compatible with many languages, see [https://docs.jupyter.org/en/latest/projects/kernels.html](https://docs.jupyter.org/en/latest/projects/kernels.html) to learn more.

---

## Options for Installing Jupyter Lab on Personal Computer

* [Anaconda](https://www.anaconda.com/): Python, Jupyter Lab and many other data science tools are packaged with this.
* Install package managers [miniconda](https://docs.anaconda.com/miniconda/) or [mamba](https://mamba.readthedocs.io/en/latest/index.html). Both packages manager come with Python.
  * Install Jupyter Lab following the instructions at [https://jupyterlab.readthedocs.io/en/stable/getting_started/installation.html](https://jupyterlab.readthedocs.io/en/stable/getting_started/installation.html).
* As a stand alone without using Package managers: 
  * [https://www.python.org/downloads/](https://www.python.org/downloads/) for installing Python.
  * [https://jupyterlab.readthedocs.io/en/stable/getting_started/installation.html](https://jupyterlab.readthedocs.io/en/stable/getting_started/installation.html) for installing Jupyter Lab.

---

## Start a new Jupyter Lab Session

Once installed, Jupyter Lab runs through a web browser. To start a Jupyter Lab session, do the following.

```
jupyter lab --no-browser
```

Copy and paste any of the following URLs into a web browser to start using Jupyter. These URLs will be different for every Jupyter Lab session.

```
To access the server, open this file in a browser:
        file:///Users/wuz8/Library/Jupyter/runtime/jpserver-30985-open.html
    Or copy and paste one of these URLs:
        http://localhost:8890/lab?token=1952fcce201164f8368f2666f2f2625c0bbeeea1ddc20b2c
        http://127.0.0.1:8890/lab?token=1952fcce201164f8368f2666f2f2625c0bbeeea1ddc20b2c
```

---

## Writing Code, Viewing Output, and Documenting Analysis Steps in Jupyter Notebook

The first example will use Python code to demonstrate the utility of Jupyter Notebook for keeping code, output, and analysis steps all in one place.

* First, the `import` command of Python will be used to load packages `numpy` which is used for numeric computation and `matplotlib` which is a popular data visualization tool.
* Next, two numeric arrays (x and y) will be generated using `numpy` and its `array` sub-command.
* Finally, a scatter plot will be generated using `matplotlib` to visualize the relationship between the values in array x versus those in array y.
* See code in the [next slide](#10).

---

## Viewing Relation between two Numeric Arrays

```
import numpy
import matplotlib.pyplot as plt

plt.scatter(x,y)
plt.xlabel("x", size=15)
plt.ylabel("y", size=15)
plt.tick_params(labelsize=12)
plt.title("Relationship between x and y", size=16)
```

---

## X-Y scatter plot

![](./images/x_y_scatter.png)

---

## Importing Tabular Data in Jupyter Notebook

Analyses require scientists to work with tabular data. The next examples will demonstrate importing tabular data in Jupyter Notebook (hint: this will be language dependent) in both [Python's Pandas package](#12) and [R's `read.csv` function](#13).

---

## Importing Tabular Data Using Python

The dataset imported are:

* hbr_uhr_deg_chr22_with_significance.csv (RNA sequencing differential expression results table)
* hbr_uhr_top_deg_normalized_counts.csv (RNA sequencing gene expression)

```
import pandas
hbr_uhr_deg_chr22=pandas.read_csv("./hbr_uhr_deg_chr22_with_significance.csv")
hbr_uhr_top_deg_normalized_counts=pandas.read_csv("./hbr_uhr_top_deg_normalized_counts.csv", index_col=0)
```

To view the first five lines of the data tables use the `head` attributes of the data tables as shown below.

```
hbr_uhr_deg_chr22.head()
```

```
hbr_uhr_top_deg_normalized_counts.head()
```

---

## Running R Code in a Python Jupyter Notebook

Its possible to run R code using the [rpy2.ipython](https://rpy2.github.io), which the user will have to install (see [https://pypi.org/project/rpy2/](https://pypi.org/project/rpy2/)). Assuming rpy2.ipython has been installed, load it in a Python Jupyter notebook using the following.

```
%load_ext rpy2.ipython
```

To run R code in a Python specific Jupyter Notebook start the code cell with `%%R` then proceed to writing the R code.

---

## Importing Tabular Data using R

The code below will import the hbr_uhr_deg_chr22_with_significance.csv data (ie. RNA sequencing differential expression analysis results) using R's `read.csv` and stored as a dataframe called hbr_uhr_chr22_deg.

```
hbr_uhr_chr22_deg <- read.csv("./hbr_uhr_deg_chr22_with_significance.csv")
```

Because of R's column heading format rules, the column name "-log10PAdj" will be changed to "neg.log10PAdj":

```
colnames(hbr_uhr_chr22_deg)[4] <- "neg.log10PAdj"
```

Use the `head` command to view the first six lines of the newly imported hbr_uhr_chr22_deg dataframe.

```
head(hbr_uhr_chr22_deg)
```

---

## Overview of hbr_uhr_deg_chr22

* Imported using R and Python  
* Contains RNA sequencing differential expression analysis results. The columns are:
  * name: contains gene names
  * log2FoldChange: gene expression change between two experimental conditions on the log2 scale
  * PAdj: adjusted p-value indicating statistical confidence of the calculated gene expression change
  * -log10PAj: negative of the values in the PAdj column on a log10 scale
  * significance: whether the gene expression is up regulated, down regulated, or has no change between two experimental condition as determined by a user determined gene expression change and statistical confidence threshold
* See [next slide](#16) for a glimpse of the data

---

## First Five Lines of hbr_uhr_deg_chr22

| name | log2FoldChange | PAdj      |   -log10PAdj  | significance |
|------|----------------|-----------|---------------|--------------|
|SYNGR1|       -4.6     |  5.2e-217 |     216.2840  |      down    |
|SEPT3 |       -4.6     |  4.5e-204 |     203.3468  |      down    |
|YWHAH |       -2.5     |  4.7e-191 |     190.3279  |      down    |
|RPL3  |        1.7     |  5.4e-134 |     133.2676  |        ns    |
|PI4KA |       -2.0     |  2.9e-118 |     117.5376  |      down    |

---

## Overview of hbr_uhr_top_deg_normalized_counts

* Imported using Python
* Contains RNA sequencing gene expression counts where the columns are:
  * First column (not labeled) contains gene names
  * Columns 2 through 7 contains expression counts for each genes across the six samples
* See [next slide](#18)

---

## First Five Lines of hbr_uhr_top_deg_normalized_counts

|	       |    HBR_1	 |  HBR_2	 |   HBR_3  |  UHR_1	|  UHR_2	|  UHR_3 |
|--------|-----------|---------|----------|---------|---------|--------|
|SULT4A1 |	  375.0	 |  343.6	 |   339.4	|    3.5	|    6.9	|    2.6 | 
|MPPED1	 |    157.8	 |  158.4	 |   162.6	|    0.7	|    3.0	|    2.6 |
|PRAME	 |      0.0  |    0.0	 |     0.0	|  568.9	|  467.3	|  519.2 |
|IGLC2	 |      0.0  |    0.0	 |     0.0	|  488.6	|  498.0	|  457.5 |
|IGLC3	 |      0.0  |    0.0	 |     0.0	|  809.7	|  313.8	|  688.0 |

---

## Creating Plots from Tabular Data

These sets of exercises will create the following plots from the hbr_uhr_deg_chr22 and hbr_uhr_top_deg_normalized_counts data tables.

* Volcano plot for hbr_uhr_deg_chr22 using Python's Seaborn package and R's ggplot2
  * Volcano plot is a special case of a scatter plot that depicts changes on one axis and statistical confidence for the change on another. For RNA sequencing differential analysis, this will be log2 fold change and the negative of log10 p-value (or adjusted p-value).
* Heatmap for hbr_uhr_top_deg_normalized_counts.
  * Heatmaps depict numeric values and a color scale. Along with clustering (dendrograms), heatmaps can be used to identify patterns between groups. For instance, whether different biological conditions display differing patterns of gene expression.

---

## Volcano plot using Seaborn

The following code is used to create a volcano plot for the hbr_uhr_deg_chr22 data table using Seaborn.

* Step 1: importing seaborn package (`import seaborn`)
* Step 2: generate the plot using Seaborn's `scatterplot` function; the arguments are
    * hbr_uhr_deg_chr22: data
    * `x=`: specifies values to plot on the x-axis (ie. log2FoldChange)
    * `y=`: specifies values to plot on the y-axis (ie. -log10PAdj)
    * `hue=`: specifies values to color the dots by (ie. significance or whether expression was statistically up or down regulated) 

```
import seaborn
seaborn.scatterplot(hbr_uhr_deg_chr22,x="log2FoldChange", y="-log10PAdj", hue="significance")
```

---

## Volcano plot generated using Seaborn

![](./images/volcanco_seaborn.png)

---

## Volcano Plot using ggplot2

To construct the volcano plot using R's ggplot2 package, users will need to import it to the working environment via `library(ggplot2)`.

```
library(ggplot2)
```

Next, construct the plot using the code below.

```
ggplot(hbr_uhr_chr22_deg, aes(x=log2FoldChange, y=neg.log10PAdj, color=significance))+
geom_point()+xlab("Log2 Fold Change")+ylab("-log10 Adjusted P")+
theme(axis.title.x=element_text(size=15),axis.title.y=element_text(size=15),
axis.text.x=element_text(size=14),axis.text.y=element_text(size=14),
legend.title=element_text(size=15),legend.text=element_text(size=14))
```

---

## Volcano plot generated using ggplot2

![](./images/volcano_ggplot2.png)

---

## Create Heatmap using Seaborn

This exercise will use Seaborn's `clustermap` function to construct a gene expression heatmap of top differentially expressed genes in the HBR and UHR study. Heatmaps are another common visualization in RNA sequencing and allow scientists to identify clusters of samples with similar gene expression patterns.

First, import the dataset (hbr_uhr_top_deg_normalized_counts.csv) using `pandas.read_csv` and assign it to the variable hbr_uhr_top_deg_normalized_counts. Then use the code on the [next slide](#-25) to generate the heatmap.

---

## Code for Creating Heatmap using Seaborn

The `clustermap` function of seaborn takes the following arguments and options.

  * Data: hbr_uhr_top_deg_normalized_counts (the expression counts table imported using `pandas.read_csv`).
  * `z_score`: set this to 0 to scale the expression counts for each gene by the z_score.
  * `cmap`: specify a coloring scheme (ie. viridis)
  * `figsize`: specify figure size
  * `cbar_kws`: specify title for the heatmap color bar using a key-value pair
  * `cbar_pos`: specify coordinate to place the heatmap color bar

```
seaborn.clustermap(hbr_uhr_top_deg_normalized_counts,z_score=0,cmap="viridis",
                   figsize=(8,8),vmin=-1.5, vmax=1.5,cbar_kws=({"label": "z score"}),
                   cbar_pos=(0.855,0.8,0.025,0.15))
```

---

## Heatmap using Seaborn

![](./images/heatmap_seaborn.png)