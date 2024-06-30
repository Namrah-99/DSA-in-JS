# 380. Insert Delete GetRandom O(1)

## Leetcode Problem
https://leetcode.com/problems/insert-delete-getrandom-o1/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The RandomizedSet class needs to support the following operations:

- `insert(val)`: Inserts an item `val` into the set if it is not already present. Returns `true` if the item was not present, `false` otherwise.
- `remove(val)`: Removes an item `val` from the set if it is present. Returns `true` if the item was present, `false` otherwise.
- `getRandom()`: Returns a random element from the current set of elements. Each element must have the same probability of being returned.

The goal is to implement these functions such that each function works in average `O(1)` time complexity.

### Key Points
- Insert and remove operations need to be efficient.
- getRandom needs to be efficient, requiring uniform random access to the elements in the set.

## Approach
To achieve average `O(1)` time complexity for all operations, we can use a combination of a list (array) and a hash map:
- List to store the elements, allowing efficient random access.
- Hash Map to store the indices of elements in the list, allowing efficient lookups and removals.
#### Detailed Steps
- Insert:
    - Check if the value is already in the hash map. If not, add it to the list and update the hash map with the index of the new element.
- Remove:
    - Check if the value is in the hash map. If it is, swap the element to be removed with the last element in the list to maintain O(1) deletion time. Then, update the hash map and remove the last element.
- getRandom:
    - Simply return a random element from the list.
 
## Solution Code
```javascript
class RandomizedSet {
    constructor() {
        this.map = new Map();
        this.list = [];
    }
    
    insert(val) {
        if (this.map.has(val)) {
            return false;
        }
        this.list.push(val);
        this.map.set(val, this.list.length - 1);
        return true;
    }
    
    remove(val) {
        if (!this.map.has(val)) {
            return false;
        }
        const index = this.map.get(val);
        const lastElement = this.list[this.list.length - 1];
        
        // Swap the element with the last element
        this.list[index] = lastElement;
        this.map.set(lastElement, index);
        
        // Remove the last element
        this.list.pop();
        this.map.delete(val);
        return true;
    }
    
    getRandom() {
        const randomIndex = Math.floor(Math.random() * this.list.length);
        return this.list[randomIndex];
    }
}

// Example usage:
const randomizedSet = new RandomizedSet();
console.log(randomizedSet.insert(1)); // true
console.log(randomizedSet.remove(2)); // false
console.log(randomizedSet.insert(2)); // true
console.log(randomizedSet.getRandom()); // 1 or 2
console.log(randomizedSet.remove(1)); // true
console.log(randomizedSet.insert(2)); // false
console.log(randomizedSet.getRandom()); // 2
```

## Complexity Analysis
- Insert: `O(1)` time complexity, `O(n)` space complexity.
- Remove: `O(1)` time complexity, `O(n)` space complexity.
- Get Random: `O(1)` time complexity, `O(n)` space complexity.


The average time complexity for each operation is O(1) due to the efficient use of a list and a hash map to manage the elements and their indices. The space complexity is O(n) because the list and the hash map store all the elements in the set.
