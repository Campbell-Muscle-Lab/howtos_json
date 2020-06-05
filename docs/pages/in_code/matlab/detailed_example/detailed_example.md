---
title: A Detailed Example
nav_order: 3
parent: MATLAB
grand_parent: Using JSONs in Code
---

# A Detailed Example
{:.no_toc}

* TOC
{:toc}

## Overview

Now that we have learned how to read and write JSON files using MATLAB, we can move on to a more advanced demo.

For the sake of the demo, let's assume we have a model file in JSON format that we would like to:
1. Read into MATLAB.
2. Modify one of the values in the struct read in from the JSON file.
3. Create an instance of a model class with the struct read in from the JSON file.
4. Write the model struct with the newly manipulated value as a new file.


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

### 1. Read the JSON File Into MATLAB

We're going to read in the JSON model file much like we did in the [reading demo](../reading/reading.md).

```m
% Describe the file path that we're going to read the model file from.
JSON_FILE_PATH = 'our_model.json';

model = loadjson(JSON_FILE_PATH);
```

### 2. Modify The Model In MATLAB

Now we can manipulate the model from within Python. Let's turn the verbose logging off since we're not concerned with the output.

```m
% JSONs are read in as dictionaries in Python and thus are easy to manipulate.
model.model.verbose_logging = False
```

### 3. Create Model Object

For the purpose of this section, let's assume that we have a `Model` class defined by the following chunk of code:

```m
classdef Model   
    properties
        y0
        solver
        xtol_rel
        verbose_logging
    end
    
    methods
        function obj = Model(model)
            %MODEL Construct an instance of this class
            model = model.model;
            obj.y0 = model.y0;
            obj.solver = model.solver;
            obj.xtol_rel = model.xtol_rel;
            obj.verbose_logging = model.verbose_logging;
        end
        
    end
end
```

Now we can create a `Model` object by doing the following:

```m
model_obj = Model(model)
```

### 4. Write the Modified Model Struct To JSON

We would like to record the set of model parameters to run this simulation, so we can write the modified model file to another file. We do this with the following code:

```m
% Indicate where we'd like to store our modified model file.
new_json_file = 'modified_model.json'

savejson('', model, new_json_file);
```

## Conclusion

This demo is obviously heavily contrived but it demonstrates all of the basic functionality of working with JSON files in MATLAB.