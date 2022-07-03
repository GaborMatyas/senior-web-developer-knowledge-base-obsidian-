## Casting of a variable
```rust
let a = 10;
let b = 3.0;
let c = a as f64 / b;
```
# Primitive Data Types
Each one can represent a simple scalar value. 

## Integer
It can be signed or unsigned. The length of the number can vary between 8 and 128 bit. By default it uses i32 signed integer.

To set a different type, the following syntax can be used (unsigned 8 bit integer):
`let x: u8 = 10;`

## Floating Point 
f32 and f64 are supported.
`let x = 10.1;`

The default is f64 and this is the suggested way, because it is not much slower than the 32bit and it has higher precision...but it can be modified to 32 bit with this syntax:
`let x: f32 = 10.1;`


## Boolean
With the traditional values `true(1)` or `false(0)`.
 
## Char
It is used to represent a singhe character. It is a unicode scalar value. 
It is stored using 4 bytes. 
Examples:
`let letter = 'a';`
`let number = 1;`
`let finger = '\u{261D}';`


# Compound Data Types
## Array 
Elements with the same data type. They have fixed size, you can not dynamically resaize an array in Rust. 
The first element has 0 index.
```rust
let letters = ['a', 'b', 'c'];

let mut mutableArray = ['a', 'b', 'c'];
mutableArray[0] = 'x'; // no the first element gets a new value but it must be the same data type 


let numbers: [i32; 5]; // define an array for 32 bit integers with 5 elements, without assigning an actual value 

numbers = [0; 5]; // initialize the array with 5 copies of value 0 
```
### Usize
When a variable is used to reach an index of an array, the variable type has to be 'usize'. This is necessary, because when the program compiles for a 32 bit system, the size of this type is 4 bytes, on 64 bit it is 8 bytes long.

```rust
let letters = ['a', 'b', 'c'];
let lastIndex: usize = letters.len()-1;
let lastElement = letters[lastIndex];
```