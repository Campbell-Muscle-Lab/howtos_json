---
title: Reading JSON Files
parent: Python
grand_parent: Using JSONs in Code
nav_order: 1
---

# Reading JSON Files
{:.no_toc}

* TOC
{:toc}

## Overview

This page goes over how to read in JSON files into Python.

## Reading JSON Files in Python

JSON files are read in as dictionaries in Python. The following is an example of how they are read in:

```python
import json

# This is where you describe the file path to your JSON file.
JSON_FILE_PATH = "your file path here"

# Open the file and load it in as a dictionary.
# NOTE: It is best to use `with` here as it automatically closes the file once
#       you go out of the indentation block.
with open(JSON_FILE_PATH, 'r') as f:
  j_d = json.load(f)
```