# HashSet Data Structures in JavaScript

In JavaScript, the closest equivalent to a HashSet is the `Set` object. A `Set` is a collection of unique values, where each value can only occur once.

## Characteristics

- **Unique Values:** A `Set` can only store unique values, preventing duplicates.
- **Insertion Order:** `Set` maintains the order of elements as they were inserted.
- **Any Type of Value:** Values in a `Set` can be of any type, including objects, functions, and primitives.
- **Iterability:** `Set` is iterable, allowing you to loop through its values.

## Common Operations and Their Complexities

1. **Creation**

   - **Description:** Initialize a new `Set`.
   - **Syntax:** `let set = new Set();`
   - **Time Complexity:** O(1)
   - **Space Complexity:** O(1)

2. **Adding Elements**

   - **Description:** Add a new value to the `Set`.
   - **Syntax:** `set.add(value);`
   - **Time Complexity:** O(1) on average
   - **Space Complexity:** O(n) (n is the number of entries in the `Set`)

3. **Checking for Elements**

   - **Description:** Check if a value exists in the `Set`.
   - **Syntax:** `set.has(value);`
   - **Time Complexity:** O(1) on average
   - **Space Complexity:** O(1)

4. **Deleting Elements**

   - **Description:** Remove a value from the `Set`.
   - **Syntax:** `set.delete(value);`
   - **Time Complexity:** O(1) on average
   - **Space Complexity:** O(1)

5. **Clearing the Set**

   - **Description:** Remove all values from the `Set`.
   - **Syntax:** `set.clear();`
   - **Time Complexity:** O(1)
   - **Space Complexity:** O(1)

6. **Size of the Set**

   - **Description:** Get the number of values in the `Set`.
   - **Syntax:** `set.size`
   - **Time Complexity:** O(1)
   - **Space Complexity:** O(1)

7. **Iterating Over Elements**

   - **Description:** Loop through the values of the `Set`.
   - **Syntax:**

     ```javascript
     // Using for...of loop
     for (let value of set) {
       console.log(value);
     }

     // Using forEach method
     set.forEach((value) => console.log(value));
     ```

   - **Time Complexity:** O(n) (n is the number of entries)
   - **Space Complexity:** O(n)

## Additional Points to Note

- **Comparison of Values:** `Set` uses the SameValueZero algorithm for value comparison, similar to strict equality (===), but treats NaN as equal to NaN.
- **Order of Iteration:** The iteration order of a `Set` is guaranteed to be the same as the order in which the values were added.
- **Performance:** `Set` is optimized for frequent additions and removals of values.

## Example Usage

```javascript
// Creating a new Set
let set = new Set();

// Adding values
set.add(1);
set.add("a");
set.add({ key: "value" });

// Checking for a value
console.log(set.has(1)); // Output: true

// Deleting a value
set.delete(1);

// Iterating over values
for (let value of set) {
  console.log(value);
}

set.forEach((value) => console.log(value));

// Clearing the set
set.clear();
console.log(set.size); // Output: 0
```
