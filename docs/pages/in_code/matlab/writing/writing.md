---
title: Writing JSON Files
nav_order: 2
parent: MATLAB
grand_parent: Using JSONs in Code
---

# Writing JSON Files
{:.no_toc}

* TOC
{:toc}

## Overview

This page describes how to read JSON files into a MATLAB script.

## Writing JSON Files in MATLAB

Just as how JSON files are read in as structs in MATLAB, you must be working with a struct to write a JSON file. The following is an example of how you write structs to a JSON file via MATLAB:

### MATLAB Code

```m
% The file path to the JSON you wish to write.
JSON_FILE_PATH = "path/to/json/file.json";

% Make the struct to write.
root = struct(...
  "inner_obj", ...
    struct( ...
      "example_boolean", true, ...
      "example_float", 5.7 ...
    ), ...
  "example_array", [1, 2, 3, 4, 5] ...
);

% Write the JSON file in as a struct.
json_data = savejson('', root, JSON_FILE_PATH);
```

### Output

This will save a JSON file to the file described by `JSON_FILE_PATH` and this file will look like:

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