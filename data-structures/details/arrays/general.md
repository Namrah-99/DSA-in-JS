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

###### 6. How can you find the index of an element in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const array = [1, 2, 3, 4, 5];

// Method 1: Using splice()
array.splice(2, 1); // Remove element at index 2

// Method 2: Using filter()
const newArray = array.filter((_, index) => index !== 2); // Remove element at index 2

console.log(array); // [1, 2, 4, 5]
console.log(newArray); // [1, 2, 4, 5]
```

- splice(index, number) (Primary Method)
  Removes number elements starting at index and returns a new array containing the removed elements. This modifies the original array.
- filter(callbackFunction) (Alternative Method)
  Creates a new array containing all elements that pass the test implemented by the provided function. You can use this to filter out the element at the desired index.

### Time Complexity
#### Using splice():
```javascript
array.splice(2, 1); // Remove element at index 2
```
- Time Complexity: O(n)
- Explanation: The splice method removes an element from the array at the specified index and shifts all subsequent elements one position to the left. This shifting operation involves moving all elements after the removed element, which takes O(n) time where n is the number of elements in the array.

#### Using filter():
```javascript
const newArray = array.filter((_, index) => index !== 2); // Remove element at index 2
```
- Time Complexity: O(n)
- Explanation: The filter method creates a new array by iterating through each element of the original array and applying the provided function. It includes only those elements that do not match the specified condition. Since it iterates through all elements once, the time complexity is O(n).
</p>
</details>

###### 7. How can you find the index of an element in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const colors1 = ["red", "green"];
const colors2 = ["blue", "purple"];

// Method 1: Spread syntax
const combinedColors = [...colors1, ...colors2]; // ["red", "green", "blue", "purple"]

// Method 2: concat()
const combinedColors2 = colors1.concat(colors2); // ["red", "green", "blue", "purple"]

console.log(combinedColors); // ["red", "green", "blue", "purple"]
console.log(combinedColors2); // ["red", "green", "blue", "purple"]
```

- Spread Syntax (...) (Concise Method)
  Combines elements from both arrays into a new array.
- concat() (Explicit Method)
  Creates a new array containing elements from both arrays, leaving the originals unchanged.

### Time Complexity
#### Using Spread Syntax:
```javascript
const combinedColors = [...colors1, ...colors2]; // ["red", "green", "blue", "purple"]
```
- Time Complexity: O(n + m)
- Explanation: The spread syntax creates a new array by iterating through each element of colors1 and colors2. The time complexity is proportional to the sum of the lengths of both arrays, where n is the length of colors1 and m is the length of colors2.
#### Using concat():
```javascript
const combinedColors2 = colors1.concat(colors2); // ["red", "green", "blue", "purple"]
```
- Time Complexity: O(n + m)
- Explanation: The concat method creates a new array by appending all elements of colors2 to the end of colors1. This involves iterating through both arrays, resulting in a time complexity that is proportional to the sum of the lengths of both arrays.
</p>
</details>

###### 8. How can you find the index of an element in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const numbers = [3, 1, 4, 5, 2];

// Method 1: Default sort (ascending)
numbers.sort(); // [1, 2, 3, 4, 5]

// Method 2: Sort with custom comparison function (descending)
numbers.sort((a, b) => b - a); // descending order

console.log(numbers); // [5, 4, 3, 2, 1] (original array modified)
```

- sort() (Default Method)
  Sorts the array in place (ascending order by default) based on the Unicode code points of the elements. It modifies the original array.
- sort(comparisonFunction) (Custom Sorting)
  Allows you to define a custom comparison function for custom sorting logic (e.g., sorting numbers in ascending or descending order).

### Time Complexity
#### Using Default Sort (Ascending):
```javascript
numbers.sort(); // [1, 2, 3, 4, 5]
```
- Time Complexity: O(n log n)
- Explanation: The default sort method in JavaScript uses the Timsort algorithm, which has a time complexity of O(n log n) in the average and worst cases. Timsort is a hybrid sorting algorithm derived from merge sort and insertion sort.
#### Using Sort with Custom Comparison Function (Descending):
```javascript
numbers.sort((a, b) => b - a); // descending order
```
- Time Complexity: O(n log n)
- Explanation: When using a custom comparison function, the sort method still utilizes the Timsort algorithm. The time complexity remains O(n log n) in the average and worst cases, as the sorting mechanism does not change with the addition of a custom comparator.

</p>
</details>

###### 9. How can you find the index of an element in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const letters = ["a", "b", "c", "d"];

// Method 1: reverse() (mutates)
letters.reverse(); // ["d", "c", "b", "a"]

// Method 2: slice().reverse() (immutable)
const reversedLetters = letters.slice().reverse(); // ["a", "b", "c", "d"] (original remains unchanged)

console.log(letters); // ["d", "c", "b", "a"]
console.log(reversedLetters); // ["a", "b", "c", "d"]
```

- reverse is a direct method for reversing the order of elements in an array, but it modifies the original array.
- slice().reverse is a preferred approach when you want to avoid modifying the original array. It creates a new reversed array, preserving the original order.

### Time Complexity
#### Using reverse() (mutates the original array):
```javascript
letters.reverse(); // ["d", "c", "b", "a"]
```
- Time Complexity: O(n)
- Explanation: The reverse method in JavaScript iterates through the array and reverses the order of the elements in place. This requires swapping each element, which takes linear time relative to the number of elements in the array.
#### Using slice().reverse() (creates a new array and then reverses it):
```javascript
const reversedLetters = letters.slice().reverse(); // ["a", "b", "c", "d"] (original remains unchanged)
```
- Time Complexity: O(n)
- Explanation: The slice method first creates a shallow copy of the array, which takes O(n) time. Then, the reverse method is applied to this new array, which also takes O(n) time. Combining these operations, the overall time complexity remains O(n).

</p>
</details>

###### 10. How can you find the index of an element in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const message = "Hello, world!";

// Method 1: Splitting on characters
const characters = message.split(""); // ["H", "e", "l", "l", "o", ...]

// Splitting on words (space as separator)
const words = message.split(" "); // ["Hello,", "world!"]

console.log(characters); // ["H", "e", "l", "l", "o", ...]
console.log(words); // ["Hello,", "world!"]

