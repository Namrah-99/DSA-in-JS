# 189. Rotate Array

## Leetcode Problem
https://leetcode.com/problems/rotate-array/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
To solve the problem of rotating an array nums to the right by k steps efficiently, we can explore an approach, including an in-place solution with O(1) extra space.

## Approach
`Using Cyclic Replacements (In-place)`: Instead of rotating the elements one by one, we can move each element to its correct position in one go by using cyclic replacements.

## Solution Code
```javascript
var rotate = function(nums, k) {

    // Calculate effective rotations (if k is larger than nums.length, it wraps around)
    k = k % nums.length;

    // Initialize a counter to keep track of the number of elements processed
    let count = 0;
    
    // Outer loop to iterate through each starting position in the array
    for (let startIndex = 0; count < nums.length; startIndex++) {

        // Initialize variables for current index and the previous value
        let currentIndex = startIndex;
        let prevEle = nums[startIndex];

        // Inner loop (do-while) to cycle through elements until we return to the starting position
        do {
            // Calculate the next position where the current element should go
            let nextIndex = (currentIndex + k) % nums.length;

            // Swap elements: move the current element to its new position
            let temp = nums[nextIndex];
            nums[nextIndex] = prevEle;
            prevEle = temp;

            // Update current index to the next position
            currentIndex = nextIndex;

            // Increment count to track the number of elements processed
            count++;

        } while (startIndex !== currentIndex); // Repeat until we return to the starting position
    }

    // Return the modified array after rotation
    return nums;
};

// Example usage:
console.log(rotate([1,2,3,4,5,6,7],3)); // Output: [5,6,7,1,2,3,4]
```

## Explanation
### Initialization (`k`, `count`):
- `k = k % nums.length;`: Ensures that `k` is within the range of `nums.length` to handle cases where `k` might be larger than the array length.
- `count = 0;`: Initializes a counter to track the number of elements that have been correctly placed in their new positions after rotation.
### Outer Loop (`for` loop):
- `for (let start = 0; count < nums.length; start++) {`: This loop iterates through each starting position in the array. It continues until `count` reaches `nums.length`, ensuring each element is processed exactly once.
### Inner Loop (`do-while` loop):
- `do { ... } while (start !== current);`: Executes the rotation process for each element starting from `start` until we return to the starting position `start`. This loop ensures that each element is moved to its new position in a single pass using cyclic replacements.
### Rotation Logic:
- Calculates `next` as the new position for the current element based on `current + k`.
- Swaps elements between `nums[current]` and `nums[next]`, using `prev` and `temp` variables to facilitate the swap.
- Updates `current` to `next` and increments `count` to track progress.
### Return:
- Returns `nums` array after all elements have been rotated according to `k` steps to the right.

## Dry Run
Example: `rotate([1,2,3,4,5,6,7], 3)`
1. Initialization:
```
nums = [1, 2, 3, 4, 5, 6, 7]
k = 3
Calculate k % nums.length: 3 % 7 = 3
count = 0
```
2. Outer Loop (for start = 0):
```
start = 0
current = 0
prev = nums[0] = 1
```
Inner Loop (do-while):
```
Calculate next = (0 + 3) % 7 = 3
Swap nums[3] with prev: nums = [1, 2, 3, 1, 5, 6, 7]
Update prev = 4
Update current = 3
Increment count = 1
```
```
Calculate next = (3 + 3) % 7 = 6
Swap nums[6] with prev: nums = [1, 2, 3, 1, 5, 6, 4]
Update prev = 7
Update current = 6
Increment count = 2
```
```
Calculate next = (6 + 3) % 7 = 2
Swap nums[2] with prev: nums = [1, 2, 7, 1, 5, 6, 4]
Update prev = 3
Update current = 2
Increment count = 3
```
Continue until `start === current` (which happens after the first complete cycle):
```
nums = [7, 1, 2, 3, 4, 5, 6]
```
3. Result:
- Return nums = [5, 6, 7, 1, 2, 3, 4]

## Output
```
k:  3
================================================
startIndex:  0  currentIndex:  0  prevEle:  1
nextIndex:  3  nums[nextIndex]:  4  prevEle:  1
nums[nextIndex]:  1  prevEle:  4
currentIndex:  3

nums:  [ 1, 2, 3, 1, 5, 6, 7 ]

startIndex !== currentIndex  true
--------------------------------------------------------
nextIndex:  6  nums[nextIndex]:  7  prevEle:  4
nums[nextIndex]:  4  prevEle:  7
currentIndex:  6

nums:  [ 1, 2, 3, 1, 5, 6, 4 ]

startIndex !== currentIndex  true
--------------------------------------------------------
nextIndex:  2  nums[nextIndex]:  3  prevEle:  7
nums[nextIndex]:  7  prevEle:  3
currentIndex:  2

nums:  [ 1, 2, 7, 1, 5, 6, 4 ]

startIndex !== currentIndex  true
--------------------------------------------------------
nextIndex:  5  nums[nextIndex]:  6  prevEle:  3
nums[nextIndex]:  3  prevEle:  6
currentIndex:  5

nums:  [ 1, 2, 7, 1, 5, 3, 4 ]

startIndex !== currentIndex  true
--------------------------------------------------------
nextIndex:  1  nums[nextIndex]:  2  prevEle:  6
nums[nextIndex]:  6  prevEle:  2
currentIndex:  1

nums:  [ 1, 6, 7, 1, 5, 3, 4 ]

startIndex !== currentIndex  true
--------------------------------------------------------
nextIndex:  4  nums[nextIndex]:  5  prevEle:  2
nums[nextIndex]:  2  prevEle:  5
currentIndex:  4

nums:  [ 1, 6, 7, 1, 2, 3, 4 ]

startIndex !== currentIndex  true
--------------------------------------------------------
nextIndex:  0  nums[nextIndex]:  1  prevEle:  5
nums[nextIndex]:  5  prevEle:  1
currentIndex:  0

nums:  [ 5, 6, 7, 1, 2, 3, 4 ]

startIndex !== currentIndex  false
--------------------------------------------------------
count:  7
[ 5, 6, 7, 1, 2, 3, 4 ]
```

## Complexity Analysis
Time Complexity: `O(n)`, each element is moved exactly once.
Space Complexity: `O(1)`, no extra space used

#### Explanation:
The time complexity of the given `rotate` function is `O(n)` and not O(n^2) due to the nature of how each element in the array `nums` is moved exactly once during the rotation process.

Let's break down why it's O(n):

##### 1. Loop Structure: 
- The function uses a single loop that iterates over each element in the array exactly once. The loop condition `count < nums.length` ensures that the loop runs exactly `nums.length` times.
##### 2. Cyclic Replacements: 
- Inside the loop, each element is moved to its new position in a single pass using the cyclic replacement technique:
  - It calculates the next position for the current element (`next = (current + k) % nums.length`).
  - It performs the swap of elements (`nums[next] = prev` and updates `prev` and `current`).
##### 3. Counting Operations: The `count` variable keeps track of how many elements have been correctly placed in their final positions. It increments with each swap operation, ensuring that each element is processed exactly once.
##### 4. Termination Condition: 
- The outer loop runs exactly `nums.length` times, and within each iteration, the inner `do-while` loop ensures that each element is placed correctly in its new position.

Given these points, the total number of operations (swaps) performed by the function is proportional to the number of elements n in the array nums. There are no nested loops or operations that would increase the complexity to O(n^2). Each element is handled precisely once, leading to a time complexity of `O(n)`.

Therefore, despite the nested look of the code, the actual complexity is linear, `O(n)`, making this an efficient approach for rotating the array nums to the right by k steps.
