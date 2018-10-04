# Models

The purpose of Talos is to allow you to continue working with Keras models exactly the way you are used to, and to allow leveraging the flexibility available in Keras without adding any restrictions. **Any Keras model can be used in a Talos experiment** and Talos does not introduce any new syntax to Keras models.

> A single line example of modifying the model

```python
# In original Keras model
model.add(64, input_dim=8)

# In Talos
model.add(Dense(params['first_neuron'], input_dim=8))

```

In order to use a Keras model in an experiment, you have to modify a working Keras model in a way where the hyperparameter references are replaced with the parameter dictionary references.

You can find several examples of modified Keras models ready for a Talos experiment [here](https://github.com/autonomio/talos/blob/master/talos/examples/models.py) and a code complete example with parameter dictionary and experiment configuration [here](https://github.com/autonomio/talos/blob/master/examples/iris.py).

<aside class="notice">
You should always make sure that your Keras model works as-is before using it in a Talos experiment.
</aside>
