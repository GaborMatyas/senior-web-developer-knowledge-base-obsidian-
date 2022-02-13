# Spread operator
**Spread syntax** (`...`) allows an iterable such as an array expression or string to be expanded in places where zero or more arguments (for function calls) or elements (for array literals) are expected, or an object expression to be expanded in places where zero or more key-value pairs (for object literals) are expected.

Spread syntax can be used when all elements from an object or array need to be included in a list of some kind.

## [Syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax#syntax "Permalink to Syntax")

For function calls:

```
myFunction(...iterableObj); // pass all elements of iterableObj as arguments to function myFunction
```

For array literals:

```
[...iterableObj, '4', 'five', 6]; // combine two arrays by inserting all elements from iterableObj
```

For object literals (new in ECMAScript 2018):

```
let objClone = { ...obj }; // pass all key:value pairs from an object 
```