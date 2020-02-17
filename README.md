# Cyclum

## Introduction
Cyclum is a package to tackle cell cycle. It provides methods to recover cell cycle information and remove cell cycle factor from the scRNA-seq data. The methodology is to rely on the circular manifold, instead of the marker genes. Multiple methods suits this idea. We provide an Auto-Encoder based realization at this time, and we are adding Gaussian Process Latent Variable Model soon. Also provided are a set of supplementary tools to visualize and anaylzing the result, in python and in R. We also provide a [one-click self-contained demo](https://github.com/KChen-lab/Cyclum-Demo) ships with its dataset.

![Illustration](old-version/docs/Illustration.PNG)

For further information, please also refer to the [documentation](https://kchen-lab.github.io/cyclum/) and the [manuscript](https://www.biorxiv.org/content/10.1101/625566v1).

## Updated version:
We revised almost everything, except for the concept of using sinusoidal function in an autoencoder to find circular biological processes *ab initio*. The autoencoder is now rewritten using [keras](https://keras.io/), in a more readable way. We hope this will help researchers who want to experiment similar network structures. We also implemented class `cyclum.tuning.CyclumAutoTune`, which automatically select the proper number of linear components to help find the "most circular" manifold.

## Transferring data between python and R:
Although Python is a good data analysis tool in addition to a general programing language, researchers may want to use R, which is more focused on statistics. Cyclum is implemented in python, but in order to help use both languages, we implemented `mat2hdf` and `hdf2mat` in both Python and R, to help transferring data back and forth rapidly. In general, the correspondence of data structures in R and Python are: unnamed matrices -- 2D numpy.array, named matrices -- pandas.DataFrame, data.frame -- pandas.DataFrame. (Prerequisites: `hdf5r` in R, `h5py` in python.)

[GSEA](http://software.broadinstitute.org/gsea/index.jsp) is a powerful tool to perform downstream gene enrichment analysis. We implemented in R...
- `mat2txt`, which writes a expression matrix to a GSEA compatible `.txt` file (Prerequisite: `data.table`, for much faster writing than `write.table`),
- `vec2cls`, which writes phenotypes (either discrete, e.g., cell type, or continuous, e.g., pseudotime) to a GSEA compatible `.cls` file,
- `mat2cls`, which writes multiple sets of phenotypes (continuous only, e.g., multiple PCs) to a GSEA compatible `.cls` file.

[Documentation](https://lshh125.github.io/cyclum2/index.html) is available at https://lshh125.github.io/cyclum2/index.html.
