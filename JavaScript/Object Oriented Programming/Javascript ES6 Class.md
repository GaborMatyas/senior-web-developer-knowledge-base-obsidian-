# Javascript ES6 Class


An important difference between **function declarations** and **class declarations** is that while functions can be called in code that appears before they are defined, classes must be defined before they can be constructed, or it will throw a ReferenceError. 

The class keyword creates a `constant` so you can not redefine it. 
```js

// definition
class Rectangle {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }
}

// intentiate
let firstRectangle = new Rectangle(2, 3);
```


## Instance Methods


## Static Methods
Static methods are called without instantiating their class and cannot be callled though a class instance. 

```js

// definition
class Rectangle {
	constructor(height, width) {
		this.height = height;
		this.width = width;
	}
	static calcArea(param1, param2) {
		//.....
	}
}

Rectangle.calcArea(2,4);

```