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


