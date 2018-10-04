# Workflow

Talos follows *POD* (prepare, optimize, deploy) workflow, with additional functionality for evaluation and reporting, including plots for visual analysis.

## (P)repare

Preparation involves the process of defining the hyperparameter space for the experiment, and the setting of the experiment options such as choosing of the optimization strategy.

See [Parameter dictionary](#parameter-dictionary), [Models](#models), and [Scan()](#scan).

## (O)ptimize

Optimization involves the automated process of finding an optimal hyperparameter combination for a well generalizing model for a given prediction task.

See [Optimization strategies](#optimization-strategies) and [Reporting](#reporting).

## (D)eploy

Deployment involves the automated process of storing locally the required assets for local or remote deployment of a predictive model for production purpose.

See [Predict()](#predict).

## Reporting and Evaluation

In addition Talos provides several useful tools for analysis and evaluation of experiments, including live updating plots for epoch-by-epoch visual analysis of experiment progress.

See [Reporting()](#reporting) and [Monitoring](#monitoring)
