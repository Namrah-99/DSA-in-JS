## Objects in JavaScript

Objects are a fundamental data structure in JavaScript used to store collections of key-value pairs. They are versatile and widely used due to their flexibility and ease of use.

## Characteristics
- Key-Value Pairs: Objects store data in key-value pairs where keys are strings (or symbols) and values can be any data type.
- Dynamic Nature: Objects can be modified at runtime, allowing keys to be added, changed, or deleted.
- Prototype Chain: Objects can inherit properties and methods from other objects through the prototype chain.

## Common Operations and Their Complexities

### 1. Creating an Object

- Description: Initialize a new object.
- Syntax: let obj = {}; or let obj = new Object();
- Time Complexity: O(1)
- Space Complexity: O(1)

### 2. Setting Properties

- Description: Add or update a key-value pair in the object.
- Syntax: obj[key] = value; or obj.key = value;
- Time Complexity: O(1)
- Space Complexity: O(1) (additional space for new properties)

### 3. Getting Properties

- Description: Retrieve the value associated with a given key.
- Syntax: obj[key]; or obj.key;
- Time Complexity: O(1)
- Space Complexity: O(1)

### 4. Deleting Properties

- Description: Remove a key-value pair from the object.
- Syntax: delete obj[key];
- Time Complexity: O(1)
- Space Complexity: O(1)

### 5. Checking for Properties

- Description: Check if a key exists in the object.
- Syntax: key in obj; or obj.hasOwnProperty(key);
- Time Complexity: O(1)
- Space Complexity: O(1)

### 6. Iterating Over Properties

- Description: Loop through the keys or values of the object.
- Syntax:
  - For-in Loop: for (let key in obj) { ... }
  - Object.keys(): Object.keys(obj).forEach(key => { ... });
  - Object.values(): Object.values(obj).forEach(value => { ... });
  - Object.entries(): Object.entries(obj).forEach(([key, value]) => { ... });
  - Time Complexity: O(n) (n is the number of properties)
  - Space Complexity: O(n) (for arrays created by Object.keys, Object.values, and Object.entries)

### 7. Merging Objects

- Description: Combine properties from one or more objects into a single object.
- Syntax: Object.assign(target, ...sources); or { ...obj1, ...obj2 }
- Time Complexity: O(n) (n is the total number of properties in all objects)
- Space Complexity: O(n)

## Additional Points to Note

- Prototype Chain: Objects in JavaScript can inherit properties and methods from a prototype object. This inheritance can affect property lookup times, although most lookups remain O(1).
- Property Attributes: Properties in objects have attributes such as writable, enumerable, and configurable, which control their behavior.
- Performance Considerations: Objects are optimized for fast property access. However, adding or deleting many properties or using non-standard keys (e.g., objects as keys) can affect performance.
- Comparison with Maps: For dynamic collections of key-value pairs where keys are unknown or not fixed, Map is often a better choice than Object due to its optimized handling of frequent additions and deletions.

Example Usage

```javascript
// Creating an object
let obj = {
  name: "John",
  age: 30
};

// Setting properties
obj.gender = "male";
obj["city"] = "New York";

// Getting properties
console.log(obj.name); // Output: John
console.log(obj["age"]); // Output: 30

// Deleting properties
delete obj.city;

// Checking for properties
console.log("name" in obj); // Output: true
console.log(obj.hasOwnProperty("age")); // Output: true

// Iterating over properties
for (let key in obj) {
  console.log(`${key}: ${obj[key]}`);
}

Object.keys(obj).forEach(key => {
  console.log(`${key}: ${obj[key]}`);
});

Object.values(obj).forEach(value => {
  console.log(value);
});

Object.entries(obj).forEach(([key, value]) => {
  console.log(`${key}: ${value}`);
});

// Merging objects
let obj2 = { height: 180, weight: 75 };
let merged = Object.assign({}, obj, obj2);
console.log(merged);

let spreadMerged = { ...obj, ...obj2 };
console.log(spreadMerged);
```

Understanding these operations and their complexities helps in effectively utilizing objects in JavaScript for various applications, especially those requiring dynamic key-value pairs and inheritance through the prototype chain.
