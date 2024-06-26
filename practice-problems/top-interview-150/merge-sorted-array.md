# 88. Merge Sorted Array

## Leetcode Problem
https://leetcode.com/problems/merge-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150

## Approach
Using a two-pointer approach starting from the end of both arrays. This allows us to merge the arrays in-place without needing extra space.

## Solution Code

```javascript
function merge(nums1, m, nums2, n) {
    // Pointers for nums1 and nums2
    let p1 = m - 1;
    let p2 = n - 1;
    // Pointer for the last position in nums1
    let p = m + n - 1;

    // While there are still elements to compare in nums1 and nums2
    while (p1 >= 0 && p2 >= 0) {
        if (nums1[p1] > nums2[p2]) {
            nums1[p] = nums1[p1];
            p1--;
        } else {
            nums1[p] = nums2[p2];
            p2--;
        }
        p--;
    }

    // If there are remaining elements in nums2, copy them
    while (p2 >= 0) {
        nums1[p] = nums2[p2];
        p2--;
        p--;
    }
}

// Example usage
let nums1 = [1, 2, 3, 0, 0, 0];
let m = 3;
let nums2 = [2, 5, 6];
let n = 3;
merge(nums1, m, nums2, n);
console.log(nums1); // Output: [1, 2, 2, 3, 5, 6]

nums1 = [1];
m = 1;
nums2 = [];
n = 0;
merge(nums1, m, nums2, n);
console.log(nums1); // Output: [1]

nums1 = [0];
m = 0;
nums2 = [1];
n = 1;
merge(nums1, m, nums2, n);
console.log(nums1); // Output: [1]
```

## Explanation of the Code

#### Initialize Pointers:
- p1 starts at the last element of the initial part of nums1.
- p2 starts at the last element of nums2.
- p starts at the last position of nums1.

#### Merge from the End:
- The while loop compares elements from the end of nums1 and nums2 and places the larger element at the current position of p in nums1.
- After placing the element, it moves the respective pointer (p1 or p2) and the position pointer p.

#### Copy Remaining Elements:
- If p2 is not exhausted, it copies the remaining elements of nums2 into nums1.

## Time Complexity
- This ensures that the merged array is sorted in non-decreasing order. The algorithm runs in O(m + n) time and uses O(1) additional space, making it efficient and optimal.
 
