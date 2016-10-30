A SLAB parser for JavaScript
============================

[![NPM version](https://img.shields.io/npm/v/slab-markup.svg)](https://www.npmjs.org/package/slab-markup)

A human-friendly markup format.

Installation
------------

### SLAB module for node.js

```
npm install slab-markup
```


###Sublime Text 3 Syntax Highlighting

To get the syntax highlighter to work, copy the [slab.sublime_syntax](https://raw.githubusercontent.com/increpare/slab-markup-sublime/master/slab.sublime_syntax) file to your Packages/User directory in Sublime Text.


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

(Which is basically the same as the SLAB version, and the libraries for parsing that are far more robust/numerous. So you should probably use that instead).

API
---

To parse a string, do

```
var slab = require("slab-markup")
var dat = slab.parse(myString)
```

To parse a file, do

```
var slab = require("slab-markup)
var dat = slab.parseFileSync('myfile.slab')
```

