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