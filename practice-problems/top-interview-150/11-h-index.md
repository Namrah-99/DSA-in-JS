# 274. H-Index

## Leetcode Problem
https://leetcode.com/problems/h-index/description/?envType=study-plan-v2&envId=top-interview-150

## Problem Explanation
The h-index is a metric that measures both the productivity and citation impact of the publications of a researcher. According to the definition on Wikipedia, the h-index is defined as the maximum value of `h` such that the given researcher has published at least `h` papers that have each been cited at least `h` times.

## Problem Requirements
Given an array of integers `citations` where `citations[i]` is the number of citations a researcher received for their `i-th` paper, return the researcher's h-index.

## Examples
#### Example 1:
```
Input: citations = [3, 0, 6, 1, 5]
Output: 3
```
Explanation: 
- The researcher has 5 papers with the following citations: `[3, 0, 6, 1, 5]`.
- The researcher has 3 papers with at least 3 citations each. The other two papers have fewer than 3 citations. Hence, the h-index is 3.

#### Example 2:
```
Input: citations = [1, 3, 1]
Output: 1
```
Explanation: 
- The researcher has 3 papers with the following citations: `[1, 3, 1]`.
- The researcher has 1 paper with at least 1 citation. The other papers have fewer than 1 citation. Hence, the h-index is 1.

#### Constraints
```
- n == citations.length
- 1 <= n <= 5000
- 0 <= citations[i] <= 1000
```

## Approach
To achieve an `O(n)` time complexity, we can use a `counting sort-like approach`. The main idea is to count how many papers have each citation count and then determine the h-index by iterating from the highest possible citations count down to 0.

#### Steps:
1. **Initialize a count array of size** `n+1` to hold the number of papers with each citation count, where `n` is the length of the citations array.
2. **Populate the count array**:
- If a paper has more than `n` citations, it is counted in the `n`th index (since any paper with more than `n` citations will only contribute to the h-index being at most `n`).
3. **Iterate through the count array** from the highest citation count to determine the h-index:
- Keep a running total of the number of papers with at least `i` citations.
- The first time this running total is at least `i`, that value of `i` is the h-index.

## Solution Code
```javascript
function hIndex(citations) {
    const n = citations.length;
    const count = new Array(n + 1).fill(0);
    
    // Populate the count array
    for (let i = 0; i < n; i++) {
        if (citations[i] >= n) {
            count[n]++;
        } else {
            count[citations[i]]++;
        }
    }
    
    // Determine the h-index
    let total = 0;
    for (let i = n; i >= 0; i--) {
        total += count[i];
        if (total >= i) {
            return i;
        }
    }
    
    return 0;
}

// Example usage:
console.log(hIndex([3, 0, 6, 1, 5])); // Output: 3
console.log(hIndex([1, 3, 1]));       // Output: 1
```

## Explanation of the Code
1. Initialization:
    - `n` is the length of the `citations` array.
    - `count` is an array of size `n+1` initialized to 0.
2. Populate the Count Array:
    - Iterate through each citation. If the citation is greater than or equal to `n`, increment the count at index `n`.
    - Otherwise, increment the count at the index corresponding to the citation value.
3. Determine the h-index:
    - Iterate from the highest possible citation count (`n`) down to 0.
    - Keep a running total of the number of papers with at least `i` citations.
    - When this running total is at least `i`, return `i` as the h-index.

## Complexity Analysis
This approach ensures that we find the h-index in linear time, `O(n)`, and uses only a constant amount of extra space, `O(n)`.
