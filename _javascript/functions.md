---
layout: page
---
Lots of ways to create a function:

* Function declaration
* Function expression

## Function declaration

Start off saying it's a function that you're going to be defining (using the `function` keyword), then give the function a name (an "identifier") and its parameters in parentheses, and follow up with the function body in curly brackets.

```javascript
function doStuff(parameter = default_value) {
	stuff;
}
```

## Function expression

Where the `function` keyword is used without an identifier on the right-hand side of an expression.  The functions created in these cases are *anonymous functions*, for obvious reasons.

```javascript
const variableName = function(param, otherparam) {
	const newVariable = param * otherparam;
	return newVariable;
}



## Notes

**Hoisting** is technically allowed in JavaScript, where you can call a function before it's been defined using the `function` keyword, but it's considered *bad practice*, so don't do it!
