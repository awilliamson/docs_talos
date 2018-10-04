# Parameter Dictionary

The first step in an experiment is to decide the hyperparameters you want to use in the optimization process.

> Example parameter dictionary:

```python
from keras.activations import relu, elu

p = {
    'first_neuron': [12, 24, 48],
    'activation': [relu, elu],
    'batch_size': [10, 20, 30]
}
```
> Activations need to go in as objects and not strings

In addition to standard Keras hyperparameters, Talos allows several extra conveniences such as the ability to include number of hidden layers in the process.

## Input Formats

Parameters may be inputted in three distinct ways:

- as a set of discreet values in a list
- as a range of values in a tuple
- as a single value in list


```python
# discreet values in a list
p = {'first_neuron': [12, 24, 48, 96]}

# range of values in a tuple
p = {'first_neuron': (12, 48, 10)}

# a single value
p = {'first_neuron': [12]}

```

When a tuple is used for a range of values, the first value is *min*, second value is *max* and the third value is *steps*.

## Allowed hyperparameters

Generally speaking, whatever hyperparameters you can use in Keras, you can include in a Talos experiment as simply as including the hyperparameter label together with the desired values or the range of values in the parameter dictionary.

If you find that a given hyperparamter is not supported, [create an issue](https://github.com/autonomio/talos/issues/new/choose) on Github.

## Hidden Layers

Each hidden layer is followed by a Dropout regularizer. If this is undesired, set dropout to 0 with ```dropout: [0]``` in the parameter dictionary.

```python
from talos.model.layers import hidden_layers

def input_model():
  # model prep and input layer...
  hidden_layers(model, params, 1)
  # rest of the model...
```

Including hidden_layers in a model allows the use of number of hidden layers as an optimization parameter.

<aside class="notice">
When hidden layers are used, <code>dropout, hidden_layers, and first_neuron</code> parameters must be included in the parameter dictionary.
</aside>

## LR Normalizer

As one experiment may include more than one optimizer, and optimizers generally have default learning rates in different order of magnitudes, lr_normalizer can be used to allow simultanously including different optimizers and different degrees of learning rates into the Talos experiment.

```python
from talos.model.normalizers import lr_normalizer
# model first part is here ...
model.compile(loss='binary_crossentropy',
              optimizer=params['optimizer'](lr_normalizer(params['lr'], params['optimizer'])),
              metrics=['accuracy'])
# model ending part is here ...
```

<aside class="notice">
The lr_normalizer needs to be invoked explicitly
</aside>
