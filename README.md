# Procedural vs. Declarative Control of Decision Making

Cher's project, but in (faster) Python code. An overview of this project can be found on this [BioarXiv preprint](https://www.biorxiv.org/content/10.1101/2023.01.10.523458v1.abstract). Instead of implementing models and running simulations in ACT-R, the two subsystems of declarative memory and procedural memory are directly modeled as Python code.

There are two major advantages to this strategy:

* The models are much (100x) faster to run and estimate, and we can use Nelder-Mead instead of discrete grid search;
* log likelihood is now calculated on a trial by trial bases, which gives significantly more data.
