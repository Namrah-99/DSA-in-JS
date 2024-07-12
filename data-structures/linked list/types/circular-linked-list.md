# Circular Singly Linked List
The circular linked list is a linked list where all nodes are connected to form a circle. In a circular linked list, the first node and the last node are connected to each other which forms a circle. There is no NULL at the end.

In a circular Singly linked list, the last node of the list contains a pointer to the first node of the list. We traverse the circular singly linked list until we reach the same node where we started. The circular singly linked list has no beginning or end. No null value is present in the next part of any of the nodes.

## Node Structure
```javascript
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
  }
}
```

## Operations:

- Searching in Circular Linked List
- Finding Length of Circular Linked List
- Insertion at the beginning, end, and a specific position
- Deletion from the beginning, end, and a specific position
- Traversal in Circular Linked List

## Implementation
```javascript
class Node {
    constructor(value) {
        this.value = value;
        this.next = null;
    }
}

class CircularLinkedList {
    constructor() {
        this.head = null;
        this.size = 0;
    }

    // Searching in Circular Linked List
    search(value) {
        if (this.head === null) return false;
        let current = this.head;
        do {
            if (current.value === value) {
                return true;
            }
            current = current.next;
        } while (current !== this.head);
        return false;
    }

    // Finding Length of Circular Linked List
    getLength() {
        return this.size;
    }

    // Insertion at the beginning of Circular Linked List
    insertAtBeginning(value) {
        const newNode = new Node(value);
        if (this.head === null) {
            newNode.next = newNode;
            this.head = newNode;
        } else {
            let current = this.head;
            while (current.next !== this.head) {
                current = current.next;
            }
            newNode.next = this.head;
            current.next = newNode;
            this.head = newNode;
        }
        this.size++;
    }

    // Insertion at the end of Circular Linked List
    insertAtEnd(value) {
        const newNode = new Node(value);
        if (this.head === null) {
            newNode.next = newNode;
            this.head = newNode;
        } else {
            let current = this.head;
            while (current.next !== this.head) {
                current = current.next;
            }
            current.next = newNode;
            newNode.next = this.head;
        }
        this.size++;
    }

    // Insertion at a specific position in Circular Linked List
    insertAtPosition(value, position) {
        if (position < 0 || position > this.size) {
            throw new Error("Invalid position");
        }
        if (position === 0) {
            this.insertAtBeginning(value);
        } else if (position === this.size) {
            this.insertAtEnd(value);
        } else {
            const newNode = new Node(value);
            let current = this.head;
            let index = 0;
            while (index < position - 1) {
                current = current.next;
                index++;
            }
            newNode.next = current.next;
            current.next = newNode;
            this.size++;
        }
    }

    // Deletion of a node at the beginning of Circular Linked List
    deleteFromBeginning() {
        if (this.head === null) return;
        if (this.head.next === this.head) {
            this.head = null;
        } else {
            let current = this.head;
            while (current.next !== this.head) {
                current = current.next;
            }
            current.next = this.head.next;
            this.head = this.head.next;
        }
        this.size--;
    }

    // Deletion of a node at the end of Circular Linked List
    deleteFromEnd() {
        if (this.head === null) return;
        if (this.head.next === this.head) {
            this.head = null;
        } else {
            let current = this.head;
            let previous = null;
            while (current.next !== this.head) {
                previous = current;
                current = current.next;
            }
            previous.next = this.head;
        }
        this.size--;
    }

    // Deletion of a node at a specific position in Circular Linked List
    deleteAtPosition(position) {
        if (position < 0 || position >= this.size) {
            throw new Error("Invalid position");
        }
        if (position === 0) {
            this.deleteFromBeginning();
        } else if (position === this.size - 1) {
            this.deleteFromEnd();
        } else {
            let current = this.head;
            let index = 0;
            while (index < position - 1) {
                current = current.next;
                index++;
            }
            current.next = current.next.next;
            this.size--;
        }
    }

    // Traversal in Circular Linked List
    traverse() {
        if (this.head === null) return;
        let current = this.head;
        do {
            console.log(current.value);
            current = current.next;
        } while (current !== this.head);
    }
}

// Example usage
const list = new CircularLinkedList();
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
list.traverse(); // Output: 1, 1.5, 2
list.deleteAtPosition(1);
list.traverse(); // Output: 1, 2
console.log('Length:', list.getLength()); // Output: Length: 2
```

## Edge Cases for Each Operation
- `search(value)`
  - List is empty: Immediately returns false since there are no nodes to search.
  - Element not found: Traverses the entire list and returns false if the value is not found.
  ```javascript
    search(value) {
        if (this.head === null) return false;
        let current = this.head;
        do {
            if (current.value === value) {
                return true;
            }
            current = current.next;
        } while (current !== this.head);
        return false;
    }
  ```
- `getLength()`
  - No specific edge cases; it simply returns the size of the list.
  ```javascript
    getLength() {
        return this.size;
    }
  ```
