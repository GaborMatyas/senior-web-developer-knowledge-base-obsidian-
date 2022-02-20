# Queues
This is a `FIFO` (first in first out) data structure.


## Application
- Printing / Task processing
- Background tasks


## Big O
##### When using linked list:
Insertion = O(1)
Removal = O(1)
Searching = O(n)
Access = O(n)


## Implementation
There are multiple ways of course, it could be used an [[Array]] or a Queue [[Class]] as well.
`Push` and `shift` array functions and `unshift` with `pop` array function pairs can be used to achieve this functionality, but these are not so performant solutions when there are couple of elements in the array.
```js
class Node {
    constructor(value){
        this.value = value;
        this.next = null;
    }
}

class Queue {
    constructor(){
        this.first = null;
        this.last = null;
        this.size = 0;
    }

	// add new value
    enqueue(val){
        let newNode = new Node(val);
        if(!this.first){
            this.first = newNode;
            this.last = newNode;
        } else {
            this.last.next = newNode;
            this.last = newNode;
        }
        return ++this.size;
    }

	// remove a value
    dequeue(){
        if(!this.first) return null;

        let temp = this.first;

        if(this.first === this.last) {
            this.last = null;
        }
	
        this.first = this.first.next;
        this.size--;
        return temp.value;
    }
}
```
