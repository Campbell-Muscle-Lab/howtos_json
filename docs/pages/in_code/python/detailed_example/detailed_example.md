---
title: A Detailed Example
nav_order: 3
parent: Python
grand_parent: Using JSONs in Code
---

# A Detailed Example
{:.no_toc}

* TOC
{:toc}

## Overview

Now that we have learned how to read and write JSON files using Python, we can move on to a more advanced demo.

For the sake of the demo, let's assume we have a model file in JSON format that we would like to:
1. Read into Python.
2. Modify one of the values in the dictionary read in from the JSON file.
3. Create an instance of a model class with the dictionary read in from the JSON file.
4. Write the model dictionary with the newly manipulated value as a new file.


## The JSON Model File

For the purpose of the demo, we're contriving a made up model file. The model file we're working with will be:

```json
{
  "model" : {
    "y0": [0, 105.3],
    "solver" : "Newton-Raphson",
    "xtol_rel": 1e-3,
    "verbose_logging": true
  }
}
```

## Breaking Down The Steps

The demo is chunked up into the code that fulfills the goal of the respective section, but the code can be ran all together at once.

### 1. Read the JSON File Into Python

We're going to read in the JSON model file much like we did in the [reading demo](../reading/reading.md).

```python
# Import the json module.
import json

# Describe the file path that we're going to read the model file from.
JSON_FILE_PATH = "our_model.json"

with open(JSON_FILE_PATH, 'r') as f:
  model = json.load(f)
```

### 2. Modify The Model In Python

Now we can manipulate the model from within Python. Let's turn the verbose logging off since we're not concerned with the output.

```python
# JSONs are read in as dictionaries in Python and thus are easy to manipulate.
model["model"]["verbose_logging"] = False
```

### 3. Create Model Object

For the purpose of this section, let's assume that we have a `Model` class defined by the following chunk of code:

```python
class Model:
  """A class for describing the model we're working with"""
  def __init__(self, json_model_dict):
    """Initialize a Model object

    Parameters
    ----------
    json_model_dict : dict
      The model dictionary that was read in via JSON.
    """
    self.y0 = json_model_dict["model"]["y0"]
    self.solver = json_model_dict["model"]["solver"]
    self.xtol_rel = json_model_dict["model"]["xtol_rel"]
    self.verbose_logging = json_model_dict["model"]["verbose_logging"]
```

Now we can create a `Model` object by doing the following:

```python
model_obj = Model(model)
```

### 4. Write the Modified Model Dictionary To JSON

We would like to record the set of model parameters to run this simulation, so we can write the modified model file to another file. We do this with the following code:

```python
# Indicate where we'd like to store our modified model file.
new_json_file = "modified_model.json"

with open(new_json_file, 'w') as f:
  json.dump(model, f, indent=2)
```

## Conclusion

This demo is obviously heavily contrived but it demonstrates all of the basic functionality of working with JSON files in Python.