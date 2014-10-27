# Javascript Code Conventions

## Use strict

`'use strict'`

* [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode) 

* [http://ejohn.org/blog/ecmascript-5-strict-mode-json-and-more/](http://ejohn.org/blog/ecmascript-5-strict-mode-json-and-more/) 

## Spacing

(jQuery)

Your code need to breathe. check this out: http://contribute.jquery.org/style-guide/js/#bad-examples

space after each comma, and after opening parenthesis, before closing parenthesis

var functionName = function( arg1, arg2, arg3 ) { }

## Return statements

Absolutely avoid directly returning:

* **functions declarations**: return (function() { … })()

* **non JSON literals **containing function calls return {a:getA(), b:3, c: buildC(getA(),getB())}

* **ternary expression**. return isValid() ? getValue() : ‘invalid’

and avoid:

* **functions calls**

* **Expressions with booleans operators **( || , && )

Those are a nightmare to debug and is unfortunately commonly seen in popular frameworks (jQuery, especially).

### terrible examples:

This is problematic:

`return this.pushStack( jQuery.unique( jQuery.merge(`

`	this.get(),`

`	typeof selector === "string" ?`

`		jQuery( selector ) :`

`		jQuery.makeArray( selector )`

`)));`

how one can rephrase that code into this:

`var selection = typeof selector === "string" ?`

`	jQuery( selector ) :`

`	jQuery.makeArray( selector );`

`var toBePushed = jQuery.unique( jQuery.merge(`

`	this.get(),`

`	selection`

`));`

`var pushedStack = this.pushStack( toBePushed );`

`return pushedStack;`

`//The avantage of writing this way is you can easily debug and see`

`//the result of each individual expression.`

`//How to tell what ‘toBePushed’ is in the previous example ?`

	

Another messy example with ternary expressions mixed up with function calls mixed up with default operators (||). When you try to inspect this it’s really hard to tell where we are in the expression. Also, good luck tracking exceptions in something like this:

`return table && jQuery.nodeName(elem, "table") && jQuery.nodeName(cur, "tr") ?`

`	(elem.getElementsByTagName("tbody")[0] ||`

`	elem.appendChild(elem.ownerDocument.createElement("tbody"))) :`

`	elem;`

## Comparisons

# URL Design

You have to follow some guidelines regarding how you design your backend HTTP API (may it be RESTful or not). But it also applies to your webapp’s routes.

You can check out these resources.

* [http://stackoverflow.com/questions/778203/are-there-any-naming-convention-guidelines-for-rest-apis](http://stackoverflow.com/questions/778203/are-there-any-naming-convention-guidelines-for-rest-apis)

* [http://stackoverflow.com/questions/1619152/how-to-create-rest-urls-without-verbs#1619677](http://stackoverflow.com/questions/1619152/how-to-create-rest-urls-without-verbs#1619677)

* [http://blog.2partsmagic.com/restful-uri-design/](http://blog.2partsmagic.com/restful-uri-design/)


