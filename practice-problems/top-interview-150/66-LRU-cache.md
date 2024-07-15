# 146. LRU Cache

## Leetcode Problem
https://leetcode.com/problems/lru-cache/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To implement the LRUCache in JavaScript with `O(1)` average time complexity for both `get` and `put` operations, we can utilize a `combination of a doubly linked list and a hashmap`. Here's how we can approach the problem and implement the solution:

# Approach:

## Data Structures Used:
- HashMap (cache): This will store key-value pairs for fast access (O(1) time complexity).
- Doubly Linked List (DLL): This will maintain the order of keys based on their recent usage. Nodes closer to the head are more recently used, and nodes closer to the tail are less recently used.

## Operations:
- Initialization (`LRUCache(capacity)`):
  - Initialize a `DLL` to manage the order of keys.
  - Initialize a `cache` (HashMap) to store key-value pairs.
  - Ensure `capacity` is set appropriately.
- `get(key)` Operation:
  - If the `key` exists in `cache`:
    - Move the corresponding node in `DLL` to the front (to mark it as recently used).
    - Return the value associated with the `key`.
  - If the `key` doesn't exist, return `-1`.
- `put(key, value)` Operation:
  - If the `key` already exists in `cache`:
    - Update the value in `cache`.
    - Move the corresponding node in `DLL` to the front (to mark it as recently used).
  - If the `key` doesn't exist:
    - Create a new node with `key` and `value`.
    - Add the new node to the front of `DLL`.
    - Add the `key` with its corresponding node to `cache`.
    - If adding this new entry exceeds `capacity`, remove the least recently used node from the `DLL` (tail of the list) and also remove its corresponding entry from `cache`.
## Edge Cases Handled:
- Correctly managing the cache when capacity limits are reached.
- Handling `get` operations for non-existent keys.
- Efficiently updating the cache and DLL for `put` operations.
## Complexity Analysis:
- Time Complexity:
  - Both `get` and `put` operations are `O(1)` on average due to the use of `HashMap` for direct access and `DLL` for efficient reordering.
- Space Complexity:
  - `O(capacity)` due to the storage of at most `capacity` key-value pairs in the cache and nodes in the `DLL`.

## Solution Code

```javascript
class LRUCache {
    constructor(capacity) {
        this.capacity = capacity;
        this.cache = new Map();
        this.head = { key: null, value: null, prev: null, next: null };
        this.tail = { key: null, value: null, prev: this.head, next: null };
        this.head.next = this.tail;
    }
    
    get(key) {
        if (!this.cache.has(key)) {
            return -1;
        }
        
        const node = this.cache.get(key);
        this._moveToHead(node);
        return node.value;
    }
    
    put(key, value) {
        if (this.cache.has(key)) {
            const node = this.cache.get(key);
            node.value = value;
            this._moveToHead(node);
        } else {
            const newNode = { key, value, prev: this.head, next: this.head.next };
            this.head.next.prev = newNode;
            this.head.next = newNode;
            this.cache.set(key, newNode);
            
            if (this.cache.size > this.capacity) {
                this._removeLRU();
            }
        }
    }
    
    _moveToHead(node) {
        if (node.prev !== this.head) {
            // remove
            node.prev.next = node.next;
            node.next.prev = node.prev;
            // add to start
            node.prev = this.head;
            node.next = this.head.next;

            this.head.next.prev = node;
            this.head.next = node;

        }
    }

    _removeLRU() {
        // remove from end as least frequently are present at end and most frequently on start
        let nodeToDel = this.tail.prev;
        let nodeToDelKey = nodeToDel.key;
        //remove last node
        this.tail.prev = nodeToDel.prev;
        nodeToDel.prev.next = this.tail;
        // del from cache
        this.cache.delete(nodeToDelKey)
    }
}


// Example 1
const lruCache = new LRUCache(2);

lruCache.put(1, 1); // cache is {1=1}
lruCache.put(2, 2); // cache is {1=1, 2=2}
console.log(lruCache.get(1)); // Output: 1
lruCache.put(3, 3); // LRU key was 2, evicts key 2, cache is {1=1, 3=3}
console.log(lruCache.get(2)); // Output: -1 (not found)
lruCache.put(4, 4); // LRU key was 1, evicts key 1, cache is {4=4, 3=3}
console.log(lruCache.get(1)); // Output: -1 (not found)
console.log(lruCache.get(3)); // Output: 3
console.log(lruCache.get(4)); // Output: 4

console.log("_________________________________")
// Example 2
const lruCache2 = new LRUCache(3);

lruCache2.put(1, 10); // cache is {1=10}
lruCache2.put(2, 20); // cache is {1=10, 2=20}
lruCache2.put(3, 30); // cache is {1=10, 2=20, 3=30}
console.log(lruCache2.get(2)); // Output: 20 (key 2 is now the most recently used)
lruCache2.put(4, 40); // LRU key was 1, evicts key 1, cache is {2=20, 3=30, 4=40}
console.log(lruCache2.get(1)); // Output: -1 (not found)
console.log(lruCache2.get(3)); // Output: 30
console.log(lruCache2.get(4)); // Output: 40
```
## Explanation
- The `LRUCache` class uses a doubly linked list (`head` and `tail`) to maintain the order of recently used keys.
- `cache` is a `Map` where keys are stored along with their corresponding nodes in the doubly linked list.
- `get` and `put` methods ensure `O(1)` average time complexity by efficiently managing both the hashmap and the linked list for recent usage tracking.
- `_moveToHead` moves a node to the front of the linked list when accessed or updated.
- `_removeLRU` removes the least recently used node from the cache and the linked list when capacity is exceeded.

## Detailed Explanation of `this.head.next = this.tail;`

The line `this.head.next = this.tail;` in the constructor of the `LRUCache` class sets up the initial state of the doubly linked list (`DLL`). Let's break down its purpose and why it's essential:

### Purpose:
#### Initialization of DLL:
The `LRUCache` uses a doubly linked list to maintain the order of recently used keys. The `head` and `tail` nodes serve as sentinels to simplify boundary conditions.

#### Connecting Head and Tail:
- `this.head` represents the head sentinel, which is always present and does not store any key-value pair.
- `this.tail` represents the tail sentinel, which is also always present and does not store any key-value pair.
- Initially, the DLL is empty, so `this.head.next` should point to `this.tail` and `this.tail.prev` should point to `this.head`. This setup ensures that the DLL is properly initialized with no nodes in between the head and the tail.

#### Handling Edge Cases:
- When the cache is empty (`capacity` is zero or just after construction), `this.head.next` and `this.tail.prev` correctly point to each other, indicating that there are no nodes in the DLL.
- When nodes are added (`put` operation), the DLL structure will be adjusted accordingly. New nodes will be inserted between `this.head` and `this.tail`.

#### Visual Representation:
If we were to represent the initial state visually:

```css
Initial State:
this.head <-> this.tail
```
- `this.head` and `this.tail` are connected, indicating an empty `DLL`.

After adding nodes, the structure might look like:

```css
After adding nodes:
this.head <-> Node1 <-> Node2 <-> ... <-> NodeN <-> this.tail
```
Here, `Node1`, `Node2`, ..., `NodeN` represent the nodes with actual key-value pairs stored in the cache.

The line `this.head.next = this.tail;` ensures that the DLL is properly set up with sentinels (head and tail) and handles the initial empty state of the cache. This setup is foundational for subsequent operations (get, put, etc.) to efficiently manage and access the cached data while maintaining the LRU eviction policy.
