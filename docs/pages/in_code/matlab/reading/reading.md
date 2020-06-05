---
title: Reading JSON Files
nav_order: 1
parent: MATLAB
grand_parent: Using JSONs in Code
---

# Reading JSON Files
{:.no_toc}

* TOC
{:toc}

## Overview

This page describes how to read JSON files into a MATLAB script.

## Reading JSON Files in MATLAB

JSON files are read in as structs in MATLAB. The following is an example of how they're read in and manipulated via MATLAB:

### Example JSON File

```json
{
  "root": {
    "inner_obj": {
      "example_boolean": true,
      "example_float": 5.7
    },
    "example_array": [1, 2, 3, 4, 5]
  }
}
```

### MATLAB Code

```m
% The file path to the JSON you wish to read.
JSON_FILE_PATH = "path/to/json/file.json";

% Read the JSON file in as a struct.
json_data = loadjson(JSON_FILE_PATH);

% Examples of accessing the JSON structure.
json_data.root.inner_obj.example_boolean
json_data.root.inner_obj.example_float
json_data.example_array(5)
```

### MATLAB Output

```
ans =
  logical
  1
ans =
  5.7000
ans =
  5
```