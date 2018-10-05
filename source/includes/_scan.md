# Commands

## Scan()

> Starting a simple quantum random experiment

```python
Scan(x, y,
     params=p,
     model=input_model,
     random_method=quantum)
```

The experiment is configured and started through the [Scan()](https://github.com/autonomio/talos/blob/master/talos/scan/Scan.py) command. All of the options effecting the experiment, other than the hyperparameters themselves, are configured through the Scan arguments. The most common use-case is where ~10 arguments are invoked.

### Scan Arguments

Parameter | Default | Description
--------- | ------- | -----------
`x` | user input | prediction features
`y` | user input | prediction outcome variable
`params` | user input | the parameter dictionary
`model` | user input | the Keras model as a function
`dataset_name` | None | Used for experiment log
`experiment_no` | None | Used for experiment log
`x_val` | None | validation data for x
`y_val` | None | validation data for y
`val_split` | .3 | validation data split ratio
`shuffle` | True | if the data should be shuffled or not
`random_method` | 'uniform_mersenne' | the random method to be used
`search_method` | 'random' | the order in which permutations are checked
`reduction_method` | None | type of probabilistic reduction is used
`reduction_interval` | 50 | number of permutations after which reduction is applied
`reduction_window` | 20 | the look back window for reduction process
`grid_downsample` | None | A float to indicate fraction for random sampling
`reduction_threshold` | 0.2 | The threshold at which reduction is applied
`reduction_metric` | 'val_acc' | The metric to be used for reduction
`reduce_loss` | False | If reduction_metric is a loss function
`round_limit` | None | Maximum number of permutations in the experiment
`talos_log_name` | 'talos.log' | Name of the master log
`debug` | False | Turn on debug messages
`seed` | None | Seed for random states
`clear_tf_session` | True | Clear tensorflow session after each round
`disable_progress_bar` | False | Show live updating progress bar
`functional_model` | False | For functional model support
`last_epoch_value` | False | Reporting last epoch value in log
`print_params` | False | Print each permutation hyperparameters

<aside class="notice"> x, y, params, and model are the only needed arguments to start the experiment, all other are optional.</aside>

### Scan Object

The scan object has several attributes that are used for `Reporting()`, `Predict()` and `Deploy()`, but may also be useful to access directly. The namespace only consist of meaningful attributes.

```python

# returns the results dataframe
h.data

# returns the experiment configuration details
h.details

# returns the epoch entropy dataframe
h.peak_epochs_df

# returns the saved models (json)
h.saved_models

# returns the saved model weights
h.saved_weights

# returns x data
h.x

# returns y data
h.y

```
