# HashTable Data Structures in JavaScript

In JavaScript, a `Map` object can serve as a hash table. Additionally, objects are often used as hash tables, though they have some limitations compared to `Map`. A hash table stores key-value pairs and uses a hash function to compute an index into an array of buckets or slots, from which the desired value can be found.

## Characteristics

- **Key-Value Pairs:** Each element in a hash table is stored as a key-value pair.
- **Hash Function:** A function that converts a given key into a specific index in an array.
- **Collision Handling:** Techniques like chaining (using linked lists) or open addressing (probing) to handle collisions where multiple keys hash to the same index.
- **Dynamic Resizing:** Automatically resizing the array when it becomes too full to maintain efficient operations.

## Common Operations and Their Complexities

1. **Creation**
   - **Description:** Initialize a new hash table.
   - **Syntax:**
     ```javascript
     // Using an object
     let hashTable = {};

     // Using a Map
     let hashTable = new Map();
     ```
   - **Time Complexity:** O(1)
   - **Space Complexity:** O(1)

2. **Setting Elements**
   - **Description:** Add a new key-value pair to the hash table or update an existing key with a new value.
   - **Syntax:**
     ```javascript
     // Using an object
     hashTable[key] = value;

     // Using a Map
     hashTable.set(key, value);
     ```
   - **Time Complexity:** O(1) on average
   - **Space Complexity:** O(n) (n is the number of entries in the hash table)

3. **Getting Elements**
   - **Description:** Retrieve the value associated with a given key.
   - **Syntax:**
     ```javascript
     // Using an object
     let value = hashTable[key];

     // Using a Map
     let value = hashTable.get(key);
     ```
   - **Time Complexity:** O(1) on average
   - **Space Complexity:** O(1)

4. **Deleting Elements**
   - **Description:** Remove a key-value pair from the hash table.
   - **Syntax:**
     ```javascript
     // Using an object
     delete hashTable[key];

     // Using a Map
     hashTable.delete(key);
     ```
   - **Time Complexity:** O(1) on average
   - **Space Complexity:** O(1)

5. **Checking for Keys**
   - **Description:** Check if a key exists in the hash table.
   - **Syntax:**
     ```javascript
     // Using an object
     let exists = key in hashTable;

     // Using a Map
     let exists = hashTable.has(key);
     ```
   - **Time Complexity:** O(1)
   - **Space Complexity:** O(1)

6. **Clearing the Hash Table**
   - **Description:** Remove all key-value pairs from the hash table.
   - **Syntax:**
     ```javascript
     // Using an object
     hashTable = {};

     // Using a Map
     hashTable.clear();
     ```
   - **Time Complexity:** O(1)
   - **Space Complexity:** O(1)

7. **Size of the Hash Table**
   - **Description:** Get the number of key-value pairs in the hash table.
   - **Syntax:**
     ```javascript
     // Using an object
     let size = Object.keys(hashTable).length;

     // Using a Map
     let size = hashTable.size;
     ```
   - **Time Complexity:** O(1)
   - **Space Complexity:** O(1)

8. **Iterating Over Elements**
   - **Description:** Loop through the keys, values, or entries of the hash table.
   - **Syntax:**
     ```javascript
     // Using an object
     for (let key in hashTable) {
       if (hashTable.hasOwnProperty(key)) {
         console.log(key, hashTable[key]);
       }
     }

     // Using a Map
     for (let [key, value] of hashTable.entries()) {
       console.log(key, value);
     }

     // Using forEach with Map
     hashTable.forEach((value, key) => {
       console.log(key, value);
     });
     ```
   - **Time Complexity:** O(n) (n is the number of entries)
   - **Space Complexity:** O(n)

## Additional Points to Note

- **Hash Function:** A good hash function distributes keys uniformly across the array to minimize collisions.
- **Collision Handling:** Common techniques include chaining (storing multiple elements at the same index using a data structure like a linked list) and open addressing (finding another open slot within the array).
- **Dynamic Resizing:** When the load factor (ratio of the number of elements to the array size) exceeds a certain threshold, the array is resized to maintain efficient operations.
- **Performance:** Hash tables are optimized for quick lookups, insertions, and deletions.
- **WeakMap:** JavaScript also provides `WeakMap`, where keys must be objects and they are weakly referenced, meaning that they do not prevent garbage collection if there are no other references to the object. This is useful for memory-sensitive applications but has limited methods compared to `Map`.

## Example Usage

```javascript
// Using an object as a hash table

// Creating a new hash table
let hashTable = {};

// Setting key-value pairs
hashTable['a'] = 1;
hashTable['b'] = 2;

// Getting a value by key
console.log(hashTable['a']); // Output: 1

// Checking for a key
console.log('b' in hashTable); // Output: true

// Deleting a key-value pair
delete hashTable['a'];

// Iterating over keys and values
for (let key in hashTable) {
  if (hashTable.hasOwnProperty(key)) {
    console.log(key, hashTable[key]);
  }
}

// Using a Map as a hash table

// Creating a new Map
let map = new Map();

// Setting key-value pairs
map.set('a', 1);
map.set('b', 2);

// Getting a value by key
console.log(map.get('a')); // Output: 1

// Checking for a key
console.log(map.has('b')); // Output: true

// Deleting a key-value pair
map.delete('a');

// Iterating over keys, values, and entries
for (let key of map.keys()) {
  console.log(key);
}

for (let value of map.values()) {
  console.log(value);
}

for (let [key, value] of map.entries()) {
  console.log(key, value);
}

// Using forEach with Map
map.forEach((value, key) => {
  console.log(key, value);
});

// Clearing the map
map.clear();
console.log(map.size); // Output: 0
```

Understanding these operations and their complexities helps in efficiently utilizing hash tables in JavaScript for various applications, especially those requiring frequent key-based lookups and dynamic insertion/deletion of entries.
