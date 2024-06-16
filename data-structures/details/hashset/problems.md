# Interview Problems Solvable with HashSet in JavaScript

Here is a list of 50+ interview problems that can be efficiently solved using data structures like HashSet, along with their time complexities and explanations of how HashSet helps in solving them:

1. **Two Sum**
   - **Description:** Find two numbers in an array that add up to a specific target.
   - **Time Complexity:** O(n)
   - **Efficiency:** Use HashSet to store the difference between the target and each element as you iterate through the array.

2. **Contains Duplicate**
   - **Description:** Check if an array contains any duplicates.
   - **Time Complexity:** O(n)
   - **Efficiency:** Use HashSet to keep track of seen elements.

3. **Intersection of Two Arrays**
   - **Description:** Find the intersection of two arrays.
   - **Time Complexity:** O(n + m)
   - **Efficiency:** Use HashSet to store elements of one array and check for membership with elements of the second array.

4. **Happy Number**
   - **Description:** Determine if a number is a happy number.
   - **Time Complexity:** O(log n)
   - **Efficiency:** Use HashSet to detect cycles in the sum of the squares of digits.

5. **Longest Consecutive Sequence**
   - **Description:** Find the length of the longest consecutive elements sequence.
   - **Time Complexity:** O(n)
   - **Efficiency:** Use HashSet to store elements and check for consecutive sequences.
  
6. **First Missing Positive**
   - Description: Find the smallest missing positive integer.
   - Time Complexity: O(n)
   - Efficiency: Use a HashSet to keep track of seen numbers and iterate to find the smallest missing positive.

7. **Valid Sudoku**
   - Description: Check if a 9x9 Sudoku board is valid.
   - Time Complexity: O(1)
   - Efficiency: Use a HashSet to keep track of seen numbers in rows, columns, and 3x3 sub-boxes.

8. **Longest Substring Without Repeating Characters**
   - Description: Find the length of the longest substring without repeating characters.
   - Time Complexity: O(n)
   - Efficiency: Use a sliding window with a HashSet to store characters of the current substring.

9. **Group Anagrams**
   - Description: Group anagrams together.
   - Time Complexity: O(n * k)
   - Efficiency: Use a HashSet to categorize anagrams by sorted strings.

10. **Word Pattern** 
     - Description: Check if a string follows a given pattern.
     - Time Complexity: O(n)
     - Efficiency: Use two HashSets to map pattern characters to words and vice versa.

11. **Single Number** 
     - Description: Find the element that appears only once in an array where every other element appears twice.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to track elements seen once and remove if seen again.

12. **Longest Palindrome** 
     - Description: Find the length of the longest palindrome that can be built with given characters.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to count characters and determine pairs.

13. **Valid Anagram** 
     - Description: Determine if two strings are anagrams.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to count character frequencies.

14. **Subarray Sum Equals K**
     - Description: Find the number of subarrays that sum to a specific target.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to store cumulative sums and their counts.

15. **4Sum II**
     - Description: Count tuples that sum to zero from four lists.
     - Time Complexity: O(n^2)
     - Efficiency: Use a HashSet to store sums of pairs and check for complements.

16. **Longest Palindromic Subsequence**
     - Description: Find the length of the longest palindromic subsequence.
     - Time Complexity: O(n^2)
     - Efficiency: Use a HashSet to store intermediate results in dynamic programming.

17. **Minimum Window Substring**
     - Description: Find the minimum window substring that contains all characters of another string.
     - Time Complexity: O(n)
     - Efficiency: Use a sliding window with a HashSet to track character counts.

18. **Find All Anagrams in a String**
     - Description: Find all start indices of anagram substrings.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to store character counts for comparison.

19. **Repeated DNA Sequences**
     - Description: Find all 10-letter-long sequences that occur more than once in a DNA string.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to track seen sequences.

20. **Top K Frequent Elements**
     - Description: Find the k most frequent elements in an array.
     - Time Complexity: O(n log k)
     - Efficiency: Use a HashSet with a heap to track frequencies.

21. **Kth Largest Element in a Stream**
     - Description: Design a class to find the kth largest element in a stream.
     - Time Complexity: O(n log k)
     - Efficiency: Use a HashSet with a heap to maintain the k largest elements.

22. **Find All Numbers Disappeared in an Array**
     - Description: Find all the numbers that are missing in an array.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to track present numbers.

23. **Subsets**
     - Description: Find all possible subsets of a given array.
     - Time Complexity: O(n * 2^n)
     - Efficiency: Use a HashSet to avoid duplicate subsets.

