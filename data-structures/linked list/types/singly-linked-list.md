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
    
    // Delete a node at a specific position
    deleteAtPosition(position) {
        // If the list is empty or the position is invalid
        if (this.head === null || position < 1) {
            return this.head;
        }
    
        // If the head needs to be deleted
        if (position === 1) {
            let temp = this.head;
            this.head = this.head.next;
            temp = null;
            this.size--;
            return this.head;
        }
    
        // Traverse to the node before the position to be deleted
        let current = this.head;
        for (let i = 1; i < position - 1 && current !== null; i++) {
            current = current.next;
        }
    
        // If the position is out of range
        if (current === null || current.next === null) {
            return this.head;
        }
    
        // Store the node to be deleted
        let temp = current.next;
    
        // Update the links to bypass the node to be deleted
        current.next = current.next.next;
    
        // Delete the node
        temp = null;
        this.size--;
        return this.head;
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
console.log('deleteAtPosition:', list.deleteAtPosition(2));
list.traverse(); // Output: 1
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
  - deleteAtPosition removes a node at a specific position in linked list.

## Edge Cases Handled with Code
- `traverse()`
    - Empty list: If the list is empty (this.head is null), the while loop condition current !== null prevents any action.
    ```javascript
    traverse() {
        let current = this.head;
        while (current !== null) {
            console.log(current.value);
            current = current.next;
        }
    }
    ```
- `search(value)`
    - Empty list: If the list is empty (this.head is null), the while loop condition current !== null prevents any action and the function returns false.
    - Non-existent value: If the value is not found in the list, the function returns false.
    ```javascript
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
    ```
- `getLength()`
- No special edge cases: This simply returns the size of the list which is maintained during insertion and deletion.
```javascript
getLength() {
    return this.size;
}
```
- `insertAtBeginning(value)`
    - Empty list: If this.head is null, the new node becomes the head of the list.
    - Non-empty list: The new node is added at the beginning and the previous head becomes the next node of the new node.
    ```javascript
    insertAtBeginning(value) {
        const newNode = new Node(value);
        newNode.next = this.head;
        this.head = newNode;
        this.size++;
    }
    ```
- `insertAtEnd(value)`
    - Empty list: If this.head is null, the new node becomes the head of the list.
    - Non-empty list: Traverses to the end of the list and adds the new node.
    ```javascript
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
    ```
- `insertAtPosition(value, position)`
    - Invalid position: Throws an error if position is less than 0 or greater than this.size.
    - Insertion at the beginning: Calls insertAtBeginning if position is 0.
    - Insertion at the end: Calls insertAtEnd if position equals this.size.
    - Insertion in the middle: Adjusts pointers of the new node and the nodes at position - 1 and position.
    ```javascript
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
    ```
- `deleteFromBeginning()`
    - Empty list: If this.head is null, simply returns.
    - Single element list: If this.head.next is null, sets this.head to null.
    - Multiple elements: Adjusts the head pointer to the next node.
    ```javascript
    deleteFromBeginning() {
        if (this.head === null) {
            return;
        }
        this.head = this.head.next;
        this.size--;
    }
    ```
- `deleteFromEnd()`
    - Empty list: If this.head is null, simply returns.
    - Single element list: If this.head.next is null, sets this.head to null.
    - Multiple elements: Traverses to the second-to-last node and sets its next to null.
    ```javascript
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
    ```
- `deleteNode(value)`
    - Empty list: If this.head is null, simply returns.
    - Node to be deleted is the head: If the head node matches the value, adjusts the head pointer to the next node.
    - Node to be deleted is in the middle or end: Traverses the list to find the node, adjusts pointers to bypass the node, and deletes the node.
    ```javascript
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
    ```
- `deleteAtPosition(position)`
    - Invalid position: If position is less than 1, simply returns the head.
    - Deletion at the beginning: If position is 1, adjusts the head pointer to the next node and deletes the current head.
    - Position out of range: If position is greater than the list size, simply returns the head.
    - Deletion in the middle or end: Traverses to the node before the position, adjusts pointers to bypass the node at position, and deletes the node.
    ```javascript
    deleteAtPosition(position) {
        if (this.head === null || position < 1) {
            return this.head;
        }
        
        if (position === 1) {
            let temp = this.head;
            this.head = this.head.next;
            temp = null;
            this.size--;
            return this.head;
        }
        
        let current = this.head;
        for (let i = 1; i < position - 1 && current !== null; i++) {
            current = current.next;
        }
        
        if (current === null || current.next === null) {
            return this.head;
        }
        
        let temp = current.next;
        current.next = current.next.next;
        temp = null;
        this.size--;
        return this.head;
    }
    ```

## Complexity Analysis
### Time Complexity
- Traversal (traverse)
        - Time Complexity: `O(n)`
        - Explanation: The method traverses all the nodes in the list, where n is the number of nodes.
- Search (search)
        - Time Complexity: `O(n)`
        - Explanation: In the worst case, the method searches through all nodes until it finds the target node or reaches the end of the list.
- Get Length (getLength)
        - Time Complexity: `O(1)`
        - Explanation: The length is stored in a variable and returned directly.

- Insertion
    - Insert at the Beginning (insertAtBeginning)
        - Time Complexity: `O(1)`
        - Explanation: The new node is inserted directly at the head of the list.
    - Insert at the End (insertAtEnd)
        - Time Complexity: `O(n)`
        - Explanation: In the worst case, the method traverses the entire list to insert the node at the end.
    - Insert at a Specific Position (insertAtPosition)
        - Time Complexity: `O(n)`
        - Explanation: In the worst case, the method traverses the list to the specified position.

- Deletion
    - Delete from the Beginning (deleteFromBeginning)
        - Time Complexity: `O(1)`
        - Explanation: The head node is removed directly.
    - Delete from the End (deleteFromEnd)
        - Time Complexity: `O(n)`
        - Explanation: In the worst case, the method traverses the entire list to find and remove the last node.
    - Delete a Specific Node (deleteNode)
        - Time Complexity: `O(n)`
        - Explanation: In the worst case, the method traverses the entire list to find the node with the specified value.
    - Delete at a Specific Position (deleteAtPosition)
        - Time Complexity: `O(n)`
        - Explanation: In the worst case, the method traverses the entire list to reach the specified position.
### Space Complexity
- Overall Space Complexity: `O(n)`
- Explanation: The space complexity is `O(n)` for storing n nodes in the list, where each node occupies constant space.
