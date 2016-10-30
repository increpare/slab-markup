stupid custom data format - contains js code to parse, and sublime text 3 syntax highlighting file

here's an example of a file:

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
  
to parse it, just do 

```
var slab = require("./js/slab")
var db = slab.loadFile('myfile.slab');
```

and it will look like this:

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

Which is basically the same as the SLAB version, and has far more robust code.

(Warning, it doesn't support depths of >2 right now...)

To get the syntax highlighter to work, copy the .sublime-syntax file to your Packages/User directory in sublime text.

![Alt screenshot](sshot.png?raw=true)
