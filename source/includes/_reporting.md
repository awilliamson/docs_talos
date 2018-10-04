## Reporting()

The experiment results can be analyzed through the [Reporting()](https://github.com/autonomio/talos/blob/master/talos/utils/reporting.py) command. The reporting consist of access to several meaningful signals related with the experiment, together with a dataframe with results for each permutation, together with the corresponding hyperparameter configurations. Reporting may be used after Scan completes, or during an experiment (from a different shell / kernel).

> Using reporting

```python
r = Reporting('experiment_log.csv')

# returns the results dataframe
r.data

# returns the highest value for 'val_fmeasure'
r.high('val_fmeasure')

# returns the number of rounds it took to find best model
r.rounds2high()

# draws a histogram for 'val_acc'
r.plot_hist()
```

<aside class="notice">
Reporting works by loading the experiment log .csv file which is saved locally as part of the experiment. The filename can be changed through dataset_name and experiment_no Scan arguments.
</aside>


The evaluation of experiment results consist of Reporting and Predict classes.

### Reporting Functions

See docstrings for each function for a more detailed description.

**`high`** The highest result for a given metric

**`rounds`**  The number of rounds in the experiment

**`rounds2high`** The number of rounds it took to get highest result

**`low`** The lowest result for a given metric

**`correlate`** A dataframe with Spearman correlation against a given metric

**`plot_line`** A round-by-round line graph for a given metric

**`plot_hist`** A histogram for a given metric where each observation is a permutation

**`plot_corr`** A correlation heatmap where a single metric is compared against hyperparameters

**`table`** A sortable dataframe with a given metric and hyperparameters

**`best_params`** A dictionary of parameters from the best model

### Reporting Arguments

Parameter | Default | Description
--------- | ------- | -----------
filename | None | name of the file with experiment log
