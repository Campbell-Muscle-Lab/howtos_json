---
title: Writing JSON Files
nav_order: 2
parent: Python
grand_parent: Using JSONs in Code
---

# Writing JSON Files
{:.no_toc}

* TOC
{:toc}

## Overview

This page goes over how to write JSON files using Python.

## Writing JSON Files Using Python

JSON files are written using dictionaries in Python. The dictionary class mimics the tree structure of a JSON perfectly.

The following is an example of writing a simple dictionary to a JSON file.

```python
# Import the json module for reading/writing JSONs.
import json

# Describe the file path where you would like to save the JSON file.
JSON_FILE_PATH = "python_writing_demo.json"

# Form the dictionary that we would like to write. Notice how close this syntax
# is to the JSON structure!
our_dict = {
  "model1": {
    "mode": "fast",
    "solver": 2
  },
  "model2": {
    "mode": "slow",
    "solver": 4
  },
  "y0": [10, 112.07]
}

# Now we write the dictionary to a JSON file. 
# NOTE: As with the Python JSON "reading" demo, it is best practice to use
#       `with` here since it automatically handles the closing of the file.
with open(JSON_FILE_PATH, 'w') as f:
  json.dump(our_dict, f, indent=2)
```

Note how we included `indent=2` in the last line of the example. This automatically formats your JSON file to be far more readable. 