// Method 2: Using Array.from() to split on characters
const array2 = Array.from(message); // ['h', 'e', 'l', 'l', 'o']
```
- split is the primary method for converting strings to arrays. You can specify a separator to define how the string is split.
- Array.from converts an array-like or iterable object (such as a string) into a new array.

### Time Complexity
#### Splitting on Characters:
```javascript
const characters = message.split(""); // ["H", "e", "l", "l", "o", ...]
```
- Time Complexity: O(n)
- Explanation: Splitting a string into individual characters using split("") requires iterating through each character of the string once, resulting in a time complexity of O(n), where n is the length of the string.

#### Splitting on Words:
```javascript
const words = message.split(" "); // ["Hello,", "world!"]
```
- Time Complexity: O(n)
- Explanation: Splitting a string into words using split(" ") also requires iterating through each character of the string once to identify word boundaries. Therefore, it also has a time complexity of O(n).

#### Using Array.from() to Split on Characters:
```javascript
const array2 = Array.from(message); // ['h', 'e', 'l', 'l', 'o']
```
- Time Complexity: O(n)
- Explanation: Using Array.from() to convert a string into an array of characters also requires iterating through each character of the string once, resulting in a time complexity of O(n).

#### Summary
- Splitting on Characters: O(n)
- Splitting on Words: O(n)
- Using Array.from() to Split on Characters: O(n)

</p>
</details>

###### 11. How can you convert an array to a string in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const array = ["Hello", "world"];
const string = array.join(", "); // "Hello, world"


const array = ["Hello", "world"];
const string = array.toString(); // "Hello,world"
```

- join(separator): Creates a new string by joining elements of the array with a specified separator (comma by default).
- toString(): Converts the array to a string representation, often containing commas and square brackets.

### Time Complexity

#### Using join():
```javascript
const array = ["Hello", "world"];
const string = array.join(", "); // "Hello, world"
```
- Time Complexity: O(n)
- Explanation: Iterates through each element and constructs the resulting string, where n is the total number of characters in the final string.
#### Using toString():
```javascript
const array = ["Hello", "world"];
const string = array.toString(); // "Hello,world"
```
- Time Complexity: O(n)
- Explanation: Converts each element to a string and concatenates them with commas, where n is the total number of characters in the final string.

</p>
</details>

###### 12. How can you filter elements in an array based on a condition?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(num => num % 2 === 0); // [2, 4]


const numbers = [1, 2, 3, 4, 5];
const evenNumbers = [];
for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] % 2 === 0) {
    evenNumbers.push(numbers[i]);
  }
}
```
- filter(callbackFunction): Creates a new array containing elements that pass the test implemented by the provided function.
- The for loop in JavaScript repeats a block of code a specified number of times, based on a condition, typically used for iterating over arrays or other iterable objects.

### Time Complexity

#### Using filter():
```javascript
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = numbers.filter(num => num % 2 === 0); // [2, 4]
```
- Time Complexity: O(n)
- Explanation: The filter() method iterates through each element of the array once, applying the given callback function to check if the element should be included in the resulting array. Therefore, the time complexity is O(n), where n is the number of elements in the array.

#### Using a for Loop:
```javascript
const numbers = [1, 2, 3, 4, 5];
const evenNumbers = [];
for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] % 2 === 0) {
    evenNumbers.push(numbers[i]);
  }
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates through each element of the array once, checking if each element is even and then adding it to the evenNumbers array if it is. This results in a time complexity of O(n), where n is the number of elements in the array.

</p>
</details>

###### 13. How can you map over an array and modify its elements?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const numbers = [1, 2, 3, 4, 5];
const squaredNumbers = numbers.map(num => num * num); // [1, 4, 9, 16, 25]

const numbers = [1, 2, 3, 4, 5];
const squaredNumbers = [];
for (let i = 0; i < numbers.length; i++) {
  squaredNumbers.push(numbers[i] * numbers[i]);
}
```

- map is useful for transforming each element in an array based on the logic defined in the callback function. It creates a new array with the transformed elements.
- The for loop in JavaScript repeats a block of code a specified number of times, based on a condition, typically used for iterating over arrays or other iterable objects.

### Time Complexity

#### Using map():
```javascript
const numbers = [1, 2, 3, 4, 5];
const squaredNumbers = numbers.map(num => num * num); // [1, 4, 9, 16, 25]
```
- Time Complexity: O(n)
- Explanation: The map() method iterates through each element of the array once, applying the given callback function to compute the square of each number. Therefore, the time complexity is O(n), where n is the number of elements in the array.
#### Using a for Loop:
```javascript
const numbers = [1, 2, 3, 4, 5];
const squaredNumbers = [];
for (let i = 0; i < numbers.length; i++) {
  squaredNumbers.push(numbers[i] * numbers[i]);
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates through each element of the array once, computing the square of each number and adding it to the squaredNumbers array. This results in a time complexity of O(n), where n is the number of elements in the array.

</p>
</details>

###### 14. How can you reduce an array to a single value?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using reduce()
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((acc, curr) => acc + curr, 0); // 15

// Method 2: Using a for loop
const numbers = [1, 2, 3, 4, 5];
let sum = 0;
for (let i = 0; i < numbers.length; i++) {
  sum += numbers[i];
}
```

- map is useful for transforming each element in an array based on the logic defined in the callback function. It creates a new array with the transformed elements.
- The for loop in JavaScript repeats a block of code a specified number of times, based on a condition, typically used for iterating over arrays or other iterable objects.

### Time Complexity
#### Using reduce():
```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((acc, curr) => acc + curr, 0); // 15
```
- Time Complexity: O(n)
- Explanation: The reduce() method iterates through each element of the array once, applying the given callback function to compute the sum. Therefore, the time complexity is O(n), where n is the number of elements in the array.
#### Using a for Loop:
```javascript
const numbers = [1, 2, 3, 4, 5];
let sum = 0;
for (let i = 0; i < numbers.length; i++) {
  sum += numbers[i];
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates through each element of the array once, adding each element to the sum variable. This results in a time complexity of O(n), where n is the number of elements in the array.

</p>
</details>

###### 15. How can you check if all elements in an array pass a certain condition?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using every()
const numbers = [2, 4, 6, 8, 10];
const allEven = numbers.every(num => num % 2 === 0); // true

// Method 2: Using a for loop
const numbers = [2, 4, 6, 8, 10];
let allEven = true;
for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] % 2 !== 0) {
    allEven = false;
    break;
  }
}
```
- every performs a test on each element in the array and returns true only if all elements pass the condition defined in the callback function.
- The for loop in JavaScript repeats a block of code a specified number of times, based on a condition, typically used for iterating over arrays or other iterable objects.

### Time Complexity
#### Using every():
```javascript
const numbers = [2, 4, 6, 8, 10];
const allEven = numbers.every(num => num % 2 === 0); // true
```
- Time Complexity: O(n)
- Explanation: The every() method iterates through each element of the array until it finds an element that does not satisfy the provided condition. In the worst case, it checks every element, resulting in a time complexity of O(n), where n is the number of elements in the array.
#### Using a for Loop:
```javascript
const numbers = [2, 4, 6, 8, 10];
let allEven = true;
for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] % 2 !== 0) {
    allEven = false;
    break;
  }
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates through each element of the array until it finds an element that does not satisfy the condition. In the worst case, it checks every element, resulting in a time complexity of O(n), where n is the number of elements in the array.

</p>
</details>

###### 16. How can you check if any element in an array passes a certain condition?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const numbers = [1, 2, 3, 4];

// Method 1: some()
const hasEven = numbers.some(number => number % 2 === 0); // true (2 is even)

