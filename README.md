# Enterobacter_classification

Repository designed to assign new sequences of Enterobacter to the MASH Clusters and Phylons developed through pangenomic study of the *Enterobacter* Genus [add citation here].

## Repository Contents
### Data
Contains data from the pangenomic study including the __L__ normalized and binarized matrices, representing the accessory genes associated with the phylon structure determined by NMF, as well as the __A__ binarized and normalized matrices, reprsenting strain associated with phylons. It contains the MASH sketches for the strains in the pangenome to compare against, as well as the representative seqeunces from the pangenome for the gene clusters determined by CD-HIT. Also contained is metadata for the pangenome strains, as well as eggnog annotations for the gene clusters in the pangneome. 
### Input Strains
The folder to place new strains to be classified using the pangenome structure. 5 example strains are given.
### Notebooks
Contains a jupyter notebook with code to visualize the results of the assignment pipeline.
### Scripts
Snakemake scripts used to process new strains and assign them mash distances and membership in pangneome gene clusters. 
### environment.yaml
File containing conda specification for environment to run notebook and pipeline. Please use conda flexible solver if there is difficulty in solving the environment.

## How to Use
Several Example strains are available in the Input_Strains folder, but a user can use their own assembled genomes ( as .fna files). The workflow will annotate the genomes with BAKTA, calculate mash distances to strains in the pangenome, cluster strain .faa files to the pangenome representative sequences, and combine results for all input files. 

### Steps
1. Install conda/mamba environment from .yaml file (and use flexible solver if issues are faced) (ex. `mamba env create -f environment.yaml --channel-priority flexible`).
2. Activate environment and navigate to /Scripts. In order to run snakemake workflow, run the command: `snakemake --use-singularity -c 8 -d ../`
3. Following completion of the pipeline, open `Classification.ipynb` and run in order to display strain classifications.