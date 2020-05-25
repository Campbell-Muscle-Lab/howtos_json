---
title: Basic Structure
nav_order: 2
---

# Basic Structure
{:.no_toc}

* TOC
{:toc}

## What Exactly is a JSON?

JSON is an easy-to-use data-interchange format that is simple and human-readable. This is much preferred over traditional `txt` files since JSON files enforce a structure that leads them to be easier for both human and machine to interpret.

Here in the Cambpell Muscle Lab we use JSON files for model input/output.

## The JSON Structure

The JSON format consists of two basic structures:
  + A collection of name and value pairs where the name is used to index the value. 
      + For example, the name `"jared"` could index the value `7`. If you're familiar with Python, this is similar to a dictionary.
  + An ordered list of values. 
      + This is much like an array, list, or vector in many programming languages.

These basic structures take the forms of:

  + An *object* is an unordered set of the first structure of name and value pairs. 
      + Each object begins with a left brace, `{`, and ends with a right brace, `}`. 
      + Every name in the object is followed by a colon, then the value. 
      + Each name and value pair is seperated by a comma. 
      + An example of an object has been included below. This object contains six key/value pairs.
          ```json
          {
            "Jared": 7,
            "Elise": 1200,
            "Allen": 34,
            "Borris": "strings can also be values!",
            "Agatha": null,
            "Harold": true
          }
          ```
  + An *array* is an ordered collection of values. 
      + Arrays begin with a left bracket, `[`, and ends with a right bracket, `]`. 
      + Values in arrays are separated by commas. 
      + The following is an example of an array of numbers inside of an object:
          ```json
          {
            "my_array": [10, 11, 12, 13, 14]
          }
          ```
  + A *value* can be of the following types:
      + String
          + A sequence of characters surrounded by quotation marks.
              + Example: `"hello"`
      + Number
          + A regular integer or floating point number.
              + Example: `1.4` and `2`.
      + Object
          + An object as described above.
      + Array
          + An array as described above.
      + Boolean 
          + Either `true` or `false`.
      + `null`
          + Indicates no value for the given key.

