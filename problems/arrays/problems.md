## Efficient Use of Arrays

Arrays provide efficient solutions due to their `contiguous memory allocation`, which allows for direct access to elements `(O(1) time complexity for accessing elements by index)`. Operations that require `traversal of the entire array usually have linear time complexity (O(n))`, making arrays suitable for problems that can be solved with a single pass or require direct index-based manipulation.

For problems that can benefit from sorting, using algorithms like `quicksort or mergesort, which have O(n log n) time complexity`, can enhance the efficiency of subsequent operations (e.g., binary search).

## Problems

### Finding the Maximum/Minimum Element

Problem: Find the maximum or minimum element in an array.
Time Complexity: O(n)
Explanation: By iterating through the array once, you can compare each element with the current maximum or minimum.

### Searching for an Element

Problem: Check if an element exists in an array.
Time Complexity: O(n)
Explanation: In an unsorted array, you need to check each element. However, if the array is sorted, binary search can be used with O(log n) time complexity.

### Reversing an Array

Problem: Reverse the order of elements in an array.
Time Complexity: O(n)
Explanation: By swapping elements from the start and end moving towards the center, you can reverse the array in linear time.

### Finding the Sum of Elements

Problem: Calculate the sum of all elements in an array.
Time Complexity: O(n)
Explanation: By iterating through the array once, you can accumulate the sum.

### Merging Two Sorted Arrays

Problem: Merge two sorted arrays into one sorted array.
Time Complexity: O(n + m) where n and m are the lengths of the two arrays.
Explanation: By using two pointers, you can merge the arrays in linear time.

### Rotating an Array

Problem: Rotate the array by k positions.
Time Complexity: O(n)
Explanation: This can be done efficiently using array reversal in three steps: reverse the whole array, reverse the first k elements, and then reverse the remaining elements.

### Removing Duplicates from a Sorted Array

Problem: Remove duplicates from a sorted array.
Time Complexity: O(n)
Explanation: By using two pointers, one for the current element and another for the place to insert the unique element, you can remove duplicates in linear time.

### Finding the Intersection of Two Arrays

Problem: Find common elements between two arrays.
Time Complexity: O(n + m) if both arrays are sorted, using a two-pointer technique.
Explanation: By using two pointers to traverse both arrays simultaneously, you can efficiently find common elements.

### Finding the Missing Number

Problem: Find the missing number in an array containing n distinct numbers taken from the range 0 to n.
Time Complexity: O(n)
Explanation: By calculating the expected sum of the first n natural numbers and subtracting the sum of the array elements, you can find the missing number.

### Finding the Duplicates in an Array

Problem: Find duplicates in an array of n elements.
Time Complexity: O(n) if using extra space (e.g., a hash set); O(n log n) if sorting the array first.
Explanation: Using a hash set to track seen elements can help identify duplicates efficiently.

### Finding the Second Largest Element

Problem: Find the second largest element in an array.
Time Complexity: O(n)
Explanation: By iterating through the array twice or keeping track of the largest and second largest elements in a single pass.

### Checking for Pair with Given Sum

Problem: Check if there are two elements in the array that add up to a specific sum.
Time Complexity: O(n) with a hash set.
Explanation: Using a hash set to track complements of the target sum.

### Finding the Majority Element

Problem: Find the element that appears more than n/2 times in an array.
Time Complexity: O(n)
Explanation: Using Boyer-Moore Voting Algorithm.

### Finding the Longest Consecutive Sequence

Problem: Find the length of the longest consecutive sequence in an array.
Time Complexity: O(n) with a hash set.
Explanation: Using a hash set to track elements and finding the longest streak.

### Finding the Subarray with Given Sum

Problem: Find a subarray with a given sum in a non-negative integer array.
Time Complexity: O(n)
Explanation: Using the sliding window technique.

### Maximum Subarray Sum (Kadane’s Algorithm)

Problem: Find the maximum sum of a contiguous subarray.
Time Complexity: O(n)
Explanation: Using Kadane's Algorithm to keep track of the current and global maximum.

### Finding the Equilibrium Index

Problem: Find an index such that the sum of elements at lower indexes is equal to the sum of elements at higher indexes.
Time Complexity: O(n)
Explanation: By calculating the total sum and then iterating while keeping track of the left sum.

