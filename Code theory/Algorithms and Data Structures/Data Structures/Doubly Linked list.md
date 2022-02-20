# Doubly Linked list
It needs more memory but provides greater flexibility than the [[Singly linked list]].

![[Pasted image 20220220142722.png]]

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
        this.prev = null;
    }
}


class DoublyLinkedList {
    constructor(){
        this.head = null;
        this.tail = null;
        this.length = 0;
    }

    // inserting a new value at the end (after the tail)
    push(val){
        let newNode = new Node(val);
        if(this.length === 0){
            this.head = newNode;
            this.tail = newNode;
        } else {
            this.tail.next = newNode;
            newNode.prev = this.tail;
            this.tail = newNode;
        }
        this.length++;
        return this;
    }

    // removing a node from the end
    pop(){
        if(!this.head) return undefined;

        let poppedNode = this.tail;

        if(this.length === 1){
            this.head = null;
            this.tail = null;
        } else {
            this.tail = poppedNode.prev;
            this.tail.next = null;
            poppedNode.prev = null;
        }

        this.length--;

        return poppedNode;
    }

    // removing a node from the beginning of the linked list
    shift(){
        if(this.length === 0) return undefined;

        let oldHead = this.head;

        if(this.length === 1){
            this.head = null;
            this.tail = null;
        }else{
            this.head = oldHead.next;
            this.head.prev = null;
            oldHead.next = null;
        }
        this.length--;
        return oldHead;
    }

    // add a new node to the beginning of the linked list
    unshift(val){
        let newNode = new Node(val);
        if(this.length === 0) {
            this.head = newNode;
            this.tail = newNode;
        } else {
            this.head.prev = newNode;
            newNode.next = this.head;
            this.head = newNode;
        }
        this.length++;
        return this;
    }

    // return the value in the provided index position
    get(index){
        if(index < 0 || index >= this.length) return null;

        let count, current;

        if(index <= this.length/2){
            count = 0;
            current = this.head;
            while(count !== index){
                current = current.next;
                count++;
            }

        } else {

            count = this.length - 1;
            current = this.tail;
            while(count !== index){
                current = current.prev;
                count--;
            }
        }
        return current;
    }

    // set the provided value at the concrete index position
    set(index, val){
        let foundNode = this.get(index);
        if(foundNode != null){
            foundNode.val = val;
            return true;
        }
        return false;
    }

    // // adding a node to the linked list at a specific position
    insert(index, val){
        if(index < 0 || index > this.length) {
            return false;
        }

        if(index === 0) {
            return !!this.unshift(val);
        }

        if(index === this.length) {
            return !!this.push(val);
        }

        let newNode = new Node(val);
        let beforeNode = this.get(index-1);
        let afterNode = beforeNode.next;

        beforeNode.next = newNode;

        newNode.prev = beforeNode;
        newNode.next = afterNode;

        afterNode.prev = newNode;
        this.length++;
        return true;
    }
}

let list = new DoublyLinkedList()
```