24. **Permutations**
     - Description: Find all permutations of a given array.
     - Time Complexity: O(n * n!)
     - Efficiency: Use a HashSet to avoid duplicate permutations.

25. **Combination Sum**
     - Description: Find all unique combinations of numbers that sum to a target.
     - Time Complexity: O(2^n)
     - Efficiency: Use a HashSet to track seen combinations.

26. **Word Break**
     - Description: Determine if a string can be segmented into space-separated words.
     - Time Complexity: O(n^2)
     - Efficiency: Use a HashSet to store words for quick lookup.

27. **Isomorphic Strings**
     - Description: Check if two strings are isomorphic.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to map characters from one string to another.

28. **Palindrome Permutation**
     - Description: Check if any permutation of a string is a palindrome.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to count character frequencies.

29. **Check if a Number is a Sum of Two Squares**
     - Description: Check if a number can be expressed as the sum of two squares.
     - Time Complexity: O(sqrt(n))
     - Efficiency: Use a HashSet to track seen squares.

30. **Find the Town Judge**
     - Description: Determine the town judge in a graph representation.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to track trust relationships.

31. **Decode String**
     - Description: Decode an encoded string with nested patterns.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to track nested patterns.

32. **Evaluate Division**
     - Description: Evaluate division expressions and return results.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to track evaluated divisions.

33. **N-ary Tree Level Order Traversal**
     - Description: Perform a level-order traversal of an N-ary tree.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to track visited nodes.

34. **Employee Importance**
     - Description: Calculate the importance of an employee.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to track employee IDs.

35. **Number of Islands**
     - Description: Count the number of islands in a grid.
     - Time Complexity: O(m * n)
     - Efficiency: Use a HashSet to track visited cells.

36. **Surrounded Regions**
     - Description: Capture surrounded regions on a board.
     - Time Complexity: O(m * n)
     - Efficiency: Use a HashSet to track border regions.

37. **Alien Dictionary**
     - Description: Derive the order of characters in an alien language.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to track character order.

38. **Path Sum**
     - Description: Determine if there's a path in a binary tree that sums to a target.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to store seen sums.

39. **Course Schedule**
     - Description: Determine if you can finish all courses given prerequisites.
     - Time Complexity: O(V + E)
     - Efficiency: Use a HashSet to detect cycles in the dependency graph.

40. **Clone Graph**
     - Description: Clone a graph.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to track visited nodes.

41. **Find Minimum in Rotated Sorted Array**
     - Description: Find the minimum element in a rotated sorted array.
     - Time Complexity: O(log n)
     - Efficiency: Use binary search with HashSet to avoid duplicates.

42. **Word Ladder**
     - Description: Transform one word into another by changing one letter at a time.
     - Time Complexity: O(n * k)
     - Efficiency: Use a HashSet to store intermediate words.

43. **Graph Valid Tree**
     - Description: Determine if a graph is a valid tree.
     - Time Complexity: O(V + E)
     - Efficiency: Use a HashSet to track visited nodes.

44. **Course Schedule II**
     - Description: Return the order in which you should take courses to finish them all.
     - Time Complexity: O(V + E)
     - Efficiency: Use a HashSet to detect cycles and track order.

45. **Meeting Rooms II**
     - Description: Determine the minimum number of conference rooms required.
     - Time Complexity: O(n log n)
     - Efficiency: Use a HashSet to track meeting times.

46. **Sliding Window Maximum**
     - Description: Find the maximum in each sliding window of size k.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to track maximums.

47. **Palindrome Pairs**
     - Description: Find all unique pairs of indices that form palindromes.
     - Time Complexity: O(n * k^2)
     - Efficiency: Use a HashSet to store reversed words.

48. **Kth Smallest Element in a Sorted Matrix**
     - Description: Find the kth smallest element in a sorted matrix.
     - Time Complexity: O(k log n)
     - Efficiency: Use a HashSet with a min-heap to track elements.

49. **Insert Delete GetRandom O(1)**
     - Description: Design a data structure that supports insertion, deletion, and getting random elements in constant time.
     - Time Complexity: O(1)
     - Efficiency: Use a HashSet to store elements.

50. **Word Search**
     - Description: Find if there is a word in a 2D grid.
     - Time Complexity: O(m * n * k)
     - Efficiency: Use a HashSet to track visited cells.

51. **Robot Room Cleaner**
     - Description: Design a robot to clean a room given certain constraints.
     - Time Complexity: O(n)
     - Efficiency: Use a HashSet to track cleaned cells.
