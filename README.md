# open
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.10291042.svg)](https://doi.org/10.5281/zenodo.10291042)

## Overview
This repository stores the entire workflow for the perspective "Investing in open and FAIR practices for more usable and equitable climate-risk research" This includes all data corresponding to the articles included in our review sample, and all code for processing data, generating summary statistics, and producing the figures in the manuscript. 

## Journal reference
Will update upon acceptance to a peer-reviewed journal. 

## Data Reference
The repository includes all raw, interim, and final data outputs. We note that some "interim" or "processed" data, such as data/processed/articles_reviewed.csv is not produced by code. For these reasons, these datasets are not treated as a separate minted data release. 

## Code Reference
This study does not make use of any minted software releases. The raw data and all code is included in the repository. Instructions for reproducing reported summary statistics and figures in the manuscript are in the next section.

## Reproduce my analysis
These instructions assume that you have [conda](https://docs.conda.io/en/latest/) or [mamba](https://mamba.readthedocs.io/en/latest/) installed. These instructions were successfully followed on the following systems:
1. Ubuntu machine with mamba version 1.4.2
2. A macOS Monterey (version 12.4) machine with conda version 23.1.0. Mamba solves the environment much faster than conda and is recommended if you have it set up.
3. A macOS Moneterey (version 12.2) with conda version 22.9.0.    

### Environment set up
Clone the repository into a local project directory.

This project was developed with Python version 3.11.7

#### With Conda
From the terminal in your local project directory, run `cd env` and then `conda env create -f environment.yml` or replace `conda` with `mamba`.

#### With Pip
1. From the terminal in your local project directory, run `conda create -n open python=3.11.7` or replace `conda` with `mamba`.
2. Activate the conda environment. 
3. Run `pip install -r requirements.txt`

#### Create ipykernel to run Jupyter Notebooks
Create an ipykernel for the environment. For the remainder of the instructions, we refer to this as the 'project environment.' If you are new to Jupyter Notebooks and/or conda, please see: https://ipython.readthedocs.io/en/stable/install/kernel_install.html#kernels-for-different-environments. 

### Processing data
In the src/ directory, open the process_data.ipynb notebook and activate the project environment. You can run all cells. The code in this notebook performs two tasks. First, it returns the list of journals to search according to the criteria defined in the Supplementary Information in the manuscript. Second, it takes the list of articles returned for each journal and applies the criteria defined in the Supplementary Information to obtain our review sample. The following table is a summary of the tasks:

|Task|Input|Output|
|----|-----|------|
|Obtain and write out the list of journals for our review sample|data/interim/JCR_SCEI_Filtered.csv|data/processed/journals_to_search.csv|
|Obtain and write out the articles that make our review sample|data/raw/articles/*.txt|data/interim/articles.csv|

### Generating summary statistics and figures
In the src/directory, open the Results.ipynb notebook and activate the project environment. You can run all cells. This notebook performs several tasks. First, the data from data/processed/articles_reviewed.csv and data/processed/journals_to_search.csv are loaded and merged to process the results of our review into summary statistics and figures. Second, summary statistics about data and code openness are computed and printed. Finally, figures 1 and 2 are written out in the fig/ directory as png files. 

## Contact (corresponding author)
So far, these instructions have resulted in successful reproduction of the figures and summary statistics reported in the manuscript, but you may run into issues and need assistance debugging. Please contact Adam Pollack at adam.b.pollack@dartmouth.edu if you have any issues following these steps. 