// Method 2: filter().length > 0
const hasGreaterThanThree = numbers.filter(number => number > 3).length > 0; // true (4)

console.log(hasEven); // true
console.log(hasGreaterThanThree); // true
```

- some(callbackFunction): Returns true if at least one element in the array satisfies the test implemented by the provided function. Otherwise, it returns false.
- filter(callbackFunction).length > 0: This approach filters elements based on the condition and checks if the resulting array has any elements (length greater than 0).

### Time Complexity
#### Using some():
```javascript
const numbers = [1, 2, 3, 4];
const hasEven = numbers.some(number => number % 2 === 0); // true (2 is even)
```
- Time Complexity: O(n)
- Explanation: The some() method iterates through the elements of the array until it finds an element that satisfies the provided condition. In the worst case, it checks every element, resulting in a time complexity of O(n), where n is the number of elements in the array.
#### Using filter().length > 0:
```javascript
const numbers = [1, 2, 3, 4];
const hasGreaterThanThree = numbers.filter(number => number > 3).length > 0; // true (4)
```
- Time Complexity: O(n)
- Explanation: The filter() method iterates through all elements of the array to apply the condition and create a new array of elements that satisfy the condition. Then, checking the length of this new array is an O(1) operation. Overall, the process results in a time complexity of O(n), where n is the number of elements in the array.

</p>
</details>

###### 17. How can you find the maximum and minimum values in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const numbers = [1, 5, 2, 8, 3];

// Method 1: Math.max and Math.min with spread syntax
const maxNumber = Math.max(...numbers); // 8
const minNumber = Math.min(...numbers); // 1

// Method 2: reduce() for max
const maxWithReduce = numbers.reduce((max, number) => Math.max(max, number), -Infinity); // 8 (initial value ensures all elements are considered)

console.log(maxNumber); // 8
console.log(minNumber); // 1
console.log(maxWithReduce); // 8
```

- Math.max(...array): Spreads the array elements and uses Math.max to find the highest value.
- Math.min(...array): Spreads the array elements and uses Math.min to find the lowest value.
- reduce(callbackFunction, initialValue): This method can be used with a custom callback function to find the maximum or minimum value.

### Time Complexity
#### Using Math.max and Math.min with spread syntax:
```javascript
const numbers = [1, 5, 2, 8, 3];
const maxNumber = Math.max(...numbers); // 8
const minNumber = Math.min(...numbers); // 1
```
- Time Complexity: O(n)
- Explanation: The spread operator ...numbers creates a new list of arguments for Math.max and Math.min, which both iterate through the elements of the array to find the maximum and minimum values, respectively. The iteration is O(n) for both Math.max and Math.min.
#### Using reduce() for max:
```javascript
const maxWithReduce = numbers.reduce((max, number) => Math.max(max, number), -Infinity); // 8
```
- Time Complexity: O(n)
- Explanation: The reduce() method iterates through all elements of the array to apply the provided function, comparing each element to the current maximum value. The overall time complexity is O(n).

</p>
</details>

###### 18. How can you flatten a nested array in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const nestedArray = [1, [2, 3], [4, [5, 6]]];

function flattenConcat(arr) {
  return arr.reduce((acc, val) => acc.concat(Array.isArray(val) ? flattenConcat(val) : val), []);
}

const flattenedConcat = flattenConcat(nestedArray);
console.log(flattenedConcat); // [1, 2, 3, 4, 5, 6]

```
- concat(): Recursively use concat to combine the outer array with the result of flattening its inner arrays.
- reduce: Use reduce with a custom callback function that recursively flattens nested arrays.

- Time Complexity: O(n)
- Explanation: The flattenConcat function uses reduce() to iterate through each element of the array. For each element that is an array, it recursively calls flattenConcat. While each concat operation itself is O(n), where n is the length of the accumulator array (acc), the overall time complexity for flattening a deeply nested array still remains O(n) due to the overhead of recursion and concat operations combined.


</p>
</details>

###### 19. How can you split an array into chunks of a certain size?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const numbers = [1, 2, 3, 4, 5, 6, 7, 8];
const chunkSize = 3;

function splitIntoChunks(arr, chunkSize) {
  const chunks = [];
  for (let i = 0; i < arr.length; i += chunkSize) {
    const chunk = arr.slice(i, i + chunkSize);
    chunks.push(chunk);
  }
  return chunks;
}

const chunkedNumbers = splitIntoChunks(numbers, chunkSize);

console.log(chunkedNumbers); // [[1, 2, 3], [4, 5, 6], [7, 8]]
```

- slice(startIndex, endIndex): Use a loop to iterate through the array, creating chunks of the desired size using slice.
- Explanation:
    - The splitIntoChunks function iterates through the array using a loop, keeping track of the starting index (i).
    - In each iteration, it uses slice to extract a chunk of the desired size (chunkSize) from the original array starting at the current index (i).
    - The extracted chunk is then pushed into the chunks array.
    - Finally, the function returns the chunks array containing all the sub-arrays.

- Time Complexity: O(n)
- Explanation: The function iterates through the input array once, creating a new chunk array for each iteration. The slice operation inside the loop also has a time complexity of O(chunkSize), but since the chunk size is fixed and does not depend on the input array size, the dominant factor is the loop itself, which iterates over each element in the input array exactly once, resulting in a linear time complexity of O(n), where n is the number of elements in the input array.

</p>
</details>

###### 20. How can you shuffle an array in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const letters = ["a", "b", "c", "d", "e"];

function shuffleArray(arr) {
  arr.sort(() => Math.random() - 0.5); // random sort
}

shuffleArray(letters);

console.log(letters); // Shuffled order (e.g., ["c", "e", "a", "d", "b"])
```

- sort(comparisonFunction): Define a custom comparison function that randomly returns -1, 0, or 1 to shuffle the elements in place.
- Explanation:
    - The shuffleArray function uses sort with a custom comparison function.
    - The comparison function uses Math.random() to generate a random number between 0 and 1.
        - If the random number is less than 0.5, it returns -1, effectively swapping the elements.
        - If it's greater than 0.5, it returns 1, leaving the elements in their original order.
        - If it's exactly 0.5, it returns 0, which doesn't affect the order.
    - This approach randomly shuffles the elements in the original array.

### Time Complexity
The time complexity of shuffling an array using the sort method with a random comparison function is O(n log n), where n is the number of elements in the array.

Explanation:

- The sort method in JavaScript uses an efficient sorting algorithm (usually a variation of quicksort or mergesort) with an average time complexity of O(n log n).
- The comparison function (a, b) => Math.random() - 0.5 is called multiple times during the sorting process. Since the sorting algorithm's complexity dominates the number of comparisons, the overall time complexity is O(n log n).

**Note:** While the actual sorting operation is O(n log n), the use of a random comparison function like in this case does not guarantee a perfect shuffle. For a more precise shuffle, consider using the Fisher-Yates shuffle algorithm, which has a time complexity of O(n).

</p>
</details>

###### 21. How can you find the intersection of two arrays?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const colors1 = ["red", "green", "blue"];
const colors2 = ["blue", "purple", "yellow"];

// Method 1: Set intersection with has()
const intersection1 = Array.from(new Set(colors1).filter(x => new Set(colors2).has(x))); // ["blue"]

// Method 2: filter() with includes()
const intersection2 = colors1.filter(color => colors2.includes(color)); // ["blue"]

console.log(intersection1); // ["blue"]
console.log(intersection2); // ["blue"]

// Method 3: Set with includes()
const intersectionSet = new Set(array1.filter(value => array2.includes(value)));
const intersection = [...intersectionSet];
console.log(intersection); // [3, 4, 5]
```

