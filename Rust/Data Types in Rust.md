## Integer
It can be signed or unsigned. The length of the number can vary between 8 and 128 bit. By default it uses i32 signed integer.

To set a different type, the following syntax can be used (unsigned 8 bit integer):
`let x: u8 = 10;`

## Floating Point 
f32 and f64 are supported.
`let x = 10.1;`

The default is f64 and this is the suggested way, because it is not much slower than the 32bit and it has higher precision...but it can be modified to 32 bit with this syntax:
`let x: f32 = 10.1;`


