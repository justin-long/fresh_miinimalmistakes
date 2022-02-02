---
Title: "Implementing a Bayesian CART Model Search"
excerpt: "Our implementation of the Bayesian CART model search algorithm."
---
Joint work with John Yannotty. 

**GitHub:** [View project on GitHub](https://github.com/justin-long/Bayesian_CART)

Classification and regression tree (CART) models are used to specify the conditional distribution of the
response variable y for given values of a covariate vector x. These models partition the covariate space into
subsets so that the distributions of the response variable y are alike within each of such subsets. In a tree,
there are internal nodes and terminal nodes where the terminal nodes are associated with each of the unique
partitions of the covariate vector. The book “Classification and Regression Trees” written by Breiman et al. first made these models popular.

The current paper proposed by Chipman et al., introduced a Bayesian framework for this class of
models. The main aim of their paper was to find a Bayesian framework for the CART models through prior
specification and a stochastic search. The main idea consists of specifying priors on the tree and related
parameters, which combined with the assumed data generating model, induces corresponding posterior distribution. The posteriors are then used to find a better CART model through a stochastic search process.
In cases where the posterior is not straightforward, they used a Metropolis-Hastings algorithm to explore
the posterior. Their model selection criteria include methods such as posterior probability and marginal
likelihood.

Furthermore, the Bayesian CART framework presented in this paper has a few primary applications.
First, the model can be used for prediction or classification, as the stochastic search will generate posterior
predictive distributions for any set of specified values of the covariates.
Additionally, the model search algorithm is able to identify a set of plausible tree structures that are supported by relatively high posterior probability. This is an advantage over the traditional CART model, which relies on a greedy approach to select an optimal tree based on certain criteria.

