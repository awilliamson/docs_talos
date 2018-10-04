# Getting Started

```python
import talos as ta

p = {
  # your parameter boundaries come here
}

def input_model():
  # your model comes here

ta.Scan(x, y, p, input_model)
```

> Find code complete examples [here](#)

To get started with your first experiment is easy. You need to have three things:

- a hyperparameter dictionary
- a working Keras model
- a Talos experiment

**STEP 1** >> In a regular Python dictionary, you declare the hyperparameters and the boundaries you want to include in the experiment.

**STEP 2** >> In order to prepare a Keras model for a Talos experiment, you simply replace parameters you want to include in the scan, with references to the parameter dictionary.

**STEP 3** >> To start the experiment, you input the parameter dictionary and the Keras model into Talos with the option for Grid, Random, or Probabilistic optimization strategy.

<aside class="notice">
Setting a complex hyperparameter optimization experiment with Talos rarely takes longer than 5 minutes.
</aside>
