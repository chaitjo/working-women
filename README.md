# Working Women and Caste in India

This repository contains code for the paper ["Working Women and Caste in India: A Study of Social Disadvantage using Feature Attribution"](https://arxiv.org/abs/1905.03092) by Kuhu Joshi and Chaitanya K. Joshi, prsented at the [ICLR 2019 AI for Social Good Workshop](https://aiforsocialgood.github.io/iclr2019/).

Women belonging to the socially disadvantaged caste-groups in India have historically been engaged in labour-intensive, blue-collar work. 
We study whether there has been any change in the ability to predict a woman’s work-status and work-type based on her caste by interpreting machine learning models using the [SHAP feature attribution framework](https://towardsdatascience.com/interpretable-machine-learning-with-xgboost-9ec80d148d27). 
We find that caste is now a less important determinant of work for the younger generation of women compared to the older generation. 
Moreover, younger women from disadvantaged castes are now more likely to be working in white-collar jobs.

Our methodology can similarly be used to study the persistence of, as well as the nuanced patterns underlying other types of social disadvantage, stratification, and bias in both developing and
developed country contexts.

![](/res/figs.PNG)

# Overview

We design three binary classification experiments to predict a woman’s work: 
1. Having a job or not (*work-status*)
2. Having a blue collar job or not (*blue-collar*)
3. Having a white collar job or not (*white-collar*). 

For each experiment, we train an ensemble Gradient Boosting Decision Tree (GBDT) model using [LightGBM](https://github.com/Microsoft/LightGBM).
Next, we interpret the trained models using the [SHAP feature attribution framework](https://github.com/slundberg/shap) for tree ensembles. 
We compute SHAP values for our entire dataset, following [Lundberg et al. (2018)](https://arxiv.org/abs/1802.03888) as a guide to using and interpreting the explanations obtained. 
These explanations allow us to understand how a single feature affects the model’s output, summarize relative feature importance over the entire dataset, and analyze higher order interactions among feature pairs.

This repository contains datasets, Jupyter notebooks and saved models for reproducing our results.
In addition to the main results from the paper (on NFHS-4 2015-16), we included notebooks containing results on NFHS-3, 2005-06.

Overview of important files/directories:
- `has_occ-201516.ipynb`: Notebook for the *work-status* experiment on NFHS-4.
- `blue_collar-201516.ipynb`: Notebook for the *blue-collar* experiment on NFHS-4.
- `white_collar-201516.ipynb`: Notebook for the *white-collar* experiment on NFHS-4.
- `\data`: NFHS datasets as `.csv` files, after retaining only representative samples of female participants.
- `\notebooks_200506`: Notebooks for experiments with NFHS-3.
- `\html`: HTML-ified notebooks for both NFHS-4 and NFHS-3 for easy viewing in browsers.
- `\models`: Saved LightGBM model files for reproducing our results. 

# Installation

In a nutshell, the repository must be set up by installing Python 3.6.8 and the exact package versions in `requirements.txt` using Anaconda or Pip.

Step-by-step guide for local installation using a Terminal (Mac/Linux) or Git Bash (Windows):

1. Install [Anaconda 3](https://www.anaconda.com/) for managing Python packages and environments.
2. Launch Terminal/Bash and clone the repository (type the commands below into Terminal). 
```
git clone https://github.com/chaitjo/working-women.git
cd working-women
```
3. Set up conda environment and activate it.
```
conda create -n working-women-env python=3.6.8
source activate working-women-env
```
4. Install dependencies and Jupyter Lab (for using notebooks).
```
conda install --yes --file requirements.txt
conda install -c conda-forge jupyterlab
```

# Usage

Notebooks provided for each of our experiments can be run and modified using Jupyter Lab.
```
cd working-women  # Make sure you are in the project directory
jupyter lab       # Launch Jupyter Lab in a browser
```
