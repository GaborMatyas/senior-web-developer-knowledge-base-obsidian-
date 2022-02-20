# Singly Linked List

Linked Lists consist of nodes, and each node has a value and a pointer to another node or null.
**Random access is not allowed** but the insertion and deletion is **NOT** expensive like with arrays.
`Use them when you care about the insertion and deletion speed. `

The data structure contains a head, tail and length property.
We do not have indexes, to reach one particular element in the list. We start at the head(first element) and moving forward to the next element and so on and so on....until the tail (the last element).

![[Pasted image 20220220134647.png]]


## Big O
Insertion = O(1)
Removal = it depends O(1) or O(n)
Searching = O(n)
Access = O(n)


## Implementation
```js
class Node{
    constructor(val){
        this.val = val;
        this.next = null;
    }
}

class SinglyLinkedList{
    constructor(){
        this.head = null;
        this.tail = null;
        this.length = 0;
    }

	// inserting a new value at the end (after the tail)
    push(val){
        let newNode = new Node(val);
        if(!this.head){
            this.head = newNode;
            this.tail = this.head;
        } else {
            this.tail.next = newNode;
            this.tail = newNode;
        }
        this.length++;
        return this;
    }

	// removing a node from the end
    pop(){
        if(!this.head) {
			return undefined;
		}

        let current = this.head;
        let newTail = current;

        while(current.next){
            newTail = current;
            current = current.next;
        }

        this.tail = newTail;
        this.tail.next = null;
        this.length--;

        if(this.length === 0){
            this.head = null;
            this.tail = null;
        }

        return current;
    }

	// removing a node from the beginning of the linked list
    shift(){
        if(!this.head) {
			return undefined;
		}

        let currentHead = this.head;
        this.head = currentHead.next;
        this.length--;
        if(this.length === 0){
            this.tail = null;
        }
        return currentHead;
    }

	// add a new node to the beginning of the linked list
    unshift(val){
        let newNode = new Node(val);
        if(!this.head) {
            this.head = newNode;
            this.tail = this.head;
        }

        newNode.next = this.head;

        this.head = newNode;
        this.length++;
        return this;
    }

	// return the value in the provided index position
    get(index){
        if(index < 0 || index >= this.length) {
			return null;
		};

        let counter = 0;
        let current = this.head;

        while(counter !== index){
            current = current.next;
            counter++;
        }
        return current;
    }

	// set the provided value at the concrete index position
	set(index, val){
        let foundNode = this.get(index);
        if(foundNode){
            foundNode.val = val;
            return true;
        }
        return false;
    }

	// adding a node to the linked list at a specific position
    insert(index, val){
        if(index < 0 || index > this.length) {
			return false;
		};

        if(index === this.length) {
			return !!this.push(val);
		}

        if(index === 0) {
			return !!this.unshift(val);
		}

        let newNode = new Node(val);
        let prev = this.get(index - 1);
        let temp = prev.next;
        prev.next = newNode;
        newNode.next = temp;
        this.length++;
        return true;
    }

	// removing a node from the linked list at a specific position
    remove(index){
        if(index < 0 || index >= this.length) {
			return undefined;
		}

        if(index === 0) {
			return this.shift();
		}

        if(index === this.length - 1) {
			return this.pop();
		}

        let previousNode = this.get(index - 1);
        let removed = previousNode.next;

        previousNode.next = removed.next;

        this.length--;
        return removed;
    }

	// reversing the linked list in place
    reverse(){
      let node = this.head;

      this.head = this.tail;
      this.tail = node;

      let next;
      let prev = null;

      for(let i = 0; i < this.length; i++){
        next = node.next;
        node.next = prev;
        prev = node;
        node = next;
      }
      return this;
    }

	// print the values as an array
    print(){
        let arr = [];
        let current = this.head
        while(current){
            arr.push(current.val)
            current = current.next
        }
        console.log(arr);
    }
}

// instantiation
const list = new SinglyLinkedList()

```

## Searching
We are starting with the first element, and then the second and the third and check the value in the nodes. Once we find the value, `true` will be returned, or the algorithm hits the tails without any much, it returns `false`.

## Insertion
If we want to insert a new element into position 4, with the value 90...
We are starting from the head, iterating through the nodes until we find the correct position.
If the goal is to insert something to the first postion, just set a new head, and point it to the previous head, which in this case will be our new second element.
