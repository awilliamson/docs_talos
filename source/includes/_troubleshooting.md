# Troubleshooting

If you run into trouble with something, or things are not working as expected, there are several things to do:

## Need help

- Read this manual
- See one of the [examples](https://github.com/autonomio/talos/tree/master/examples)
- Ask a [question](https://stackoverflow.com/questions/ask) on Stackoverflow
- Ask [for help](https://gitter.im/_talos_/Lobby?source=orgpage) in the Talos Gitter channel

## Found an issue

- See the [open](https://github.com/autonomio/talos/issues) and [closed](https://github.com/autonomio/talos/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aclosed+) issues on Github.
- See the [Common errors](#common-errors)

## Common errors

There are several common user-related cases where resulting errors are simple to overcome.

### `subprocess32 error`

This might arise during the installation on Python2.7 systems. The error results from a dependency in matplotlib. The issue can be overcome by first installing an older version of matplotlib:

`pip install matplotlib==1.5.3`

### `wrong numpy version`

This might arise in Python2.7 systems. The issue is overcome by installing a specific version of Numpy:

`pip install numpy==1.14.5`

### `TypeError: 'str' object is not callable`

This error comes as a result of listing optimizers as string values as opposed to the actual object name in the params dictionary. The solution is to use the object name instead.

### `TypeError: unsupported operand type(s) for +: 'int' and 'numpy.str_'`

Same as above.

### `TypeError: 'numpy.str_' object cannot be interpreted as an integer`

Same as above.

### `ValueError: Could not interpret optimizer identifier: <class 'keras.optimizers.Adam'>`

This is the reverse of the above; when lr_normalizer is not used, string values for optimizers should be used in the params dictionary.

### `KeyError: 'first_neuron'`

The 'first_neuron' hyperparameter is missing from the params dictionary, or it's called something else than 'first_neuron'.

### `KeyError: 'hidden_layers' or KeyError: 'dropout'`

When ever hidden_layers is applied in the model, hidden_layers and dropout parameters need to be included in the params dictionary

### `AttributeError: 'History' object has no attribute 'keys'`

This happens when the input model has:

`return model, out`

You fix this by using the right order for the objects:

`return out, model`

<aside class="notice"> If everything else fails, <a href=https://github.com/autonomio/talos/issues/new/choose> post a new issue </a> on Github.
</aside>
