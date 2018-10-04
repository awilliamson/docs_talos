# Optimization Strategies

Talos incorporates several optimization strategies:

- Grid search
- Random search
- Probabilistic reduction

## Grid search

Grid search is the default optimization strategy; all hyperparameter permutations in a given parameter boundary will be processed. Grid search is not recommended for anything but very small permutation spaces. A better option is to use random optimization strategy by invoking `grid_downsample` in Scan().


## Random Optimizers

Random search is the recommended optimization strategy in Talos. This is invoked through the 'grid_downsample' argument in Scan() with a floating point value in the experiment options. For example, to randomly pick 10% of the permutations, a grid_downsample value of 0.1 is used.

```python
Scan(x, y,
     params=p,
     model=input_model,
     grid_downsample=.1)
```

Several pseudo, quasi, true, and quantum random methods are provided for random searches. These are controlled through the 'random_method' argument in Scan().

```python
Scan(x, y,
     params=p,
     model=input_model,
     grid_downsample=.1,
     random_method=quantum)
```

- Quantum
- Ambient sound
- Halton sequence
- Sobol sequence
- Korobov matrix
- Latin hypercube
- Latin hypercube with Sudoku style constraint
- Improved Latin hypercube (very slow)
- Uniform Mersenne
- Uniform cryptographically secure

Each random method results in a different degree of discrepancy; whereas uniform random methods tend to have higher discrepancy, as does quantum and ambient sound, hypercube and Korobov have lower.  

## Probabilistic reduction

The probabilistic reducers can be used together with a Grid search, or together with any of the Random methods. The reducer makes a stop between set number of rounds i.e. 'reduction_interval' and uses a probabilistic method to remove poorly performing parameter configurations from the remaining search space.

Several parameters are related with this:

**Reduction Method:** Currently only one reduction method is supported 'correlation'.

**Reduction Interval:** The number of rounds between each reduction stop.

**Reduction Window:** The number of rounds to look back for input signals (e.g. when reduction_window is 50, the results of the last 50 rounds are used for inference)

**Reduction Threshold:** A floating point value between 0 and 1, where 1 is perfect correlation and 0 is no correlation. The lower the correlation, the less significant a given hyperparameter is with results.

**Reduction Metric:** The metric against which optimization is performed (e.g. 'val_acc' or 'fmeasure')

**Reduce Loss:** If 'reduction_metric' is a loss metric, then this needs to be True.