- The first method leverages sets for efficient membership checks. It creates sets from both arrays and uses filter to find elements present in both sets.
- The second method uses filter with includes to check if each element in the first array exists in the second array.

### Time Complexity
#### Method 1: Set intersection with has()
```javascript
const intersection1 = Array.from(new Set(colors1).filter(x => new Set(colors2).has(x)));
```
- Time Complexity: O(n + m)
- Explanation: Creating two sets from colors1 and colors2 has a time complexity of O(n + m), where n is the number of elements in colors1 and m is the number of elements in colors2. The filter operation then iterates over the elements of colors1, which has a time complexity of O(n). The overall time complexity is O(n + m).

#### Method 2: filter() with includes()
```javascript
const intersection2 = colors1.filter(color => colors2.includes(color));
```
- Time Complexity: O(n * m)
- Explanation: The includes method inside the filter function iterates over all elements of colors2 for each element in colors1. This results in a time complexity of O(n * m), where n is the number of elements in colors1 and m is the number of elements in colors2.

#### Method 3: Set with includes()
```javascript
const intersectionSet = new Set(array1.filter(value => array2.includes(value)));
const intersection = [...intersectionSet];
```
- Time Complexity: O(n * m)
- Explanation: Similar to Method 2, the includes method inside the filter function causes a nested iteration over all elements of array2 for each element in array1, resulting in a time complexity of O(n * m), where n is the number of elements in array1 and m is the number of elements in array2.

</p>
</details>

###### 22. How can you find the union of two arrays?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const numbers1 = [1, 2, 3];
const numbers2 = [2, 3, 4];

// Method 1: Set union (unique elements)
const union1 = Array.from(new Set([...numbers1, ...numbers2])); // [1, 2, 3, 4]

// Method 2: concat() (all elements)
const union2 = numbers1.concat(numbers2); // [1, 2, 3, 2, 3, 4] (duplicates included)

console.log(union1); // [1, 2, 3, 4]
console.log(union2); // [1, 2, 3, 2, 3, 4]

const unionSet = new Set([...array1, ...array2]);
const union = [...unionSet];
console.log(union); // [1, 2, 3, 4, 5, 6, 7]
```

- new Set([...array1, ...array2]): Creates a new set containing all unique elements from both arrays (duplicates are removed).
- concat(): Combines elements from both arrays (may contain duplicates).

### Time Complexity

#### Method 1: Set union (unique elements)
```javascript
const union1 = Array.from(new Set([...numbers1, ...numbers2]));
```
- Time Complexity: O(n + m)
- Explanation: Creating a new set from the concatenation of numbers1 and numbers2 has a time complexity of O(n + m), where n is the number of elements in numbers1 and m is the number of elements in numbers2. The Array.from operation then converts the set back to an array, which also has a time complexity of O(n + m). Overall, the time complexity is O(n + m).
#### Method 2: concat() (all elements)
```javascript
const union2 = numbers1.concat(numbers2);
```
- Time Complexity: O(n + m)
- Explanation: The concat method creates a new array by concatenating numbers1 and numbers2, which has a time complexity of O(n + m), where n is the number of elements in numbers1 and m is the number of elements in numbers2.

#### Method 3: Set with concat() and spread operator
```javascript
const unionSet = new Set([...numbers1, ...numbers2]);
const union = [...unionSet];
```
- Time Complexity: O(n + m)
- Explanation: Similar to Method 1, creating a new set from the concatenation of numbers1 and numbers2 has a time complexity of O(n + m). The spread operator ... then converts the set back to an array, which also has a time complexity of O(n + m). Overall, the time complexity is O(n + m).

**Note:** Method 1 and Method 3 are preferred for finding the union of arrays, as they ensure uniqueness of elements in the resulting array and have a time complexity of O(n + m).

</p>
</details>

###### 23. How can you find the difference between two arrays?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const letters1 = ["a", "b", "c", "d"];
const letters2 = ["b", "c", "e"];

// Method 1: filter() with !includes()
const difference1 = letters1.filter(letter => !letters2.includes(letter)); // ["a", "d"]

// Method 2: Set difference (efficient)
const difference2 = Array.from(new Set(letters1).difference(new Set(letters2))); // ["a", "d"]

console.log(difference1); // ["a", "d"]
console.log(difference2); // ["a", "d"]
```
- The first method uses filter with !includes to check if each element in the first array is not present in the second array.
- The second method leverages sets for efficient difference calculations. It creates sets from both arrays and uses the difference method to find elements present in the first set but not in the second.

### Time Complexity

#### Method 1: filter() with !includes()
```javascript
const difference1 = letters1.filter(letter => !letters2.includes(letter));
```
- Time Complexity: O(n * m)
- Explanation: For each element in letters1 (of length n), includes() is called on letters2 (of length m), resulting in a time complexity of O(n * m). This is because includes() has a time complexity of O(m), and it is called for each element in letters1.

#### Method 2: Set difference (efficient)
```javascript
const difference2 = Array.from(new Set(letters1).difference(new Set(letters2)));
```
- Time Complexity: O(n + m)
- Explanation: Creating two sets from letters1 and letters2 has a time complexity of O(n + m), where n is the number of elements in letters1 and m is the number of elements in letters2. The difference() operation between the two sets has a time complexity of O(n), as it iterates over the elements in the first set. Overall, the time complexity is O(n + m).

**Note:** Method 2 is more efficient for finding the difference between two arrays, as it has a time complexity of O(n + m) compared to O(n * m) for Method 1.


</p>
</details>

###### 24. How can you find the symmetric difference between two arrays?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const array1 = [1, 2, 3, 4, 5];
const array2 = [3, 4, 5, 6, 7];

