# HashMap Data Structures in JavaScript

In JavaScript, a `Map` object can be used as a HashMap. A `Map` is a collection of key-value pairs where keys can be of any data type, providing a more flexible key management compared to regular objects.

## Characteristics

- **Key-Value Pairs:** Each element in a `Map` is stored as a key-value pair.
- **Order of Insertion:** Maps remember the original insertion order of keys.
- **Any Type of Key:** Keys can be of any data type, not just strings.
- **Iterability:** Maps are iterable, meaning you can loop through their keys, values, or entries.

## Common Operations and Their Complexities

1. **Creation**
   - **Description:** Initialize a new `Map`.
   - **Syntax:** `let map = new Map();`
   - **Time Complexity:** O(1)
   - **Space Complexity:** O(1)

2. **Setting Elements**
   - **Description:** Add a new key-value pair to the `Map` or update an existing key with a new value.
   - **Syntax:** `map.set(key, value);`
   - **Time Complexity:** O(1) on average
   - **Space Complexity:** O(n) (n is the number of entries in the `Map`)

3. **Getting Elements**
   - **Description:** Retrieve the value associated with a given key.
   - **Syntax:** `map.get(key);`
   - **Time Complexity:** O(1) on average
   - **Space Complexity:** O(1)

4. **Deleting Elements**
   - **Description:** Remove a key-value pair from the `Map`.
   - **Syntax:** `map.delete(key);`
   - **Time Complexity:** O(1) on average
   - **Space Complexity:** O(1)

5. **Checking for Keys**
   - **Description:** Check if a key exists in the `Map`.
   - **Syntax:** `map.has(key);`
   - **Time Complexity:** O(1)
   - **Space Complexity:** O(1)

6. **Clearing the Map**
   - **Description:** Remove all key-value pairs from the `Map`.
   - **Syntax:** `map.clear();`
   - **Time Complexity:** O(1)
   - **Space Complexity:** O(1)

7. **Size of the Map**
   - **Description:** Get the number of key-value pairs in the `Map`.
   - **Syntax:** `map.size`
   - **Time Complexity:** O(1)
   - **Space Complexity:** O(1)

8. **Iterating Over Elements**
   - **Description:** Loop through the keys, values, or entries of the `Map`.
   - **Syntax:**
     ```javascript
     // Keys
     for (let key of map.keys()) {
       console.log(key);
     }

     // Values
     for (let value of map.values()) {
       console.log(value);
     }

     // Entries
     for (let [key, value] of map.entries()) {
       console.log(key, value);
     }

     // Using forEach
     map.forEach((value, key) => {
       console.log(key, value);
     });
     ```
   - **Time Complexity:** O(n) (n is the number of entries)
   - **Space Complexity:** O(n)

## Additional Points to Note

- **Comparison of Keys:** Maps use the SameValueZero algorithm for key comparison, which is similar to strict equality (===), but treats NaN as equal to NaN.
- **Order of Iteration:** The iteration order of a `Map` is guaranteed to be the same as the order in which the keys were added.
- **Performance:** Maps are optimized for frequent additions and removals of key-value pairs.
- **WeakMap:** JavaScript also provides `WeakMap`, where keys must be objects and they are weakly referenced, meaning that they do not prevent garbage collection if there are no other references to the object. This is useful for memory-sensitive applications but has limited methods compared to `Map`.

## Example Usage

```javascript
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

// Using forEach
map.forEach((value, key) => {
  console.log(key, value);
});

// Clearing the map
map.clear();
console.log(map.size); // Output: 0
```
