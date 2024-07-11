# Singly Linked List
A collection of nodes where each node contains a data field and a reference (link) to the next node in the sequence.


- Consists of nodes where each node contains a `data` field and a reference to the `next` node in the node.
- The last node points to null, indicating the end of the list.
- Understand the `operations` on singly linked lists (traversal, searching, length determination, insertion, and deletion)

## Node Structure
- In a singly linked list, each node consists of two parts: `data` and a `pointer` to the next node. 
- The data part stores the actual information, while the pointer (or reference) part stores the address of the next node in the sequence.
- This structure allows nodes to be `dynamically linked` together, forming a `chain-like sequence`.
```javascript
// Definition of a Node in a singly linked list
class Node {
    constructor(data) {
    // Data part of the node
        this.data = data;   
        this.next = null;   
    }
}
```

## Operations on Singly Linked List
- Traversal
- Searching
- Length
- Insertion:
    - Insert at the beginning
    - Insert at the end
    - Insert at a specific position
- Deletion:
    - Delete from the beginning
    - Delete from the end
    - Delete a specific node

## Implementation

```javascript
class Node {
    constructor(value) {
        this.value = value;
        this.next = null;
    }
}

class LinkedList {
    constructor() {
        this.head = null;
        this.size = 0;
    }

    // Traverse the linked list
    traverse() {
        let current = this.head;
        while (current !== null) {
            console.log(current.value);
            current = current.next;
        }
    }

    // Search for a specific value
    search(value) {
        let current = this.head;
        while (current !== null) {
            if (current.value === value) {
                return true;
            }
            current = current.next;
        }
        return false;
    }

    // Get the length of the linked list
    getLength() {
        return this.size;
    }

    // Insert a node at the beginning
    insertAtBeginning(value) {
        const newNode = new Node(value);
        newNode.next = this.head;
        this.head = newNode;
        this.size++;
    }

    // Insert a node at the end
    insertAtEnd(value) {
        const newNode = new Node(value);
        if (this.head === null) {
            this.head = newNode;
        } else {
            let current = this.head;
            while (current.next !== null) {
                current = current.next;
            }
            current.next = newNode;
        }
        this.size++;
    }

    // Insert a node at a specific position
    insertAtPosition(value, position) {
        if (position < 0 || position > this.size) {
            throw new Error("Invalid position");
        }
        const newNode = new Node(value);
        if (position === 0) {
            newNode.next = this.head;
            this.head = newNode;
        } else {
            let current = this.head;
            let previous = null;
            let index = 0;
            while (index < position) {
                previous = current;
                current = current.next;
                index++;
            }
            newNode.next = current;
            previous.next = newNode;
        }
        this.size++;
    }

    // Delete a node from the beginning
    deleteFromBeginning() {
        if (this.head === null) {
            return;
        }
        this.head = this.head.next;
        this.size--;
    }

    // Delete a node from the end
    deleteFromEnd() {
        if (this.head === null) {
            return;
        }
        if (this.head.next === null) {
            this.head = null;
        } else {
            let current = this.head;
            let previous = null;
            while (current.next !== null) {
                previous = current;
                current = current.next;
            }
            previous.next = null;
        }
        this.size--;
    }

    // Delete a node with a specific value
    deleteNode(value) {
        if (this.head === null) {
            return;
        }
        if (this.head.value === value) {
            this.head = this.head.next;
        } else {
            let current = this.head;
            let previous = null;
            while (current !== null && current.value !== value) {
                previous = current;
                current = current.next;
            }
            if (current !== null) {
                previous.next = current.next;
            }
        }
        this.size--;
    }
}

// Example usage
const list = new LinkedList();
list.insertAtEnd(1);
list.insertAtEnd(2);
list.insertAtEnd(3);
list.insertAtBeginning(0);
list.insertAtPosition(1.5, 2);
list.traverse(); // Output: 0, 1, 1.5, 2, 3
console.log('Length:', list.getLength()); // Output: Length: 5
console.log('Search 2:', list.search(2)); // Output: Search 2: true
list.deleteFromBeginning();
list.deleteFromEnd();
list.deleteNode(1.5);
list.traverse(); // Output: 1, 2
console.log('Length:', list.getLength()); // Output: Length: 2
```

## Explanation
- Traversal: The traverse method prints the values of all nodes in the linked list.
- Searching: The search method checks if a specific value exists in the linked list.
- Length: The getLength method returns the number of nodes in the linked list.
- Insertion:
  - insertAtBeginning adds a new node at the start of the linked list.
  - insertAtEnd adds a new node at the end of the linked list.
  - insertAtPosition adds a new node at a specific position in the linked list.
- Deletion:
  - deleteFromBeginning removes the node at the start of the linked list.
  - deleteFromEnd removes the node at the end of the linked list.
  - deleteNode removes a node with a specific value from the linked list.

