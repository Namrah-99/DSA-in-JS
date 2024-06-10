### Two Sum

- Problem: Given an array of integers, find two numbers such that they add up to a specific target number.
- Solution: Use a hash map to store the complement of each number.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time and constant space for the hash map.

### Contains Duplicate

- Problem: Given an array, find if the array contains any duplicates.
- Solution: Use a hash set to check for duplicates.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time and constant space for the hash set.

### Valid Anagram

- Problem: Check if two strings are anagrams of each other.
- Solution: Use a hash map to count character frequencies.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time and space.

### Group Anagrams

- Problem: Given an array of strings, group anagrams together.
- Solution: Use a hash map with sorted strings as keys.
- Time Complexity: O(n \* k log k) where k is the maximum length of a string.
- Efficiency: Efficient for moderate-sized input, as sorting each string takes O(k log k).

### Top K Frequent Elements

- Problem: Find the k most frequent elements in an array.
- Solution: Use a hash map for counting and a min-heap for the top k elements.
- Time Complexity: O(n log k)
- Efficiency: Efficient for moderate k, as insertion into the heap is logarithmic in k.

### Intersection of Two Arrays

- Problem: Find the intersection of two arrays.
- Solution: Use hash sets for fast lookup.
- Time Complexity: O(n + m)
- Efficiency: Efficient, as it uses linear time relative to the input sizes.

### Longest Consecutive Sequence

- Problem: Find the length of the longest consecutive elements sequence.
- Solution: Use a hash set for fast lookup.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time.

### Word Pattern

- Problem: Check if a pattern matches a string based on a specific rule.
- Solution: Use two hash maps for pattern-to-word and word-to-pattern mapping.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time and space.

### Isomorphic Strings

- Problem: Check if two strings are isomorphic.
- Solution: Use two hash maps for character mapping.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time and space.

### First Unique Character in a String

- Problem: Find the first non-repeating character in a string.
- Solution: Use a hash map to count character frequencies and then iterate.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time.

### Subarray Sum Equals K

- Problem: Find the number of continuous subarrays that sum to a given number k.
- Solution: Use a hash map to store cumulative sum frequencies.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time and space.

### Find All Anagrams in a String

- Problem: Find all start indices of anagram substrings of a pattern in a string.
- Solution: Use a sliding window and hash maps for character counts.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time.

### Find the Difference

- Problem: Find the letter that was added in t.
- Solution: Use a hash map to count character frequencies.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time and space.

### Subarrays with K Different Integers

- Problem: Find the number of subarrays with exactly k different integers.
- Solution: Use a sliding window and two hash maps.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time.

### Longest Substring Without Repeating Characters

- Problem: Find the length of the longest substring without repeating characters.
- Solution: Use a sliding window and a hash map.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time.

### Minimum Window Substring

- Problem: Find the minimum window substring containing all characters of another string.
- Solution: Use a sliding window and hash maps.
- Time Complexity: O(n)
- Efficiency: Efficient, but can be complex due to handling window resizing.

### Max Consecutive Ones

- Problem: Find the maximum number of consecutive 1s in a binary array.
- Solution: Use a simple iteration and counting.
- Time Complexity: O(n)
- Efficiency: Very efficient, as it uses linear time.

### Product of Array Except Self

- Problem: Find an array output such that output[i] is equal to the product of all elements of nums except nums[i].
- Solution: Use prefix and suffix product arrays.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time and space.

### Valid Palindrome II

- Problem: Check if a string can become a palindrome by removing at most one character.
- Solution: Use two pointers and a hash map for checking.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time.

### Longest Palindromic Substring

- Problem: Find the longest palindromic substring.
- Solution: Use dynamic programming and a hash map for intermediate results.
- Time Complexity: O(n^2)
- Efficiency: Moderately efficient for smaller strings due to quadratic time complexity.

### Palindromic Substrings

- Problem: Count all palindromic substrings in a string.
- Solution: Use dynamic programming or expand around center.
- Time Complexity: O(n^2)
- Efficiency: Moderately efficient for smaller strings due to quadratic time complexity.

### Length of Last Word

- Problem: Find the length of the last word in a string.
- Solution: Use simple iteration from the end of the string.
- Time Complexity: O(n)
- Efficiency: Very efficient, as it uses linear time.

### Rotate Array

- Problem: Rotate an array to the right by k steps.
- Solution: Use array reversal.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time.

### Remove Duplicates from Sorted Array

- Problem: Remove duplicates in-place from a sorted array.
- Solution: Use two pointers.
- Time Complexity: O(n)
- Efficiency: Very efficient, as it uses linear time.

### Move Zeroes

- Problem: Move all zeroes in an array to the end while maintaining the order of other elements.
- Solution: Use two pointers.
- Time Complexity: O(n)
- Efficiency: Very efficient, as it uses linear time.

### Intersection of Two Arrays II

- Problem: Find the intersection of two arrays, allowing duplicate elements.
- Solution: Use a hash map to count frequencies.
- Time Complexity: O(n + m)
- Efficiency: Efficient, as it uses linear time relative to the input sizes.

