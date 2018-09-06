---
layout: page
---
Truthy and falsy values are specific to variables, as non-boolean variables cannot be evaluated *exactly* as if they were boolean, but their contents can be evaluated as booleans based on truthy and falsy values instead.

For example, an empty string variable would evaluate to `false` in `if(variable)`, so the empty string is a falsy value.  Any other kind of string will be a truthy value.

Falsy values:

* `''` or `""` empty string
* `0` integer value
* `null`
* `undefined`
* `NaN` (not a number)

## Short-circuit evaluation

Like in bash, the left-hand side of a command is evaluated first, so you can use `||` to do a shorthand if-else statement.

```javascript
# Codecademy example!
let default = username || 'Stranger';
```

The above will assign the value of `username` to `default` if it exists, but if it doesn't exist, it will instead assign the string `'Stranger'`.