const symmetricDifference = [
  ...array1.filter(value => !array2.includes(value)),
  ...array2.filter(value => !array1.includes(value))
];
console.log(symmetricDifference); // [1, 2, 6, 7]
```

To find the symmetric difference between two arrays, you can use a combination of the filter and includes methods.

- Time Complexity: O(n * m)
- Explanation: For each element in array1 (of length n), includes() is called on array2 (of length m), resulting in a time complexity of O(n * m) for the first filter. Similarly, for each element in array2, includes() is called on array1, also resulting in a time complexity of O(n * m) for the second filter. Overall, the time complexity is O(n * m).

This approach is not the most efficient for finding the symmetric difference, especially for large arrays, as it has a time complexity of O(n * m). Using sets or other more efficient methods can reduce the time complexity significantly.

</p>
</details>

###### 25. How can you check if two arrays are equal?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const fruits1 = ["apple", "banana", "orange"];
const fruits2 = ["apple", "banana", "orange"];
const fruits3 = ["apple", "mango", "orange"];

// Method 1: toString() (not ideal)
const isEqual1 = fruits1.toString() === fruits2.toString(); // true

// Method 2: JSON.stringify() (better for complex objects)
const isEqual2 = JSON.stringify(fruits1) === JSON.stringify(fruits2); // true
const isEqual3 = JSON.stringify(fruits1) === JSON.stringify(fruits3); // false

// Method 3: length and element comparison (most reliable)
const isEqual4 = fruits1.length === fruits2.length && fruits1.every((val, index) => val === fruits2[index]); // true
const isEqual5 = fruits1.length === fruits3.length && fruits1.every((val, index) => val === fruits3[index]); // false

console.log(isEqual1); // true
console.log(isEqual2); // true
console.log(isEqual3); // false
console.log(isEqual4); // true
console.log(isEqual5); // false
```

- array1.toString() === array2.toString(): Converts both arrays to strings and compares them for equality (may not be reliable for complex objects).
- JSON.stringify(array1) === JSON.stringify(array2): Converts both arrays to JSON strings and compares them for equality (handles nested objects better).
- array1.length === array2.length && array1.every((val, index) => val === array2[index]): Checks if both arrays have the same length and elements at corresponding indices are equal.

### Time Complexity
#### Method 1: toString()
```javascript
const isEqual1 = fruits1.toString() === fruits2.toString(); // true
```
- Time Complexity: O(n)
- Explanation: The toString() method creates a string representation of the array elements, which involves iterating through all elements. Comparing two strings is O(n) where n is the length of the string.

#### Method 2: JSON.stringify()
```javascript
const isEqual2 = JSON.stringify(fruits1) === JSON.stringify(fruits2); // true
const isEqual3 = JSON.stringify(fruits1) === JSON.stringify(fruits3); // false
```
- Time Complexity: O(n)
- Explanation: JSON.stringify() also iterates through all elements of the array to create a JSON string representation. Comparing two JSON strings is O(n) where n is the length of the JSON string.

#### Method 3: length and element comparison
```javascript
const isEqual4 = fruits1.length === fruits2.length && fruits1.every((val, index) => val === fruits2[index]); // true
const isEqual5 = fruits1.length === fruits3.length && fruits1.every((val, index) => val === fruits3[index]); // false
```
- Time Complexity: O(n)
- Explanation: This method compares the lengths of the arrays first (O(1)), then iterates through all elements to compare each element (O(n)). The every() method returns false as soon as it finds a mismatch, so in the worst case, it will iterate through all elements.

In all methods, the time complexity for comparing two arrays is O(n), where n is the length of the arrays.

</p>
</details>

###### 26. How can you check if an array is empty?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the length property
const isEmpty = arr.length === 0;
// Method 2: Using the ! operator with the array
const isEmpty = !arr.length;
```

- array.length === 0: Checks if the length of the array is zero.
- !array.length: Negates the length check for a more concise expression.

### Time Complexity
#### Method 1: Using the length property
```javascript
const isEmpty = arr.length === 0;
```
- Time Complexity: O(1)
- Explanation: Accessing the length property of an array is a constant-time operation. It does not depend on the size of the array and always takes the same amount of time to execute.

#### Method 2: Using the ! operator with the array
```javascript
const isEmpty = !arr.length;
```
- Time Complexity: O(1)
- Explanation: This method also has a constant time complexity. The ! operator is applied to the length property, which is a constant-time operation. The ! operator then converts the length to a boolean, which is also a constant-time operation.

</p>
</details>

###### 27. How can you clone an array in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the spread operator (...)
const clone = [...arr];

// Method 2: Using the slice method
const clone = arr.slice();


const originalArray = [1, 2, 3];

const clonedArray1 = originalArray.slice(0); // [1, 2, 3] (shallow copy)
const clonedArray2 = [...originalArray]; // [1, 2, 3] (shallow copy)
const clonedArray3 = [].concat(originalArray); // [1, 2, 3] (shallow copy)

console.log(clonedArray1); // [1, 2, 3]
console.log(clonedArray2); // [1, 2, 3]
console.log(clonedArray3); // [1, 2, 3]

// Modifying the original array
originalArray[0] = 4;

console.log(clonedArray1); // [4, 2, 3] (shallow copy reflects changes)
console.log(clonedArray2); // [4, 2, 3] (shallow copy reflects changes)
console.log(clonedArray3); // [4, 2, 3] (shallow copy reflects changes)
```
- slice(0): Creates a shallow copy of the entire array using the slice method without arguments.
- spread syntax (...): Spreads the elements of the array into a new array, creating a shallow copy.
- concat([]): Creates a new array by concatenating an empty array with the original array (effectively a shallow copy).

### Time Complexity
#### Method 1: Using the spread operator (...)
```javascript
const clone = [...arr];
```
- Time Complexity: O(n)
- Explanation: The spread operator creates a new array and copies all elements from the original array into the new array. Since it copies each element one by one, the time complexity is linear, where n is the number of elements in the array.
#### Method 2: Using the slice method
```javascript
const clone = arr.slice();
```
- Time Complexity: O(n)
- Explanation: The slice method also creates a new array and copies all elements from the original array into the new array. Similar to the spread operator, it copies each element one by one, resulting in a linear time complexity.

</p>
</details>

###### 28. How can you find the first and last elements of an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const numbers = [10, 20, 30, 40];

const firstElement1 = numbers[0]; // 10
const lastElement1 = numbers[numbers.length - 1]; // 40

const firstElement2 = numbers.slice(0, 1)[0]; // 10 (slice(0, 1) extracts the first element)
const lastElement2 = numbers.slice(-1)[0]; // 40 (slice(-1) extracts the last element)

console.log(firstElement1); // 10
console.log(lastElement1); // 40
console.log(firstElement2); // 10
console.log(lastElement2); // 40
```

- array[0] and array[array.length - 1]: Access the first and last elements directly using their respective indices.
- slice(): Use slice to extract the first and last elements.

### Time Complexity
#### Method 1: Using the spread operator (...)
```javascript
const clone = [...arr];
```
- Time Complexity: O(n)
- Explanation: The spread operator creates a new array and copies all elements from the original array into the new array. Since it copies each element one by one, the time complexity is linear, where n is the number of elements in the array.

#### Method 2: Using the slice method
```javascript
const clone = arr.slice();
```
- Time Complexity: O(n)
- Explanation: The slice method also creates a new array and copies all elements from the original array into the new array. Similar to the spread operator, it copies each element one by one, resulting in a linear time complexity.

</p>
</details>

###### 29. How can you remove the first and last elements of an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the shift and pop methods
arr.shift(); // Remove first element
arr.pop();   // Remove last element

// Method 2: Using array slicing
arr = arr.slice(1, -1); // Remove first and last elements
```
- shift() and pop(): These methods remove and return the first and last elements of the array, respectively, modifying the original array.
- slice(1, -1): This approach creates a new array excluding the first and last elements of the original array.

