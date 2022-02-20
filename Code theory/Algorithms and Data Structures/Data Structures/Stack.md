# Stack

A `LIFO` (last in first out) data structure.

The last element added to the stack will be the first element removed from the stack. In Javascript, a good example of this kind of data strucure is the [[How is JavaScript Executed#A function execution process with the heap and the stack|Call Stack]]

## Application
- Managing function invocations
- Undo / Redo (e.g.: in Photoshop)
- Routing (the history object in React is treated like a stack)


## Big O
##### When using linked list:
Insertion = O(1)
Removal = O(1)
Searching = O(n)
Access = O(n)


## Implementation
There are multiple ways of course, it could be used an [[Array]] or a [[Singly linked list]] as well.
Push and pop function is the better options with an array, because they are O(1) operations. 
```js
// singly linked list implementation
class Node {
    constructor(value){
        this.value = value;
        this.next = null;
    }
}

class Stack {
    constructor(){
        this.first = null;
        this.last = null;
        this.size = 0;
    }

	// just use the shift and unshift method from the singly linked list implementation, because 
	// in this case we should work with the head, because the tail is not available directly
	// from a single linked list, only by iteration, so it would not be optimal
    push(val){
        let newNode = new Node(val);
        if(!this.first){
            this.first = newNode;
            this.last = newNode;
        } else {
            let temp = this.first;
            this.first = newNode;
            this.first.next = temp;
        }
        return ++this.size;
    }

    pop(){
        if(!this.first) return null;

        let temp = this.first;

        if(this.first === this.last){
            this.last = null;
        }
	
        this.first = this.first.next;
        this.size--;
        return temp.value;
    }
```
