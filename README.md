# Procedural vs. Declarative Control of Decision Making

Cher's project, but in (faster) Python code. An overview of this project can be found on this [BioarXiv preprint](https://www.biorxiv.org/content/10.1101/2023.01.10.523458v1.abstract). Instead of implementing models and running simulations in ACT-R, the two subsystems of declarative memory and procedural memory are directly modeled as Python code.

There are two major advantages to this strategy:

* The models are much (100x) faster to run and estimate, and we can use Nelder-Mead instead of discrete grid search;
* log likelihood is now calculated on a trial by trial bases, which gives significantly more data.

# Log-Likelihood Implementation

Declarative and procedural models will be compared using log-likelihood. Instead of using aggregate data, we will use Nathaniel Daw's (2011) original approach and calculate the probability that a given model generates the series of decisions made across two runs. 

The likelihood of a model $m$ given that a participant $p$ has made choice $c_{i,r}$ at the $i$-th trial of run $r$ is simply the probability of that choice being made by model $m$:

$\mathcal{L}(m|c_{p,r,i}) = P(c_{p,r,i}|m)$

The likelihood of a model $m$ given all the choices made by participant $p$ across all runs is simply the likelihood of a model making all of the participant's choices:

$\mathcal{L}(m|p) = \mathcal{L}(m|c_{p,1,1}, \dots, c_{p,r,i})$

In turn, this is just the product of the probability that the model would make every choice in the sequence:

$\mathcal{L}(m|p) = \prod_r \prod_i P(c_{p,r,i}|m)$

Finally, as it is convenient, we will take the log-likelihood, thus transforming all products of probabilities into sums of log-probabilities:

$\log \mathcal{L} = \sum_r \sum_i \log P(c_{p,r,i|m})$