### Time Complexity
#### Method 1: Using the shift and pop methods
```javascript
// Remove first element
arr.shift();
// Remove last element
arr.pop();
```
- Time Complexity:
    - arr.shift(): O(n)
    - arr.pop(): O(1)
- Explanation:
    - arr.shift(): Removing the first element requires shifting all other elements to the left, which has a linear time complexity.
    - arr.pop(): Removing the last element is a constant-time operation since it only involves updating the array length.
#### Method 2: Using array slicing
```javascript
// Remove first and last elements
arr = arr.slice(1, -1);
```
- Time Complexity: O(n)
- Explanation: Slicing a portion of the array requires iterating over the specified range of elements, which has a linear time complexity.

</p>
</details>

###### 30. How can you remove falsy values from an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the filter method
const filteredArray = arr.filter(Boolean);

// Method 2: Using a for loop
const filteredArray = [];
for (let i = 0; i < arr.length; i++) {
  if (arr[i]) {
    filteredArray.push(arr[i]);
  }
}

// 
const mixedArray = [0, 1, false, null, undefined, 2, 3];

// Removing falsy values
const filteredArray1 = mixedArray.filter(Boolean); // [1, 2, 3]

const filteredArray2 = mixedArray.filter(value => !!value); // [1, 2, 3]

