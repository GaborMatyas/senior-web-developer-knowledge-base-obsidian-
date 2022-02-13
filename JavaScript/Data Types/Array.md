# Array
Arrays are list-like objects whose prototype has methods to perform traversal and mutation operations. 

Neither the length of a JavaScript array nor the types of its elements are fixed. 

Since an array's length can change at any time, and data can be stored at non-contiguous locations in the array, JavaScript arrays are not guaranteed to be dense; this depends on how the programmer chooses to use them. 

In general, these are convenient characteristics; but if these features are not desirable for your particular use, you might consider using typed arrays.

Arrays cannot use strings as element indexes (as in an [associative array](https://en.wikipedia.org/wiki/Associative_array)) but must use integers.


## [Common operations](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#common_operations "Permalink to Common operations")

**Create an Array**

```
let fruits = ['Apple', 'Banana']

console.log(fruits.length)
// 2
```

**Access an Array item using the index position**

```
let first = fruits[0]
// Apple

let last = fruits[fruits.length - 1]
// Banana
```

**Loop over all elements of an Array**

```
fruits.forEach(function(item, index, array) {
  console.log(item, index)
})
// Apple 0
// Banana 1
```

**Add an item to the end of an Array**

```
let newLength = fruits.push('Orange')
// ["Apple", "Banana", "Orange"]
```

**Remove an item from the end of an Array**

```
let last = fruits.pop() // remove Orange (from the end)
// ["Apple", "Banana"]
```

**Remove an item from the beginning of an Array**

```
let first = fruits.shift() // remove Apple from the front
// ["Banana"]
```

**Add an item to the beginning of an Array**

```
let newLength = fruits.unshift('Strawberry') // add to the front
// ["Strawberry", "Banana"]
```

**Find the index of an item in the Array**

```
fruits.push('Mango')
// ["Strawberry", "Banana", "Mango"]

let pos = fruits.indexOf('Banana')
// 1
```

**Remove an item by index position**

```
let removedItem = fruits.splice(pos, 1) // this is how to remove an item

// ["Strawberry", "Mango"]
```

**Remove items from an index position**

```
let vegetables = ['Cabbage', 'Turnip', 'Radish', 'Carrot']
console.log(vegetables)
// ["Cabbage", "Turnip", "Radish", "Carrot"]

let pos = 1
let n = 2

let removedItems = vegetables.splice(pos, n)
// this is how to remove items, n defines the number of items to be removed,
// starting at the index position specified by pos and progressing toward the end of array.

console.log(vegetables)
// ["Cabbage", "Carrot"] (the original array is changed)

console.log(removedItems)
// ["Turnip", "Radish"]
```

### Copy an Array

**Shallow copy** using [spread sequence](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax):

```
let shallowCopySpread = [...fruits]
// ["Strawberry", "Mango"]
```

Shallow copy using [`Array.slice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice):

```
let shallowCopySlice = fruits.slice()
// ["Strawberry", "Mango"]
```

Shallow copy using [`Array.from()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from):

```
let shallowCopyFrom = Array.from(fruits)
// ["Strawberry", "Mango"]
```

**Deep copy**

If you need a [_deep copy_](https://developer.mozilla.org/en-US/docs/Glossary/Deep_copy) of all elements — that is, in which even nested arrays don’t just reference elements in the original array but instead are also copied — one approach is to use [`JSON.stringify()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify) to convert the array to a JSON string, and then [`JSON.parse()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse) to convert the string back into an array.

```
let deepCopy = JSON.parse(JSON.stringify(fruits));
// ["Strawberry", "Mango"]
```

## Static methods of Array class
[`Array.from()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)

Creates a new `Array` instance from an array-like or iterable object.

[`Array.isArray()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/isArray)

Returns `true` if the argument is an array, or `false` otherwise.

[`Array.of()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/of)

Creates a new `Array` instance with a variable number of arguments, regardless of number or type of the arguments.


## Instance methods

[`Array.prototype.at()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/at)

Returns the array item at the given index. Accepts negative integers, which count back from the last item.

[`Array.prototype.concat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)

Returns a new array that is this array joined with other array(s) and/or value(s).

[`Array.prototype.copyWithin()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin)

Copies a sequence of array elements within the array.

[`Array.prototype.entries()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/entries)

Returns a new _array iterator_ object that contains the key/value pairs for each index in the array.

[`Array.prototype.every()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every)

Returns `true` if every element in this array satisfies the testing function.

[`Array.prototype.fill()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)

Fills all the elements of an array from a start index to an end index with a static value.

[`Array.prototype.filter()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

Returns a new array containing all elements of the calling array for which the provided filtering function returns `true`.

[`Array.prototype.find()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)

Returns the found `element` in the array, if some element in the array satisfies the testing function, or `undefined` if not found.

[`Array.prototype.findIndex()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

Returns the found index in the array, if an element in the array satisfies the testing function, or `-1` if not found.

[`Array.prototype.flat()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)

Returns a new array with all sub-array elements concatenated into it recursively up to the specified depth.

[`Array.prototype.flatMap()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap)

Returns a new array formed by applying a given callback function to each element of the array, and then flattening the result by one level.

[`Array.prototype.forEach()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

Calls a function for each element in the array.

[`Array.prototype.includes()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)

Determines whether the array contains a value, returning `true` or `false` as appropriate.

[`Array.prototype.indexOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)

Returns the first (least) index of an element within the array equal to an element, or `-1` if none is found.

[`Array.prototype.join()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

Joins all elements of an array into a string.

[`Array.prototype.keys()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/keys)

Returns a new _array iterator_ that contains the keys for each index in the array.

[`Array.prototype.lastIndexOf()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/lastIndexOf)

Returns the last (greatest) index of an element within the array equal to an element, or `-1` if none is found.

[`Array.prototype.map()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

Returns a new array containing the results of calling a function on every element in this array.

[`Array.prototype.pop()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/pop)

Removes the last element from an array and returns that element.

[`Array.prototype.push()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/push)

Adds one or more elements to the end of an array, and returns the new `length` of the array.

[`Array.prototype.reduce()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Reduce)

Apply a function against an accumulator and each value of the array (from left-to-right) as to reduce it to a single value.

[`Array.prototype.reduceRight()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduceRight)

Apply a function against an accumulator and each value of the array (from right-to-left) as to reduce it to a single value.

[`Array.prototype.reverse()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse)

Reverses the order of the elements of an array _in place_. (First becomes the last, last becomes first.)

[`Array.prototype.shift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/shift)

Removes the first element from an array and returns that element.

[`Array.prototype.slice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

Extracts a section of the calling array and returns a new array.

[`Array.prototype.some()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some)

Returns `true` if at least one element in this array satisfies the provided testing function.

[`Array.prototype.sort()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

Sorts the elements of an array in place and returns the array.

[`Array.prototype.splice()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

Adds and/or removes elements from an array.

[`Array.prototype.toLocaleString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/toLocaleString)

Returns a localized string representing the array and its elements. Overrides the [`Object.prototype.toLocaleString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toLocaleString) method.

[`Array.prototype.toString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/toString)

Returns a string representing the array and its elements. Overrides the [`Object.prototype.toString()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/toString) method.

[`Array.prototype.unshift()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/unshift)

Adds one or more elements to the front of an array, and returns the new `length` of the array.

[`Array.prototype.values()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/values)

Returns a new _array iterator_ object that contains the values for each index in the array.

[`Array.prototype[@@iterator]()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/@@iterator)

Returns a new _array iterator_ object that contains the values for each index in the array.