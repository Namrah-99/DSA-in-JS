# WeakSet in JavaScript

WeakSet is a collection of objects, where the objects are held weakly. This means that if there are no other references to an object stored in the WeakSet, the object can be garbage collected.

## Characteristics

1. **Weak References**: Objects in a WeakSet are held weakly, meaning they do not prevent garbage collection.
2. **Only Objects**: WeakSet can only store objects, not primitive values.
3. **Non-Enumerable**: WeakSet is not enumerable, meaning there is no way to list the items in a WeakSet.
4. **No Duplicates**: Each object in a WeakSet must be unique.

## Common Operations and Their Complexities

1. **Creation**
   - **Description**: Initialize a new WeakSet.
   - **Syntax**: `let weakSet = new WeakSet();`
   - **Time Complexity**: O(1)
   - **Space Complexity**: O(n) (n is the number of elements)

2. **Adding Elements**
   - **Description**: Add a new object to the WeakSet.
   - **Syntax**: `weakSet.add(obj);`
   - **Time Complexity**: O(1)
   - **Space Complexity**: O(1) (additional space for new elements)

3. **Checking for Elements**
   - **Description**: Check if an object is in the WeakSet.
   - **Syntax**: `weakSet.has(obj);`
   - **Time Complexity**: O(1)
   - **Space Complexity**: O(1)

4. **Deleting Elements**
   - **Description**: Remove an object from the WeakSet.
   - **Syntax**: `weakSet.delete(obj);`
   - **Time Complexity**: O(1)
   - **Space Complexity**: O(1)

## Additional Points to Note

1. **Garbage Collection**: The primary advantage of WeakSet is that it allows objects to be garbage collected if there are no other references to them. This is particularly useful for managing memory in scenarios where objects are used temporarily.
2. **No Iteration**: Unlike Set, WeakSet does not provide a way to iterate over its elements. This is because the elements are held weakly and can be garbage collected at any time.
3. **Use Cases**: WeakSets are useful for storing objects that you want to track, but allow them to be garbage collected if they are no longer needed elsewhere in the program.

## Example Usage

```javascript
// Creating a new WeakSet
let weakSet = new WeakSet();

let obj1 = {name: "John"};
let obj2 = {name: "Doe"};

// Adding elements
weakSet.add(obj1);
weakSet.add(obj2);

// Checking for elements
console.log(weakSet.has(obj1)); // Output: true
console.log(weakSet.has({name: "John"})); // Output: false (different object reference)

// Deleting elements
weakSet.delete(obj2);
console.log(weakSet.has(obj2)); // Output: false

// Garbage collection
obj1 = null; // obj1 may be garbage collected if there are no other references to it
```

### Time and Space Complexities Summary

| Operation          | Time Complexity     | Space Complexity     |
| :---------------   | :------------------ | :------------------- |
|  Creation          |     O(1)            |      O(n)            |
|  Adding Elements   |     O(1)            |      O(1)            |
|  Checking Elements |     O(1)            |      O(1)            |
|  Deleting Elements |     O(1)            |      O(1)            |

Understanding these operations and their complexities helps in effectively utilizing WeakSets in JavaScript for various applications, especially those requiring temporary storage of objects without preventing garbage collection.

Limitations
- No Size Property: WeakSet does not have a size property or any method to iterate over its elements because its elements can be garbage collected at any time.
- Limited Use: Due to their weakly held references and lack of iteration methods, WeakSets are more specialized and less commonly used than regular Sets.

By understanding these aspects, we can make informed decisions about when and how to use WeakSets in the JavaScript applications.