console.log(filteredArray1); // [1, 2, 3]
console.log(filteredArray2); // [1, 2, 3]
```
- filter(Boolean): Filters elements based on truthiness using the Boolean function.
- filter(value => !!value): This approach uses a custom callback function to explicitly check for truthiness with double negation (!!).

### Time Complexity
#### Method 1: Using the filter method
```javascript
const filteredArray = arr.filter(Boolean);
```
- Time Complexity: O(n)
- Explanation: The filter method iterates over each element of the array and applies the Boolean function to determine if the element is truthy. It creates a new array containing only the truthy elements. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array.

Method 2: Using a for loop
```javascript
const filteredArray = [];
for (let i = 0; i < arr.length; i++) {
  if (arr[i]) {
    filteredArray.push(arr[i]);
  }
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates over each element of the array and checks if the element is truthy before adding it to the new array. Similar to the filter method, it iterates over each element once, resulting in a linear time complexity.

Example:
```javascript
const mixedArray = [0, 1, false, null, undefined, 2, 3];
const filteredArray1 = mixedArray.filter(Boolean); // [1, 2, 3]
const filteredArray2 = mixedArray.filter(value => !!value); // [1, 2, 3]

console.log(filteredArray1); // [1, 2, 3]
console.log(filteredArray2); // [1, 2, 3]
```
Both methods produce the same result and have a time complexity of O(n), where n is the number of elements in the array.

</p>
</details>

###### 31. How can you convert an array of strings to lowercase?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const array = ["RED", "GREEN", "bLue"];
// Method 1: Using the map method
const lowercaseArray = array.map(str => str.toLowerCase());

// Method 2: Using a for loop
const lowercaseArray = [];
for (let i = 0; i < array.length; i++) {
  lowercaseArray.push(array[i].toLowerCase());
}

// Method 3: Modifying the original array (not recommended)
array.forEach(string => string.toLowerCase()); // Modifies elements in-place

console.log(array); // ["red", "green", "blue"] (modified if forEach is used)
```
- map(string => string.toLowerCase()): Uses the map method and a callback function to convert each string to lowercase.
- forEach(string => string.toLowerCase()): Iterates through the array using forEach and applies lowercase conversion to each element, modifying the original array.

### Time Complexity
#### Method 1: Using the map method
```javascript
const lowercaseArray = array.map(str => str.toLowerCase());
```
- Time Complexity: O(n)
- Explanation: The map method iterates over each element of the array and applies the toLowerCase method to convert each string to lowercase. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array.

#### Method 2: Using a for loop
```javascript
const lowercaseArray = [];
for (let i = 0; i < array.length; i++) {
  lowercaseArray.push(array[i].toLowerCase());
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates over each element of the array and uses the toLowerCase method to convert each string to lowercase before adding it to the new array. Similar to the map method, it iterates over each element once, resulting in a linear time complexity.

#### Method 3: Modifying the original array (not recommended)
```javascript
array.forEach(string => string.toLowerCase());
```
- Time Complexity: O(n)
- Explanation: The forEach method iterates over each element of the array and applies the toLowerCase method to each string. However, it does not create a new array but modifies the elements in-place. While the time complexity remains O(n) because it still iterates over each element once, modifying the original array is not recommended as it can lead to unexpected behavior and makes the code less readable.

Example:
```javascript
const array = ["RED", "GREEN", "bLue"];
const lowercaseArray = array.map(str => str.toLowerCase());

console.log(lowercaseArray); // ["red", "green", "blue"]
```
All three methods produce the same result, but the first two are recommended for creating a new array with the lowercase strings, while the third method should be avoided for modifying the original array in-place.

</p>
</details>

###### 32. How can you convert an array of strings to uppercase?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the map method
const uppercaseArray = array.map(str => str.toUpperCase());

// Method 2: Using a for loop
const uppercaseArray = [];
for (let i = 0; i < array.length; i++) {
  uppercaseArray.push(array[i].toUpperCase());
}

// Method 3: Modifying the original array (not recommended)
colors.forEach(string => string.toLowerCase()); // Modifies elements in-place
console.log(colors); // ["red", "green", "blue"] (modified if forEach is used)
```

- map(string => string.toLowerCase()): Uses the map method and a callback function to convert each string to lowercase.
- forEach(string => string.toLowerCase()): Iterates through the array using forEach and applies lowercase conversion to each element, modifying the original array.

### Time Complexity
#### Method 1: Using the map method
```javascript
const uppercaseArray = array.map(str => str.toUpperCase());
```
- Time Complexity: O(n)
- Explanation: The map method iterates over each element of the array and applies the toUpperCase method to convert each string to uppercase. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array.

#### Method 2: Using a for loop
```javascript
const uppercaseArray = [];
for (let i = 0; i < array.length; i++) {
  uppercaseArray.push(array[i].toUpperCase());
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates over each element of the array and uses the toUpperCase method to convert each string to uppercase before adding it to the new array. Similar to the map method, it iterates over each element once, resulting in a linear time complexity.

#### Method 3: Modifying the original array (not recommended)
```javascript
colors.forEach(string => string.toUpperCase());
```
- Time Complexity: O(n)
- Explanation: The forEach method iterates over each element of the array and applies the toUpperCase method to each string. However, it does not create a new array but modifies the elements in-place. While the time complexity remains O(n) because it still iterates over each element once, modifying the original array is not recommended as it can lead to unexpected behavior and makes the code less readable.

Example:
```javascript
const array = ["red", "green", "blue"];
const uppercaseArray = array.map(str => str.toUpperCase());

console.log(uppercaseArray); // ["RED", "GREEN", "BLUE"]
```
All three methods produce the same result, but the first two are recommended for creating a new array with the uppercase strings, while the third method should be avoided for modifying the original array in-place.

</p>
</details>

###### 33. How can you convert an array of strings to title case?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const array = ["RED", "GREEN", "bLue"];
// Method 1: Using the map method with a custom function
const toTitleCase = str => str.charAt(0).toUpperCase() + str.slice(1).toLowerCase();
const titleCaseArray = array.map(toTitleCase);
// Method 2: Using a for loop with a custom function
const titleCaseArray1 = [];
for (let i = 0; i < array.length; i++) {
  titleCaseArray1.push(array[i].charAt(0).toUpperCase() + array[i].slice(1).toLowerCase());
}

const phrases = ["hello world", "hOw aRE you"];

const titleCasePhrases = phrases.map(string => 
  string.replace(/\w\S*/g, txt => txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase())); // ["Hello World", "How Are You"]

console.log(titleCasePhrases); // ["Hello World", "How Are You"]
```
map(string => string.replace(/\w\S*/g, txt => txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase())): Uses map with a complex regular expression to convert each string to title case.

### Time Complexity
#### Method 1: Using the map method with a custom function
```javascript
const toTitleCase = str => str.charAt(0).toUpperCase() + str.slice(1).toLowerCase();
const titleCaseArray = array.map(toTitleCase);
```
- Time Complexity: O(n)
- Explanation: The map method iterates over each element of the array and applies the custom toTitleCase function to convert each string to title case. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array.

#### Method 2: Using a for loop with a custom function
```javascript
const titleCaseArray1 = [];
for (let i = 0; i < array.length; i++) {
  titleCaseArray1.push(array[i].charAt(0).toUpperCase() + array[i].slice(1).toLowerCase());
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates over each element of the array and uses a custom function to convert each string to title case before adding it to the new array. Similar to the map method, it iterates over each element once, resulting in a linear time complexity.

Example:
```javascript
const array = ["RED", "GREEN", "bLue"];
const toTitleCase = str => str.charAt(0).toUpperCase() + str.slice(1).toLowerCase();
const titleCaseArray = array.map(toTitleCase);

console.log(titleCaseArray); // ["Red", "Green", "Blue"]
```

Both methods produce the same result, but the first method using the map method with a custom function is more concise and easier to read.

</p>
</details>

###### 34. How can you convert an array of numbers to strings?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the map method
const stringArray = array.map(num => String(num));

// Method 2: Using a for loop
const stringArray = [];
for (let i = 0; i < array.length; i++) {
  stringArray.push(String(array[i]));
}
```

map(number => number.toString()): Uses map and a callback function to convert each number to a string using toString.

### Time Complexity
#### Method 1: Using the map method
```javascript
const stringArray = array.map(num => String(num));
```
- Time Complexity: O(n)
- Explanation: The map method iterates over each element of the array and applies the String conversion function to convert each number to a string. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array.

#### Method 2: Using a for loop
```javascript
const stringArray = [];
for (let i = 0; i < array.length; i++) {
  stringArray.push(String(array[i]));
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates over each element of the array and uses the String conversion function to convert each number to a string before adding it to the new array. Similar to the map method, it iterates over each element once, resulting in a linear time complexity.

Both methods produce the same result, but the first method using the map method is more concise and easier to read.

</p>
</details>

###### 35. How can you convert an array of strings to numbers?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the map method
const numberArray = array.map(str => Number(str));

// Method 2: Using a for loop
const numberArray = [];
for (let i = 0; i < array.length; i++) {
  numberArray.push(Number(array[i]));
}

const stringNumbers = ["10", "twenty", "30"];

const numbers1 = stringNumbers.map(string => Number(string)); // [10, NaN, 30] ("twenty" cannot be converted to a number)

console.log(numbers1); // [10, NaN, 30]

// Additional check for valid conversion
const numbers2 = stringNumbers.map(string => {
  const parsedNumber = Number(string);
  return !isNaN(parsedNumber) ? parsedNumber : null; // Handle invalid conversion
});

console.log(numbers2); // [10, null, 30]
```

map(string => Number(string)): Uses map and a callback function to convert each string to a number using the Number constructor. Note that this might lead to unexpected results if the string is not a valid number.

### Time Complexity
#### Method 1: Using the map method
```javascript
const numberArray = array.map(str => Number(str));
```
- Time Complexity: O(n)
- Explanation: The map method iterates over each element of the array and applies the Number conversion function to convert each string to a number. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array.

#### Method 2: Using a for loop
```javascript
const numberArray = [];
for (let i = 0; i < array.length; i++) {
  numberArray.push(Number(array[i]));
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates over each element of the array and uses the Number conversion function to convert each string to a number before adding it to the new array. Similar to the map method, it iterates over each element once, resulting in a linear time complexity.

Example:
```javascript
const stringNumbers = ["10", "twenty", "30"];
const numbers = stringNumbers.map(string => Number(string));

console.log(numbers); // [10, NaN, 30]
```
In both methods, if there are invalid strings that cannot be converted to numbers, like "twenty" in the example, the result will include NaN (Not-a-Number) for those elements. To handle such cases, an additional check for valid conversion can be added, as shown in the example.

</p>
</details>

###### 36. How can you convert an array of strings to booleans?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the map method
const booleanArray = array.map(str => str.toLowerCase() === 'true');

// Method 2: Using a for loop
const booleanArray = [];
for (let i = 0; i < array.length; i++) {
  booleanArray.push(array[i].toLowerCase() === 'true');
}
// method 3: Double Negation
const boolValues2 = truthValues.map(string => !!string); // [true, true, true] (might be misleading)
console.log(boolValues2); // [true, true, true]
```
- Uses double negation (!!) to coerce strings to booleans. However, this might not be ideal for all cases (e.g., "0" becomes true).
- The first method explicitly checks for lowercase "true" to ensure accurate conversion.
- The second method leverages double negation, which coerces any non-empty string to true and empty strings to false. This might lead to unexpected results if you expect strict boolean conversions.

### Time Complexity
#### Method 1: Using the map method
```javascript
const booleanArray = array.map(str => str.toLowerCase() === 'true');
```
- Time Complexity: O(n)
- Explanation: The map method iterates over each element of the array and applies the comparison operation (str.toLowerCase() === 'true') to convert each string to a boolean value. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array.

#### Method 2: Using a for loop
```javascript
const booleanArray = [];
for (let i = 0; i < array.length; i++) {
  booleanArray.push(array[i].toLowerCase() === 'true');
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates over each element of the array and uses the comparison operation to convert each string to a boolean value before adding it to the new array. Similar to the map method, it iterates over each element once, resulting in a linear time complexity.

#### Method 3: Double Negation
```javascript
const boolValues2 = truthValues.map(string => !!string);
```
- Time Complexity: O(n)
- Explanation: The double negation (!!) is used to convert truthy and falsy values to true and false respectively. While this method is concise, it might be misleading as it converts all truthy values to true, including non-empty strings, which may not be the intended behavior.

</p>
</details>

###### 37. How can you convert an array of booleans to strings?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the map method
const stringArray = array.map(bool => String(bool));

// Method 2: Using a for loop
const stringArray = [];
for (let i = 0; i < array.length; i++) {
  stringArray.push(String(array[i]));
}

// Method 3
const booleans = [true, false, true];

const stringBooleans = booleans.map(bool => bool.toString()); // ["true", "false", "true"]
console.log(stringBooleans); // ["true", "false", "true"]
```

toString() (map): Uses map to convert each boolean to a string using toString.

### Time Complexity
#### Method 1: Using the map method
```javascript
const stringArray = array.map(bool => String(bool));
```
- Time Complexity: O(n)
- Explanation: The map method iterates over each element of the array and converts each boolean to a string using the String constructor. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array.

#### Method 2: Using a for loop
```javascript
const stringArray = [];
for (let i = 0; i < array.length; i++) {
  stringArray.push(String(array[i]));
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates over each element of the array and uses the String constructor to convert each boolean to a string before adding it to the new array. Similar to the map method, it iterates over each element once, resulting in a linear time complexity.

#### Method 3:
```javascript
const booleans = [true, false, true];

const stringBooleans = booleans.map(bool => bool.toString()); // ["true", "false", "true"]
console.log(stringBooleans); // ["true", "false", "true"]
```

This method uses the toString method directly on each boolean element to convert it to a string. Since it also iterates over each element once, the time complexity is O(n), where n is the number of elements in the array.

</p>
</details>

###### 38. How can you convert an array of booleans to numbers?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the map method
const numberArray = array.map(bool => bool ? 1 : 0);

// Method 2: Using a for loop
const numberArray = [];
for (let i = 0; i < array.length; i++) {
  numberArray.push(array[i] ? 1 : 0);
}

// Method 3
const numberBooleans = booleans.map(bool => Number(bool)); // [1, 0, 1]
console.log(numberBooleans); // [1, 0, 1]
```

Number() (map): Leverages map and the Number constructor to convert booleans to numbers (true becomes 1, false becomes 0).

### Time Complexity
#### Method 1: Using the map method
```javascript
const numberArray = array.map(bool => bool ? 1 : 0);
```
- Time Complexity: O(n)
- Explanation: The map method iterates over each element of the array and converts each boolean to a number (0 or 1) based on the ternary condition. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array.

#### Method 2: Using a for loop
```javascript
const numberArray = [];
for (let i = 0; i < array.length; i++) {
  numberArray.push(array[i] ? 1 : 0);
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates over each element of the array and uses a ternary condition to convert each boolean to a number (0 or 1) before adding it to the new array. Similar to the map method, it iterates over each element once, resulting in a linear time complexity.

#### Method 3:
```javascript
const numberBooleans = booleans.map(bool => Number(bool)); // [1, 0, 1]
console.log(numberBooleans); // [1, 0, 1]
```

This method uses the Number constructor directly on each boolean element to convert it to a number. Since it also iterates over each element once, the time complexity is O(n), where n is the number of elements in the array.

</p>
</details>

###### 39. How can you find the sum of all numbers in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const array = [10, 20, 30];

// Method 1: Using the reduce method
const sum = array.reduce((acc, curr) => acc + curr, 0);

// Method 2: Using a for loop
let sum = 0;
for (let i = 0; i < array.length; i++) {
  sum += array[i];
}

// Method 3: Using for...of
const sum2 = 0;
for (const num of numbers) {
  sum2 += num;
}
console.log(sum2); // 60
```

- reduce(): Uses the reduce method with an initial value of 0 as the accumulator (acc) and a callback function that adds each element (num) to the accumulator.
- for...of loop: Iterates through the array using a loop, keeping track of the sum in a variable.

### Time Complexity
#### Method 1: Using the reduce method
```javascript
const sum = array.reduce((acc, curr) => acc + curr, 0);
```
- Time Complexity: O(n)
- Explanation: The reduce method iterates over each element of the array once, adding it to the accumulator (acc). Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array.

#### Method 2: Using a for loop
```javascript
let sum = 0;
for (let i = 0; i < array.length; i++) {
  sum += array[i];
}
```
- Time Complexity: O(n)
- Explanation: The for loop iterates over each element of the array once, adding it to the sum. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array.

#### Method 3: Using for...of
```javascript
let sum2 = 0;
for (const num of array) {
  sum2 += num;
}
```
- Time Complexity: O(n)
- Explanation: The for...of loop iterates over each element of the array once, adding it to the sum. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array.

</p>
</details>

###### 40. How can you find the average of all numbers in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the reduce method
const sum = array.reduce((acc, curr) => acc + curr, 0);
const average = sum / array.length;

// Method 2: Using a for loop
let sum = 0;
for (let i = 0; i < array.length; i++) {
  sum += array[i];
}
const average = sum / array.length;

// method 3
const average = (numbers.reduce((acc, num) => acc + num, 0) / numbers.length).toFixed(2); // 20.00
console.log(average); // 20.00
```

This approach combines reduce to find the sum and divides by the array length to get the average. Rounding to two decimal places using toFixed(2) is optional.

### Time Complexity
#### Method 1: Using the reduce method
```javascript
const sum = array.reduce((acc, curr) => acc + curr, 0);
const average = sum / array.length;
```
- Time Complexity: O(n)
- Explanation: The reduce method iterates over each element of the array once to calculate the sum. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array. Calculating the average by dividing the sum by the length of the array is a constant time operation, so it doesn't affect the overall time complexity.

#### Method 2: Using a for loop
```javascript
let sum = 0;
for (let i = 0; i < array.length; i++) {
  sum += array[i];
}
const average = sum / array.length;
```
- Time Complexity: O(n)
- Explanation: The for loop iterates over each element of the array once to calculate the sum. Since it iterates over each element once, the time complexity is linear, where n is the number of elements in the array. Calculating the average by dividing the sum by the length of the array is a constant time operation, so it doesn't affect the overall time complexity.

#### Method 3: Using reduce and toFixed
```javascript
const average = (numbers.reduce((acc, num) => acc + num, 0) / numbers.length).toFixed(2);
console.log(average); // 20.00
```
- Time Complexity: O(n)
- Explanation: The reduce method is used to calculate the sum of numbers in the array, which has a time complexity of O(n), where n is the number of elements in the array. Dividing the sum by the length of the array is a constant time operation. The toFixed(2) method is also a constant time operation as it always formats the number to two decimal places, irrespective of the array size.

</p>
</details>
