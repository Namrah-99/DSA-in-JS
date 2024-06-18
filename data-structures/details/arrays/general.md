<div align="center">
  <img height="60" src="https://img.icons8.com/color/344/javascript.png">
  <h1>JavaScript Arrays Questions</h1>
</div>

<p align="center">Create, Traverse & Manipulate Arrays</p>

###### 1. How can you check if an array includes a certain value?
<details><summary><b>Solution</b></summary>
<p>

```javascript
  const array = [1, 2, 3, 4, 5];
  
  // Method 1: Using includes()
  const includesValue1 = array.includes(3); // true
  
  // Method 2: Using indexOf() (for older browsers)
  const includesValue2 = array.indexOf(3) !== -1; // true
  
  // Method 3: Using some()
  const includesValue3 = array.some(element => element === 3); // true
  
  console.log(includesValue1); // true
  console.log(includesValue2); // true
  console.log(includesValue3); // true
```
includes() checks for the exact value in the array.
some() checks if at least one element satisfies a condition.

### Time Complexity
#### Using includes():
```javascript
const includesValue1 = array.includes(3); // true
```
- Time Complexity: O(n)
- Explanation: The includes() method checks each element of the array one by one until it finds the specified value or reaches the end of the array.
#### Using indexOf():
```javascript
const includesValue2 = array.indexOf(3) !== -1; // true
```
- Time Complexity: O(n)
- Explanation: The indexOf() method also checks each element of the array one by one until it finds the specified value or reaches the end of the array.
#### Using some():
```javascript
const includesValue3 = array.some(element => element === 3); // true
```
- Time Complexity: O(n)
- Explanation: The some() method tests whether at least one element in the array passes the test implemented by the provided function. It stops iterating once it finds an element that passes the test or reaches the end of the array.

For all three methods, the time complexity is O(n), where n is the number of elements in the array. This is because each method potentially needs to examine each element in the array to determine if the specified value is present.

</p>
</details>

###### 2. How can you remove duplicates in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const numbers = [1, 2, 2, 3, 4, 4, 5];

// Method 1: Using `Set()` (modern, preserves insertion order)
const uniqueNumbers = [...new Set(numbers)]; // [1, 2, 3, 4, 5]

// Method 2: Using `filter()` and `indexOf()` (more control, potentially less efficient)
const filteredUniqueNumbers = numbers.filter((num, index) => numbers.indexOf(num) === index); // [1, 2, 3, 4, 5]

console.log(uniqueNumbers); // [1, 2, 3, 4, 5]
console.log(filteredUniqueNumbers); // [1, 2, 3, 4, 5]
```
- Set() creates a new set that inherently removes duplicates. spread syntax (...) converts the set back to an array.
- filter() creates a new array with elements that pass a test (here, being unique based on indexOf()).

### Time Complexity
#### Using Set():
```javascript
const uniqueNumbers = [...new Set(numbers)]; // [1, 2, 3, 4, 5]
```
- Time Complexity: O(n)
- Explanation: Creating a Set and spreading it back into an array both involve iterating through the array once.
#### Using filter() and indexOf():
```javascript
const filteredUniqueNumbers = numbers.filter((num, index) => numbers.indexOf(num) === index); // [1, 2, 3, 4, 5]
```
- Time Complexity: O(n^2)
- Explanation: The filter() method iterates through each element of the array, and for each element, indexOf() performs a linear search, resulting in nested iterations.

#### Summary
- Using Set(): Time complexity is O(n). This method is more efficient and should be preferred when working with large arrays.
- Using filter() and indexOf(): Time complexity is O(n^2). This method is less efficient due to the nested iteration caused by indexOf() within filter().
</p>
</details>

###### 3. How can you iterate over an array in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const fruits = ["apple", "banana", "orange"];

// Method 1: Using `for` loop (traditional)
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]); // apple, banana, orange
}

// Method 2: Using `forEach()` (modern, concise)
fruits.forEach(fruit => console.log(fruit)); // apple, banana, orange

// Method 3: Using `for...of` loop (modern, iterates over values, not indices)
for (const fruit of fruits) {
  console.log(fruit); // apple, banana, orange
}
```

- for loop provides manual control over index-based iteration.
- forEach() executes a provided function for each element.
- for...of loop iterates directly over array values.

### Time Complexity

#### Using for loop (traditional):
```javascript
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]); // apple, banana, orange
}
```
- Time Complexity: O(n)
- Explanation: The loop iterates through each element of the array once.
#### Using forEach() (modern, concise):
```javascript
fruits.forEach(fruit => console.log(fruit)); // apple, banana, orange
```
- Time Complexity: O(n)
- Explanation: The forEach method executes a provided function once for each array element.
#### Using for...of loop (modern, iterates over values, not indices):
```javascript
for (const fruit of fruits) {
  console.log(fruit); // apple, banana, orange
}
```
- Time Complexity: O(n)
- Explanation: The for...of loop iterates over the values of the array elements once.

</p>
</details>

###### 4. How can you add elements to the beginning and end of an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const colors = ["red", "green", "blue"];

// Add to beginning:
colors.unshift("yellow"); // ["yellow", "red", "green", "blue"]

// Add to end:
colors.push("purple"); // ["yellow", "red", "green", "blue", "purple"]

console.log(colors); // ["yellow", "red", "green", "blue", "purple"]
```

- unshift() adds elements to the front of the array.
- push() adds elements to the back of the array.

### Time Complexity
#### Add to beginning using unshift():
```javascript
colors.unshift("yellow"); // ["yellow", "red", "green", "blue"]
```
- Time Complexity: O(n)
- Explanation: The unshift method adds an element to the beginning of the array and shifts all the existing elements one position to the right. This involves moving all elements, which takes O(n) time where n is the number of elements in the array.
#### Add to end using push():
```javascript
colors.push("purple"); // ["yellow", "red", "green", "blue", "purple"]
```
- Time Complexity: O(1)
- Explanation: The push method adds an element to the end of the array. This operation takes constant time O(1) because it simply appends the element without needing to shift any existing elements.

</p>
</details>

###### 5. How can you find the index of an element in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const letters = ["a", "b", "c", "d", "e"];

// Method 1: Using `indexOf()` (returns the first occurrence)
const indexOfC = letters.indexOf("c"); // 2

// Method 2: Using `lastIndexOf()` (returns the last occurrence)
const lastIndexOfE = letters.lastIndexOf("e"); // 4

console.log(indexOfC); // 2
console.log(lastIndexOfE); // 4
```

- indexOf() searches for the first element matching a value and returns its index, or -1 if not found.
- lastIndexOf() searches from the end and returns the last occurrence's index.

### Time Complexity
#### Using indexOf():
```javascript
const indexOfC = letters.indexOf("c"); // 2
```
- Time Complexity: O(n)
- Explanation: The indexOf method searches through the array from the beginning to find the first occurrence of the specified element. In the worst case, it has to check each element until it finds a match or reaches the end of the array.
#### Using lastIndexOf():
```javascript
const lastIndexOfE = letters.lastIndexOf("e"); // 4
```
- Time Complexity: O(n)
- Explanation: The lastIndexOf method searches through the array from the end to find the last occurrence of the specified element. In the worst case, it has to check each element from the end to the beginning until it finds a match or reaches the start of the array.

</p>
</details>
