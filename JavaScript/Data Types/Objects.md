# Objects

Complex values, more expensive to create and store them in the memory. They are tipically stored in the [[How is JavaScript Executed#Heap|heap]].

The [[Array]] and the [[Functions]] are also Objects in JavaScript. 

The variable itself a reference that stores a memory address where the object and its properties are available. When this variable is copied like:

```js
const object1 = {
	name: Melkor,
};

const object2 = object1;
```
only the address/reference has been copied. 

## Copying the properties of an object

A shallow copy can be created with the [[Spread operator]].