### Finding the Duplicate in a Range (Floyd’s Tortoise and Hare)

Problem: Find the duplicate number in an array of n+1 integers where each integer is between 1 and n.
Time Complexity: O(n)
Explanation: Using Floyd’s Tortoise and Hare (cycle detection).

### Finding the First Missing Positive

Problem: Find the smallest missing positive integer.
Time Complexity: O(n)
Explanation: Using index-based marking.

### Finding the Intersection of Two Unsorted Arrays

Problem: Find common elements between two unsorted arrays.
Time Complexity: O(n + m) with a hash set.
Explanation: Using a hash set to store elements of one array and then checking the other array.

### Finding the Longest Subarray with Sum 0

Problem: Find the longest subarray with a sum of 0.
Time Complexity: O(n)
Explanation: Using a hash map to store prefix sums.

### Finding the Longest Subarray with Equal Number of 0s and 1s

Problem: Find the longest subarray with an equal number of 0s and 1s.
Time Complexity: O(n)
Explanation: Using a hash map to store the difference between the count of 0s and 1s.

### Trapping Rain Water

Problem: Calculate how much water can be trapped after raining.
Time Complexity: O(n)
Explanation: Using two-pointer technique to keep track of the maximum height to the left and right.

### Rotating an Array by K Positions Using Reverse

Problem: Rotate the array to the right by k steps.
Time Complexity: O(n)
Explanation: By reversing the array in parts and then reversing the whole array.

### Finding the Kth Largest Element

Problem: Find the k-th largest element in an array.
Time Complexity: O(n) on average using Quickselect.
Explanation: Using the Quickselect algorithm.

### Finding the Product of Array Except Self

Problem: Find the product of all elements except itself without using division.
Time Complexity: O(n)
Explanation: Using two passes to calculate the product of elements to the left and right.

### Finding the Minimum in a Rotated Sorted Array

Problem: Find the minimum element in a rotated sorted array.
Time Complexity: O(log n)
Explanation: Using binary search.

### Finding the Peak Element

Problem: Find a peak element in an array.
Time Complexity: O(log n)
Explanation: Using binary search.

### Finding the Missing Number in an Unsorted Array

Problem: Find the missing number in an array of n integers.
Time Complexity: O(n)
Explanation: Using XOR operation.

### Finding the Single Element in a Sorted Array

Problem: Find the single element in a sorted array where every element appears twice except one.
Time Complexity: O(log n)
Explanation: Using binary search.

### Finding the Number of Subarrays with Sum Equals K

Problem: Count the number of subarrays with sum equal to k.
Time Complexity: O(n)
Explanation: Using a hash map to store prefix sums.

### Finding the Minimum Size Subarray Sum

Problem: Find the minimal length of a contiguous subarray with a sum greater than or equal to a given value.
Time Complexity: O(n)
Explanation: Using the sliding window technique.

### Finding the Maximum Product Subarray

Problem: Find the maximum product of a contiguous subarray.
Time Complexity: O(n)
Explanation: Keeping track of the maximum and minimum products.

### Checking if Array is a Palindrome

Problem: Check if the array is a palindrome.
Time Complexity: O(n)
Explanation: Comparing elements from both ends.

### Finding the Largest Rectangle in Histogram

Problem: Find the largest rectangle area in a histogram.
Time Complexity: O(n)
Explanation: Using a stack to keep track of heights.

### Finding All Duplicates in an Array

Problem: Find all elements that appear twice in an array.
Time Complexity: O(n)
Explanation: Using index marking or a hash map.

### Rearranging Array Alternately

Problem: Rearrange the array such that the maximum element is followed by the minimum element.
Time Complexity: O(n)
Explanation: Using an in-place rearrangement technique.

### Finding the Smallest and Second Smallest Elements

Problem: Find the smallest and second smallest elements in an array.
Time Complexity: O(n)
Explanation: By iterating through the array once.

### Segregating 0s and 1s

Problem: Segregate 0s and 1s in an array.
Time Complexity: O(n)
Explanation: Using a two-pointer approach.

### Finding the Maximum Length of Subarray with Positive Product

Problem: Find the maximum length of a subarray with a positive product.
Time Complexity: O(n)
Explanation: Keeping track of the lengths of subarrays with positive and negative products.