### Valid Parentheses

- Problem: Check if the input string has valid parentheses.
- Solution: Use a stack.
- Time Complexity: O(n)
- Efficiency: Very efficient, as it uses linear time.

### Daily Temperatures

- Problem: Find the number of days until a warmer temperature for each day.
- Solution: Use a stack.
- Time Complexity: O(n)
- Efficiency: Very efficient, as it uses linear time.

### Next Greater Element I

- Problem: Find the next greater element for each element in an array.
- Solution: Use a stack.
- Time Complexity: O(n)
- Efficiency: Very efficient, as it uses linear time.

### Valid Sudoku

- Problem: Determine if a 9x9 Sudoku board is valid.
- Solution: Use three hash sets for rows, columns, and boxes.
- Time Complexity: O(1) (constant time for fixed-size board)
- Efficiency: Very efficient, constant time for fixed input size.

### Search Insert Position

- Problem: Find the index where a target should be inserted in a sorted array.
- Solution: Use binary search.
- Time Complexity: O(log n)
- Efficiency: Very efficient for sorted arrays.

### First Bad Version

- Problem: Find the first bad version in a sequence.
- Solution: Use binary search.
- Time Complexity: O(log n)
- Efficiency: Very efficient for sorted sequences.

### Minimum Size Subarray Sum

- Problem: Find the minimal length of a contiguous subarray with a sum >= target.
- Solution: Use a sliding window.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time.

### Find Peak Element

- Problem: Find a peak element in an array.
- Solution: Use binary search.
- Time Complexity: O(log n)
- Efficiency: Very efficient for unsorted arrays.

### Kth Largest Element in an Array

- Problem: Find the kth largest element in an unsorted array.
- Solution: Use a min-heap.
- Time Complexity: O(n log k)
- Efficiency: Efficient for moderate k.

### Sort Colors

- Problem: Sort an array with three colors.
- Solution: Use the Dutch national flag algorithm.
- Time Complexity: O(n)
- Efficiency: Very efficient, as it uses linear time.

### Find Minimum in Rotated Sorted Array

- Problem: Find the minimum element in a rotated sorted array.
- Solution: Use binary search.
- Time Complexity: O(log n)
- Efficiency: Very efficient for sorted and rotated arrays.

### Find Duplicate Number

- Problem: Find the duplicate number in an array of n + 1 integers.
- Solution: Use Floyd's Tortoise and Hare (cycle detection).
- Time Complexity: O(n)
- Efficiency: Very efficient, as it uses linear time.

### Median of Two Sorted Arrays

- Problem: Find the median of two sorted arrays.
- Solution: Use binary search.
- Time Complexity: O(log(min(n, m)))
- Efficiency: Efficient for balanced input sizes.

### Longest Increasing Subsequence

- Problem: Find the length of the longest increasing subsequence.
- Solution: Use dynamic programming with a hash map.
- Time Complexity: O(n log n)
- Efficiency: Efficient for longer sequences.

### Coin Change

- Problem: Find the minimum number of coins to make up a given amount.
- Solution: Use dynamic programming.
- Time Complexity: O(n \* amount)
- Efficiency: Efficient for moderate amount values.

### Maximum Subarray

- Problem: Find the contiguous subarray with the maximum sum.
- Solution: Use Kadane's algorithm.
- Time Complexity: O(n)
- Efficiency: Very efficient, as it uses linear time.

### House Robber

- Problem: Maximize the amount of money robbed without robbing adjacent houses.
- Solution: Use dynamic programming.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time.

### Climbing Stairs

- Problem: Count distinct ways to climb a staircase with n steps.
- Solution: Use dynamic programming.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time.

### Longest Common Subsequence

- Problem: Find the longest common subsequence of two strings.
- Solution: Use dynamic programming.
- Time Complexity: O(n \* m)
- Efficiency: Efficient for moderate-sized strings.

### Unique Paths

- Problem: Count the number of unique paths in a grid.
- Solution: Use dynamic programming.
- Time Complexity: O(m \* n)
- Efficiency: Efficient for moderate grid sizes.

### Edit Distance

- Problem: Find the minimum edit distance between two strings.
- Solution: Use dynamic programming.
- Time Complexity: O(n \* m)
- Efficiency: Efficient for moderate-sized strings.

### Decode Ways

- Problem: Count the number of ways to decode a message.
- Solution: Use dynamic programming.
- Time Complexity: O(n)
- Efficiency: Efficient, as it uses linear time.

### Combination Sum

- Problem: Find all unique combinations that sum to a target.
- Solution: Use backtracking.
- Time Complexity: O(2^n)
- Efficiency: Efficient for smaller input sizes due to exponential complexity.

### Subsets

- Problem: Find all subsets of a set.
- Solution: Use backtracking.
- Time Complexity: O(2^n)
- Efficiency: Efficient for smaller input sizes due to exponential complexity.

These problems cover a wide range of common interview scenarios and demonstrate the efficiency of using JavaScript's built-in data structures like objects (hash maps) and arrays in solving them.
