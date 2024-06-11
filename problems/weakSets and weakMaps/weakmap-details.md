# WeakMap in JavaScript

WeakMap is a collection of key-value pairs where the keys are objects and the values can be of any type. Keys in a WeakMap are held weakly, meaning that if there are no other references to the key object, it can be garbage collected. This makes WeakMap particularly useful for associating data with objects without preventing their garbage collection.

## Characteristics

1. **Weak References**: Keys in a WeakMap are weakly held, meaning they do not prevent garbage collection.
2. **Only Object Keys**: WeakMap keys must be objects, not primitive values.
3. **Non-Enumerable**: WeakMap is not enumerable, meaning there is no way to list the entries in a WeakMap.
4. **No Duplicates**: Each key in a WeakMap must be unique.

## Common Operations and Their Complexities

1. **Creation**
   - **Description**: Initialize a new WeakMap.
   - **Syntax**: `let weakMap = new WeakMap();`
   - **Time Complexity**: O(1)
   - **Space Complexity**: O(n) (n is the number of entries)

2. **Setting Elements**
   - **Description**: Add or update a key-value pair in the WeakMap.
   - **Syntax**: `weakMap.set(key, value);`
   - **Time Complexity**: O(1)
   - **Space Complexity**: O(1) (additional space for new entries)

3. **Getting Elements**
   - **Description**: Retrieve the value associated with a given key.
   - **Syntax**: `weakMap.get(key);`
   - **Time Complexity**: O(1)
   - **Space Complexity**: O(1)

4. **Checking for Elements**
   - **Description**: Check if a key exists in the WeakMap.
   - **Syntax**: `weakMap.has(key);`
   - **Time Complexity**: O(1)
   - **Space Complexity**: O(1)

5. **Deleting Elements**
   - **Description**: Remove a key-value pair from the WeakMap.
   - **Syntax**: `weakMap.delete(key);`
   - **Time Complexity**: O(1)
   - **Space Complexity**: O(1)

## Additional Points to Note

1. **Garbage Collection**: The primary advantage of WeakMap is that it allows objects used as keys to be garbage collected if there are no other references to them. This is particularly useful for managing memory in scenarios where objects are used temporarily.
2. **No Iteration**: Unlike Map, WeakMap does not provide a way to iterate over its entries. This is because the entries are held weakly and can be garbage collected at any time.
3. **Use Cases**: WeakMaps are useful for storing metadata associated with objects, such as caching, tracking, or private data, without preventing the objects from being garbage collected.

## Example Usage

```javascript
// Creating a new WeakMap
let weakMap = new WeakMap();

let obj1 = {name: "John"};
let obj2 = {name: "Doe"};

// Setting elements
weakMap.set(obj1, "Employee");
weakMap.set(obj2, "Manager");

// Getting elements
console.log(weakMap.get(obj1)); // Output: Employee
console.log(weakMap.get(obj2)); // Output: Manager

// Checking for elements
console.log(weakMap.has(obj1)); // Output: true
console.log(weakMap.has({name: "John"})); // Output: false (different object reference)

// Deleting elements
weakMap.delete(obj2);
console.log(weakMap.has(obj2)); // Output: false

// Garbage collection
obj1 = null; // obj1 may be garbage collected if there are no other references to it
```

### Time and Space Complexities Summary

| Operation          | Time Complexity     | Space Complexity     |
| :---------------   | :------------------ | :------------------- |
|  Creation          |     O(1)            |      O(n)            |
|  Setting Elements  |     O(1)            |      O(1)            |
|  Getting Elements  |     O(1)            |      O(1)            |
|  Checking Elements |     O(1)            |      O(1)            |
|  Deleting Elements |     O(1)            |      O(1)            |

Understanding these operations and their complexities helps in effectively utilizing WeakMaps in JavaScript for various applications, especially those requiring temporary storage of key-value pairs without preventing garbage collection.

Limitations
- No Size Property: WeakMap does not have a size property or any method to iterate over its entries because its entries can be garbage collected at any time.
- Limited Use: Due to their weakly held references and lack of iteration methods, WeakMaps are more specialized and less commonly used than regular Maps.

By understanding these aspects, wwe can make informed decisions about when and how to use WeakMaps in the JavaScript applications.
