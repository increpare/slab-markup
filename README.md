SLAB-MARKUP - SLAB 1.2 parser for JavaScript (+sublime text syntax files)
=================================================

[![NPM version](https://img.shields.io/npm/v/slab-markup.svg)](https://www.npmjs.org/package/slab-markup)

Human-friendly markup format.

This repository contains a javasript module to read it, and a Sublime Text 3 syntax highlighting file.

Installation
------------

### SLAB module for node.js

```
npm install slab-markup
```

EXAMPLE
-------
Here's an example of a SLAB file:

```
description: a simple key-value pair
example: bar

description: string-wrapping support
example: so many bars all the bars in the 
	universe and some bars from even some 
	other universes really a lot of bars.

description: array of strings
example:
	one string
	another string

description: array of structures
example:
	foo:bar
	ding:bat

	foo:bar
	ding:bat
```
  
Whose JSON representation is 

```
[
  {
    "description": "a simple key value pair",
    "example": "bar"
  },
  {
    "description": "string-wrapping support",
    "example": "so many bars all the bars in the universe and some bars from even some other universes really a lot of bars."
  },
  {
    "description": "array of strings",
    "example": [
      "one string",
      "another string"
    ]
  },
  {
    "description": "array of structures",
    "example": [
      {
        "foo": "bar",
        "ding": "bat"
      },
      {
        "foo": "bar",
        "ding": "bat"
      }
    ]
  }
]
```


	
The equivalent YAML is

```
---
- description: a simple key value pair
  example: bar
- description: string-wrapping support
  example: so many bars all the bars in the universe and some bars from even some
    other universes really a lot of bars.
- description: array of strings
  example:
  - one string
  - another string
- description: array of structures
  example:
  - foo: bar
    ding: bat
  - foo: bar
    ding: bat
```

(Which is basically the same as the SLAB version, and the libraries for parsing that are far more robust/numerous. So you should probably use that instead.)

API
---

To parse a string, do

```
var slab = require("slab-markup")
var db = slab.parse(myString);
```

To parse an file, do: 

```
var slab = require("slab-markup)
var db = slab.parseSync('myfile.slab');
```


Sublime Text 3 Syntax Highlighting
----------------------------------

To get the syntax highlighter to work, copy the [slab.sublime_syntax](https://raw.githubusercontent.com/increpare/slab-markup/master/slab.sublime_syntax) file to your Packages/User directory in sublime text.

