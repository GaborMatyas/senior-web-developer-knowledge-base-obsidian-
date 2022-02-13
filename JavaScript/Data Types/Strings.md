# Strings (text)
JavaScript's String type is used to represent textual data. It is a set of "elements" of 16-bit unsigned integer values. Each element in the String occupies a position in the String. The first element is at index `0`, the next at index `1`, and so on. The length of a String is the number of elements in it.

Unlike some programming languages (such as C), JavaScript strings are immutable. This means that once a string is created, it is not possible to modify it.

Examples
```js
	const string = 'Hi'
	const string = "Hi"
	const string = `Hi`
	const string = '' // empty string
```

-   A substring of the original by picking individual letters or using [`String.substr()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/substr).
-   A concatenation of two strings using the concatenation operator (`+`) or [`String.concat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/concat).

## Template strings
Template literals are enclosed by the backtick (` `) ([grave accent](https://en.wikipedia.org/wiki/Grave_accent)) character instead of double or single quotes.

```js
	// Untagged, these create strings:
	`string text`
	
	`string text line 1
	 string text line 2`
	
	`string text ${expression} string text`
	
	// Re-usable template:
	const templateFn = expression => `string text ${expression} string text`;
	
	// Tagged, this calls the function "example" with the template as the
	// first argument and substitution values as subsequent arguments:
	example`string text ${expression} string text`
```