- `insertAtBeginning(value)`
  - List is empty: Sets the new node's next to itself and assigns it as the head.
  - List is not empty: Updates the head pointer and adjusts the last node's next pointer.
  ```javascript
    insertAtBeginning(value) {
        const newNode = new Node(value);
        if (this.head === null) {
            newNode.next = newNode;
            this.head = newNode;
        } else {
            let current = this.head;
            while (current.next !== this.head) {
                current = current.next;
            }
            newNode.next = this.head;
            current.next = newNode;
            this.head = newNode;
        }
        this.size++;
    }
  ```
- `insertAtEnd(value)`
  - List is empty: Sets the new node's next to itself and assigns it as the head.
  - List is not empty: Traverses to the end and updates pointers to include the new node.
  ```javascript
    insertAtEnd(value) {
        const newNode = new Node(value);
        if (this.head === null) {
            newNode.next = newNode;
            this.head = newNode;
        } else {
            let current = this.head;
            while (current.next !== this.head) {
                current = current.next;
            }
            current.next = newNode;
            newNode.next = this.head;
        }
        this.size++;
    }
  ```
- `insertAtPosition(value, position)`
  - Invalid position: Throws an error if the position is out of range.
  - Insert at the beginning: Uses insertAtBeginning method.
  - Insert at the end: Uses insertAtEnd method.
  - Insert in the middle: Traverses to the specified position and updates pointers.
  ```javascript
    insertAtPosition(value, position) {
        if (position < 0 || position > this.size) {
            throw new Error("Invalid position");
        }
        if (position === 0) {
            this.insertAtBeginning(value);
        } else if (position === this.size) {
            this.insertAtEnd(value);
        } else {
            const newNode = new Node(value);
            let current = this.head;
            let index = 0;
            while (index < position - 1) {
                current = current.next;
                index++;
            }
            newNode.next = current.next;
            current.next = newNode;
            this.size++;
        }
    }
  ```
- `deleteFromBeginning()`
  - List is empty: Simply returns as there are no nodes to delete.
  - Only one node: Sets the head to null.
  - Multiple nodes: Updates the head pointer and adjusts the last node's next pointer.
  ```javascript
    deleteFromBeginning() {
        if (this.head === null) return;
        if (this.head.next === this.head) {
            this.head = null;
        } else {
            let current = this.head;
            while (current.next !== this.head) {
                current = current.next;
            }
            current.next = this.head.next;
            this.head = this.head.next;
        }
        this.size--;
    }
  ```
- `deleteFromEnd()`
  - List is empty: Simply returns as there are no nodes to delete.
  - Only one node: Sets the head to null.
  - Multiple nodes: Traverses to the end and updates pointers to exclude the last node.
  ```javascript
    deleteFromEnd() {
        if (this.head === null) return;
        if (this.head.next === this.head) {
            this.head = null;
        } else {
            let current = this.head;
            let previous = null;
            while (current.next !== this.head) {
                previous = current;
                current = current.next;
            }
            previous.next = this.head;
        }
        this.size--;
    }
  ```
- `deleteAtPosition(position)`
  - Invalid position: Throws an error if the position is out of range.
  - Delete at the beginning: Uses deleteFromBeginning method.
  - Delete at the end: Uses deleteFromEnd method.
  - Delete in the middle: Traverses to the specified position and updates pointers.
  ```javascript
    deleteAtPosition(position) {
        if (position < 0 || position >= this.size) {
            throw new Error("Invalid position");
        }
        if (position === 0) {
            this.deleteFromBeginning();
        } else if (position === this.size - 1) {
            this.deleteFromEnd();
        } else {
            let current = this.head;
            let index = 0;
            while (index < position - 1) {
                current = current.next;
                index++;
            }
            current.next = current.next.next;
            this.size--;
        }
    }
  ```
- `traverse()`
  - List is empty: Simply returns as there are no nodes to traverse.
  - List is not empty: Traverses and prints all nodes' values.
  ```javascript
    traverse() {
        if (this.head === null) return;
        let current = this.head;
        do {
            console.log(current.value);
            current = current.next;
        } while (current !== this.head);
    }
  ```

## Complexity Analysis
- Insertion at Beginning/End: `O(n)`
  - Because you need to find the last node to make the circular connection.
- Insertion at Specific Position: `O(n)`
  - Traversing to the specific position takes linear time.
- Deletion from Beginning/End: `O(n)`
  - Finding the node before the head to update the link to the new head.
- Deletion from Specific Position: `O(n)`
  - Traversing to the specific position takes linear time.
- Searching: `O(n)`
  - Traversing the list to find the value takes linear time.
- Finding Length: `O(1)`
  - The size is maintained as a property.
- Traversal: `O(n)`
  - Visiting each node exactly once.

This complexity analysis highlights the efficiency of various operations in a circular linked list, where most operations require linear time due to the need to traverse the list.
