# 135. Candy

## Leetcode Problem
https://leetcode.com/problems/candy/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Understanding
You are given an array `ratings` where each element represents the rating of a child standing in line. The goal is to distribute candies to the children while satisfying the following conditions:

- Each child must receive at least one candy.
- A child with a higher rating than their neighbor should receive more candies than that neighbor.

You need to return the minimum number of candies required to meet these conditions.

### Examples
#### Example 1:
```
Input: ratings = [1,0,2]
Output: 5
```
Explanation:
- Allocate candies as follows: [2, 1, 2]
- The first child gets 2 candies (higher rating than second child).
- The second child gets 1 candy (lower rating).
- The third child gets 2 candies (higher rating than second child).

#### Example 2:
```
Input: ratings = [1,2,2]
Output: 4
```
Explanation:
- Allocate candies as follows: [1, 2, 1]
- The first child gets 1 candy (lower rating).
- The second child gets 2 candies (higher rating than first child).
- The third child gets 1 candy (same rating as second child).
### Constraints
- n == ratings.length
- 1 <= n <= 2 * 10^4
- 0 <= ratings[i] <= 2 * 10^4

## Approach
To solve this problem with an `O(n)` time complexity, we can use a two-pass algorithm:
#### 1. First Pass (Left to Right):
- Ensure each child has more candies than the previous child if they have a higher rating.
#### 2. Second Pass (Right to Left):
- Ensure each child has more candies than the next child if they have a higher rating.

## Solution Code
```javascript
var candy = function (ratings) {
    // Initialization
    let candies = new Array(ratings.length).fill(1);
    // First pass (left to right)
    for (let i = 1; i < ratings.length; i++) {
        if (ratings[i] > ratings[i - 1]) {
            candies[i] = candies[i - 1] + 1;
        }
    }
    // Second pass (right to left)
    for (let i = ratings.length - 2; i >= 0; i--) {
        if(ratings[i] > ratings[i+1]){
            candies[i] = Math.max(candies[i], candies[i+1]+1)
            }
    }
    // Sum up the candies
    console.log(candies)
    return candies.reduce((sum,val)=>sum+val,0)

};

// Example usage:
console.log(candy([1,0,2])); // Output: 5
console.log(candy([1,2,2])); // Output: 4
```

## Explanation of Code
#### 1. Initialization:
- Create an array `candies` of the same length as `ratings` and initialize all elements to 1 (each child gets at least one candy).
#### 2. First Pass (Left to Right):
- Traverse the `ratings` array from left to right.
- If a child has a higher rating than the previous child, increase the number of candies for this child by 1 more than the previous child.
#### 3. Second Pass (Right to Left):
- Traverse the `ratings` array from right to left.
- If a child has a higher rating than the next child, ensure that the current child has more candies than the next child. This is done by taking the maximum of the current candies and the next child's candies plus one.
#### 4. Summing Up Candies:
- Sum up all the values in the `candies` array to get the minimum number of candies required.

### Complexity Analysis
- **Time Complexity:** `O(n)`, where n is the number of children. This is because we iterate through the list twice.
- **Space Complexity:** `O(n)`, for storing the candies for each child.
