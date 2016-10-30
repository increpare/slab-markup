custom data format - contains node code to parse one, and sublime text 3 syntax highlighting file

here's an example of a file:
```
name: Dot
description: none
uses: none
lines: none
triple: none
examples: 
	file: dotExample
	description: A dot sign is used to split lines 
			into multiple parts to allow aggregate 
			statements.
	translation: Person A is feeling good about 
      this new file format.

name: Identity
description: Used to indicate who the speaker is and who they are addressing.
uses: ABGH
lines:
	A has an identity
	You are B.
	I am G.
	Any H
triple: none
examples:
	file: personExample
	description: none
	translation: I am Person A you are Person B.
```
  
to parse it, just do 

var slab = require("./js/slab")
var db = slab.loadFile('myfile.slab');

(Warning, it doesn't support depths of >2 right now...)
