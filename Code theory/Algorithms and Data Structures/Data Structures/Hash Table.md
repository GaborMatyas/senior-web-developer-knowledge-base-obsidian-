# Hash Table


Hash tables are used to store _key_-_value_ pairs.
So a key associated to a value for very quick lookups. 
They are like [[Array]], but the keys are not ordered.

As long as you have a hash function, generally anything can be used as a key.
A string, a circle, a square or anything. 

The hash function takes a string for example, as an input, converts into some sort of integer and it remaps that integer into an index into that array. The hashcode is not actually the index in this array, we are getting from the key, through the hashcode to the index. Basically this remap is necessary, because the hashcode can be 3 000 000 as well, but we do not want so big and long arrays, we remap this value into something smaller, a reasonable index.

Two different strings can have the same hashcode. Infinite number of strings exist, but only a finite number of hashcodes. This is the collision. 

When this happens, it can be handled with chaining. It is very simple and possibly the most common one. When there is a collision, we store the values in a [[Singly linked list]]. 

E.g.: we do not used an array of people, we use an array of linked lists of people. 
We produce a key, through the hash function we get the index of the linked list. We store the key with the value, so we can reveal the value of the current linked list with the current key. 


Unlike arrays, hash tables are `fast` for all of the following operations: 
- finding values, 
- adding new values,
- and removing values!

Nearly every programming language has some sort of hash table data structure
Because of their speed, hash tables are very commonly used!

In [[JavaScript]] these are the [[Objects]] and [[Map]]

