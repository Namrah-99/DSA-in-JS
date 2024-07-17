# Queue

A Queue Data Structure is a fundamental concept in computer science used for storing and managing data in a specific order. It follows the principle of **“First in, First out” (FIFO)**, where the first element added to the queue is the first one to be removed

## Operation on Queue:
- Enqueue: Adds an element to the rear of the queue
- Dequeue: Removes an element from the front of the queue
- Peek: Retrieves the front element without removing it
- IsEmpty: Checks if the queue is empty
- IsFull: Checks if the queue is full

## Type of Queue:
- Circular Queue: Last element connects to the first element
- Double-Ended Queue (Deque): Operations can be performed from both ends
- Priority Queue: Elements are arranged based on priority

## Applications of Queue:
- Job scheduling
- Message queuing
- Simulation modeling
- Data buffering

Get all the details in depth related to queue from "https://www.geeksforgeeks.org/introduction-to-queue-data-structure-and-algorithm-tutorials/"

## Implementation of Queue Data Structure:
Queue can be implemented using following data structures:
- Implementation of Queue using Arrays
- Implementation of Queue using Linked List

### Implementation of Queue using Arrays
```javascript
// Queue class
class Queue
{
    // Array is used to implement a Queue
    constructor()
    {
        this.items = [];
    }
    isEmpty()
    {
        // return true if the queue is empty.
        return this.items.length == 0;
    }
    enqueue(element)
    {    
        // adding element to the queue
        this.items.push(element);
        document.write(element + " enqueued to queue<br>");
    }
    dequeue()
    {
        // removing element from the queue
        // returns underflow when called 
        // on empty queue
        if(this.isEmpty())
            return "Underflow<br>";
        return this.items.shift();
    }
    front()
    {
        // returns the Front element of 
        // the queue without removing it.
        if(this.isEmpty())
            return "No elements in Queue<br>";
        return this.items[0];
    }
    rear()
    {
        // returns the Rear element of 
        // the queue without removing it.
        if(this.isEmpty())
            return "No elements in Queue<br>";
        return this.items[this.items.length-1];
    }
}

// creating object for queue class
var queue = new Queue();

// Adding elements to the queue
queue.enqueue(10);
queue.enqueue(20);
queue.enqueue(30);
queue.enqueue(40);

// queue contains [10, 20, 30, 40]
// removes 10
document.write(queue.dequeue() + " dequeued from queue<br>");

// queue contains [20, 30, 40]
// Front is now 20
document.write("Front item is " + queue.front() + "<br>");

// printing the rear element
// Rear is 40
document.write("Rear item is " + queue.rear() + "<br>");
```

### Implementation of Queue using Linked List
```javascript
class Node {
    constructor(data) {
        this.data = data;   // Data of the node
        this.next = null;   // Pointer to the next node
    }
}

class Queue {
    constructor() {
        this.front = null;   // Points to the front of the queue
        this.rear = null;    // Points to the rear of the queue
        this.size = 0;       // Size of the queue
    }

    // Method to add element to the queue (enqueue)
    enqueue(data) {
        const newNode = new Node(data);

        if (!this.front) {
            this.front = newNode;
        } else {
            this.rear.next = newNode;
        }

        this.rear = newNode;
        this.size++;
    }

    // Method to remove element from the queue (dequeue)
    dequeue() {
        if (!this.front) {
            return null;  // Queue is empty
        }

        const removedNode = this.front;
        this.front = this.front.next;

        if (!this.front) {
            this.rear = null;  // Queue is now empty
        }

        this.size--;

        return removedNode.data;
    }

    // Method to get the front element of the queue without removing it
    peek() {
        if (!this.front) {
            return null;  // Queue is empty
        }

        return this.front.data;
    }

    // Method to check if the queue is empty
    isEmpty() {
        return this.size === 0;
    }

    // Method to get the size of the queue
    getSize() {
        return this.size;
    }

    print() {
        if (!this.front) {
            console.log("Queue is empty.");
            return;
        }

        let current = this.front;
        const elements = [];

        while (current) {
            elements.push(current.data);
            current = current.next;
        }

        console.log("Queue:", elements.join(" -> "));
    }
}

const queue = new Queue();

queue.enqueue(10);
queue.enqueue(20);
queue.enqueue(30);

queue.print();  // Output: Queue: 10 -> 20 -> 30

queue.dequeue();
queue.dequeue();

queue.print();  // Output: Queue: 30

queue.dequeue();

queue.print();  // Output: Queue is empty.

```
