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

###### 6. How can you remove the element at specific index from an array in JavaScript?
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

###### 7. How do you merge two arrays into one in JavaScript?
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

###### 8. How do you sort an array of numbers in both ascending and descending order in JavaScript?
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

###### 9. How can you reverse an array using both a mutating method and a non-mutating method?
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

###### 10. How can you split a string into individual characters and words using split() and Array.from()?
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

### Using Array.flat():
```javascript
const nestedArray = [1, [2, [3, 4], 5], 6];
const flattenedArray = nestedArray.flat(Infinity);
// flattenedArray: [1, 2, 3, 4, 5, 6]
```
Time Complexity: O(n), where n is the total number of elements in the nested array. The flat() method flattens the array in one pass.

### Using Recursion:
```javascript
function flattenArray(arr) {
  return arr.reduce((acc, val) => Array.isArray(val) ? acc.concat(flattenArray(val)) : acc.concat(val), []);
}

const nestedArray = [1, [2, [3, 4], 5], 6];
const flattenedArray = flattenArray(nestedArray);
// flattenedArray: [1, 2, 3, 4, 5, 6]
```
Time Complexity: O(n), where n is the total number of elements in the nested array. The recursive approach traverses each element once.

### Using Array.reduce() with concat():
```javascript
function flattenArray(arr) {
  return arr.reduce((acc, val) => acc.concat(Array.isArray(val) ? flattenArray(val) : val), []);
}

const nestedArray = [1, [2, [3, 4], 5], 6];
const flattenedArray = flattenArray(nestedArray);
// flattenedArray: [1, 2, 3, 4, 5, 6]
```
Time Complexity: O(n), similar to the recursive approach, this approach also traverses each element once.

### Using Array.prototype.flat() and Array.prototype.concat():
```javascript
const nestedArray = [1, [2, [3, 4], 5], 6];
const flattenedArray = [].concat(...nestedArray);
// flattenedArray: [1, 2, [3, 4], 5, 6]
```
Time Complexity: O(n), where n is the total number of elements in the nested array. The spread operator (...) and concat() method flatten the array in one pass.

### Using Iteration:
```javascript
function flattenArray(arr) {
  const stack = [...arr];
  const result = [];
  while (stack.length) {
    const next = stack.pop();
    if (Array.isArray(next)) {
      stack.push(...next);
    } else {
      result.push(next);
    }
  }
  return result.reverse();
}

const nestedArray = [1, [2, [3, 4], 5], 6];
const flattenedArray = flattenArray(nestedArray);
// flattenedArray: [1, 2, 3, 4, 5, 6]
```
Time Complexity: O(n), where n is the total number of elements in the nested array. This iterative approach processes each element once.

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

Using reduce() and includes():

```javascript
function intersection(arr1, arr2) {
  return arr1.reduce((acc, value) => {
    if (arr2.includes(value)) {
      acc.push(value);
    }
    return acc;
  }, []);
}

const arr1 = [1, 2, 3, 4, 5];
const arr2 = [3, 4, 5, 6, 7];
const result = intersection(arr1, arr2);
// result: [3, 4, 5]
```
Time Complexity: O(nm), similar to the first approach, this method also has a time complexity of O(nm).

Using Set and forEach():

```javascript
function intersection(arr1, arr2) {
  const set2 = new Set(arr2);
  const result = new Set();
  arr1.forEach(value => {
    if (set2.has(value)) {
      result.add(value);
    }
  });
  return [...result];
}

const arr1 = [1, 2, 3, 4, 5];
const arr2 = [3, 4, 5, 6, 7];
const result = intersection(arr1, arr2);
// result: [3, 4, 5]
```
Time Complexity: O(n+m), similar to the second approach, this method also has a time complexity of O(n+m).

```javascript
const colors1 = ["red", "green", "blue"];
const colors2 = ["blue", "purple", "yellow"];

// Method 1: Set intersection with has()
const intersection1 = Array.from(new Set(colors1)).filter(x => new Set(colors2).has(x)); // ["blue"]

// Method 2: filter() with includes()
const intersection2 = colors1.filter(color => colors2.includes(color)); // ["blue"]

console.log(intersection1); // ["blue"]
console.log(intersection2); // ["blue"]

// Method 3: Set with includes()
const intersectionSet = new Set(colors1.filter(value => colors2.includes(value)));
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
const union2 = [...new Set(numbers1.concat(numbers2))]; // [ 1, 2, 3, 4 ]

console.log(union1); // [1, 2, 3, 4]
console.log(union2); // [1, 2, 3, 2, 3, 4]

const unionSet = new Set([...numbers1, ...numbers2]);
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
const set1 = new Set(letters1);
const set2 = new Set(letters2);
set2.forEach(letter => set1.delete(letter));
const difference2 = Array.from(set1); // ["a", "d"]

console.log(difference1); // ["a", "d"]
console.log(difference2); // ["a", "d"]
```

- Method 1:
    - Time Complexity: O(n * m), where n is the number of elements in letters1 and m is the number of elements in letters2.
- Method 2:
    - Time Complexity: O(n + m), where n is the number of elements in letters1 and m is the number of elements in letters2.

</p>
</details>

###### 24. How can you find the symmetric difference between two arrays?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const array1 = ["a", "b", "c", "d"];
const array2 = ["b", "c", "e"];

const symmetricDifference = [
  ...array1.filter(value => !array2.includes(value)),
  ...array2.filter(value => !array1.includes(value))
];
console.log(symmetricDifference); [ 'a', 'd', 'e' ]
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

## Deep Cloning

### Using JSON methods: 
This method works well for arrays or objects containing only JSON-serializable data (no functions or prototype objects). However, it does not support custom serialization/deserialization logic.
```javascript
const originalArray = [[1, 2, 3], [4, 5, 6], [7, 8, 9]];
const deepCloneArray = JSON.parse(JSON.stringify(originalArray));
```
Time Complexity: O(n), where n is the total number of elements in the array and its nested arrays. The stringify and parse operations each iterate over all elements once.

### Using recursion:
```javascript
function deepCloneArray(array) {
  return array.map(element => Array.isArray(element) ? deepCloneArray(element) : element);
}

const originalArray = [[1, 2, 3], [4, 5, 6], [7, 8, 9]];
const deepCloneArray = deepCloneArray(originalArray);
```
Time Complexity: O(n), where n is the total number of elements in the array and its nested arrays. The map function iterates over each element once, and the recursive call also iterates over all elements once.

### Using a library like Lodash:
```javascript
const _ = require('lodash');
const originalArray = [[1, 2, 3], [4, 5, 6], [7, 8, 9]];
const deepCloneArray = _.cloneDeep(originalArray);
```
Time Complexity: O(n), where n is the total number of elements in the array and its nested arrays. Lodash's cloneDeep function iterates over each element once.

### Using the spread operator (for shallow cloning only):
```javascript
const originalArray = [[1, 2, 3], [4, 5, 6], [7, 8, 9]];
const deepCloneArray = originalArray.map(subArray => [...subArray]);
```
Time Complexity: O(n), where n is the total number of elements in the array and its nested arrays. The map function iterates over each element once, and the spread operator creates a shallow copy of each nested array.

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
colors.forEach(string => string.toUpperCase()); // Modifies elements in-place
console.log(colors); // ["red", "green", "blue"] (modified if forEach is used)
```

- map(string => string.toUpperCase()): Uses the map method and a callback function to convert each string to uppercase.
- forEach(string => string.toUpperCase()): Iterates through the array using forEach and applies uppercase conversion to each element, modifying the original array.

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
`map(string => string.replace(/\w\S*/g, txt => txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase()))`: Uses map with a complex regular expression to convert each string to title case.

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

`map(number => number.toString())`: Uses map and a callback function to convert each number to a string using toString.

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
const array = ['2','4','7']

// Method 1: Using the map method
const numberArray1 = array.map(str => Number(str));
console.log(numberArray1)

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

`map(string => Number(string))`: Uses map and a callback function to convert each string to a number using the Number constructor. Note that this might lead to unexpected results if the string is not a valid number.

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
const array = ['a','','bvc','23','3er','tyt6'];

// Method 1: Using the map method
const booleanArray1 = array.map(str => str.toLowerCase() === 'true');
console.log(booleanArray1);

// Method 2: Using a for loop
const booleanArray = [];
for (let i = 0; i < array.length; i++) {
  booleanArray.push(array[i].toLowerCase() === 'true');
}

// method 3: Double Negation
const boolValues2 = array.map(string => !!string); // [true, true, true] (might be misleading)
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

- toString() (map): Uses map to convert each boolean to a string using toString.

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

- Number() (map): Leverages map and the Number constructor to convert booleans to numbers (true becomes 1, false becomes 0).

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
- Time Complexity: O(n)
- Explanation: This method uses the Number constructor directly on each boolean element to convert it to a number. Since it also iterates over each element once, the time complexity is O(n), where n is the number of elements in the array.

</p>
</details>

###### 39. How can you find the sum of all numbers in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const array = [10, 20, 30];

// Method 1: Using the reduce method
const sum1 = array.reduce((acc, curr) => acc + curr, 0);
console.log(sum1); // 60
// Method 2: Using a for loop
let sum = 0;
for (let i = 0; i < array.length; i++) {
  sum += array[i];
}
console.log(sum); // 60
// Method 3: Using for...of
let sum2 = 0;
for (const num of array) {
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
let array = [2,5,7,3,4,8]

// Method 1: Using the reduce method
const sum1 = array.reduce((acc, curr) => acc + curr, 0);
const average1 = sum1 / array.length;
console.log(average1); // 4.83

// Method 2: Using a for loop
let sum2 = 0;
for (let i = 0; i < array.length; i++) {
  sum2 += array[i];
}
const average2 = sum2 / array.length;
console.log(average2); // 4.83

// Method 3
const average = (array.reduce((acc, num) => acc + num, 0) / array.length).toFixed(2); // 4.83
console.log(average); // 4.83
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

###### 41. How can you find the median of all numbers in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the sort method and conditional logic
const sortedArray = array.sort((a, b) => a - b);
const length = sortedArray.length;
const median = length % 2 === 0 ? (sortedArray[length / 2 - 1] + sortedArray[length / 2]) / 2 : sortedArray[Math.floor(length / 2)];

// Method 2: Using the reduce method to calculate the sum and then finding the median
const sum = array.reduce((acc, curr) => acc + curr, 0);
const median = sum / array.length;

// Method 3:
const numbers = [10, 20, 30, 5, 15]; // Even length
const sortedNumbers = numbers.slice().sort((a, b) => a - b); // Sort a copy to avoid modifying the original array
const median1 = (sortedNumbers[sortedNumbers.length / 2 - 1] + sortedNumbers[sortedNumbers.length / 2]) / 2; // Average of middle two elements
console.log(median1); // 15.0
const numbers2 = [10, 20, 30, 5]; // Odd length
const sortedNumbers2 = numbers2.slice().sort((a, b) => a - b);
const median2 = sortedNumbers2[Math.floor(sortedNumbers2.length / 2)]; // Middle element
console.log(median2); // 15
```

- Sorting and indexing (for even and odd lengths): Sorts the array and accesses the middle element(s) for the median.
- For even-length arrays, the median is the average of the two middle elements after sorting.
- For odd-length arrays, the median is the single middle element after sorting.

### Time Complexity
#### Method 1: Using the sort method and conditional logic
```javascript
const sortedArray = array.sort((a, b) => a - b);
const length = sortedArray.length;
const median = length % 2 === 0 ? (sortedArray[length / 2 - 1] + sortedArray[length / 2]) / 2 : sortedArray[Math.floor(length / 2)];
```
- Time Complexity: O(n log n)
- Explanation: The sort method has an average time complexity of O(n log n), where n is the number of elements in the array. After sorting, finding the median involves simple array access, which is a constant time operation.

#### Method 2: Using the reduce method to calculate the sum and then finding the median
```javascript
const sum = array.reduce((acc, curr) => acc + curr, 0);
const median = sum / array.length;
```
- Time Complexity: O(n)
- Explanation: Calculating the sum of all elements in the array using reduce is a linear operation, as it iterates over each element of the array once. Dividing the sum by the length of the array to find the average is also a constant time operation.

#### Method 3: Sorting a copy of the array and calculating the median
```javascript
const sortedNumbers = numbers.slice().sort((a, b) => a - b); // Sort a copy to avoid modifying the original array
const median1 = (sortedNumbers[sortedNumbers.length / 2 - 1] + sortedNumbers[sortedNumbers.length / 2]) / 2; // Average of middle two elements
console.log(median1); // 15.0

const sortedNumbers2 = numbers2.slice().sort((a, b) => a - b);
const median2 = sortedNumbers2[Math.floor(sortedNumbers2.length / 2)]; // Middle element
console.log(median2); // 15
```
- Time Complexity: O(n log n)
- Explanation: Similar to Method 1, sorting the array using the sort method has a time complexity of O(n log n). Calculating the median afterward is a constant time operation, as it involves accessing specific elements of the sorted array.

</p>
</details>

###### 42. How can you find the mode of all numbers in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using an object to store frequencies
const freq = {};
array.forEach(num => {
  freq[num] = (freq[num] || 0) + 1;
});
const mode = Object.keys(freq).reduce((a, b) => freq[a] > freq[b] ? a : b);

// Method 2: Using the reduce method to find the most common element
const mode = array.reduce((a, b, i, arr) =>
  (arr.filter(v => v === a).length >= arr.filter(v => v === b).length ? a : b), null);
  

// Method 3: 
const numbers = [10, 20, 30, 10, 10, 20];

const frequency = {};
for (const num of numbers) {
  frequency[num] = (frequency[num] || 0) + 1; // Initialize count if not present
}

let mode = null;
let maxCount = 0;
for (const num in frequency) {
  if (frequency[num] > maxCount) {
    mode = num;
    maxCount = frequency[num];
  }
}

console.log(mode); // 10 (if multiple elements have the same max frequency, any one can be considered the mode)
```

- Object to store frequency and finding the max frequency: Creates an object to store the frequency of each element and finds the element with the highest frequency (mode).
- Explanation:
    - The code iterates through the array, building an object where keys are numbers and values are their frequencies.
    - It then iterates through the frequency object to find the element with the highest count (mode).

### Time Complexity
#### Method 1: Using an object to store frequencies
```javascript
const freq = {};
array.forEach(num => {
  freq[num] = (freq[num] || 0) + 1;
});
const mode = Object.keys(freq).reduce((a, b) => freq[a] > freq[b] ? a : b);
```
- Time Complexity: O(n)
- Explanation: This method iterates over the array once to count the frequency of each element, resulting in a linear time complexity, where n is the number of elements in the array. The final step of finding the mode by iterating over the keys of the frequency object is also a linear operation.

#### Method 2: Using the reduce method to find the most common element
```javascript
const mode = array.reduce((a, b, i, arr) =>
  (arr.filter(v => v === a).length >= arr.filter(v => v === b).length ? a : b), null);
```
- Time Complexity: O(n^2)
- Explanation: This method uses nested filter functions inside the reduce function. Each filter function iterates over the entire array to count occurrences of a specific value, resulting in a quadratic time complexity, where n is the number of elements in the array.

#### Method 3: Using a for loop to find the mode
```javascript
const frequency = {};
for (const num of numbers) {
  frequency[num] = (frequency[num] || 0) + 1; // Initialize count if not present
}

let mode = null;
let maxCount = 0;
for (const num in frequency) {
  if (frequency[num] > maxCount) {
    mode = num;
    maxCount = frequency[num];
  }
}
```
- Time Complexity: O(n)
- Explanation: This method also iterates over the array once to count the frequency of each element, resulting in a linear time complexity. The final step of finding the mode by iterating over the keys of the frequency object is also a linear operation.

</p>
</details>

###### 43. How can you find the frequency of each element in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using an object to store frequencies
const freq = {};
array.forEach(num => {
  freq[num] = (freq[num] || 0) + 1;
});

// Method 2:
const numbers = [10, 20, 30, 10, 10, 20];

const frequency = {};
for (const num of numbers) {
  frequency[num] = (frequency[num] || 0) + 1; // Initialize count if not present
}

let mode = null;
let maxCount = 0;
for (const num in frequency) {
  if (frequency[num] > maxCount) {
    mode = num;
    maxCount = frequency[num];
  }
}

console.log(mode); // 10 (if multiple elements have the same max frequency, any one can be considered the mode)
```
- Object to store frequency and finding the max frequency: Creates an object to store the frequency of each element and finds the element with the highest frequency (mode).
- Explanation:
    - The code iterates through the array, building an object where keys are numbers and values are their frequencies.
    - It then iterates through the frequency object to find the element with the highest count (mode).

### Time Complexity
#### Method 1: Using an object to store frequencies
```javascript
const freq = {};
array.forEach(num => {
  freq[num] = (freq[num] || 0) + 1;
});
```
- Time Complexity: O(n)
- Explanation: This method iterates over the array once to count the frequency of each element, resulting in a linear time complexity, where n is the number of elements in the array.

#### Method 2:
```javascript
const frequency = {};
for (const num of numbers) {
  frequency[num] = (frequency[num] || 0) + 1; // Initialize count if not present
}

let mode = null;
let maxCount = 0;
for (const num in frequency) {
  if (frequency[num] > maxCount) {
    mode = num;
    maxCount = frequency[num];
  }
}
```
- Time Complexity: O(n)
- Explanation: This method also iterates over the array once to count the frequency of each element, resulting in a linear time complexity. The final step of finding the mode by iterating over the keys of the frequency object is also a linear operation.

</p>
</details>

###### 44. How can you find the second highest and second lowest numbers in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the sort method
const sortedArray = array.sort((a, b) => a - b);
const secondHighest = sortedArray[sortedArray.length - 2];
const secondLowest = sortedArray[1];

// Method 2:
const numbers = [10, 20, 30, 5, 15];
const sortedNumbers = numbers.slice().sort((a, b) => a - b); // Sort a copy

const secondHighest = sortedNumbers[sortedNumbers.length - 2]; // Second-to-last element
const secondLowest = sortedNumbers[1]; // Second element

console.log(secondHighest); // 20
console.log(secondLowest); // 10

// Alternative with potential modification (avoiding duplicates)
const uniqueNumbers = [...new Set(numbers)]; // Remove duplicates using Set
uniqueNumbers.sort((a, b) => a - b);

const secondHighest2 = uniqueNumbers.length > 1 ? uniqueNumbers[uniqueNumbers.length - 2] : null; // Handle cases with less than 2 unique elements
const secondLowest2 = uniqueNumbers.length > 1 ? uniqueNumbers[1] : null;

console.log(secondHighest2); // 20 (if duplicates exist)
console.log(secondLowest2); // 10 (if duplicates exist)
```

- Uses double negation (!!) to coerce strings to booleans. However, this might not be ideal for all cases (e.g., "0" becomes true).
- The first method explicitly checks for lowercase "true" to ensure accurate conversion.
- The second method leverages double negation, which coerces any non-empty string to true and empty strings to false. This might lead to unexpected results if you expect strict boolean conversions.

### Time Complexity
#### Method 1: Using the sort method
```javascript
const sortedArray = array.sort((a, b) => a - b);
const secondHighest = sortedArray[sortedArray.length - 2];
const secondLowest = sortedArray[1];
```
- Time Complexity: O(n log n)
- Explanation: The sort method typically has an average time complexity of O(n log n), where n is the number of elements in the array. Accessing the second highest and second lowest elements after sorting is O(1), so the dominant factor is the sorting operation.

#### Method 2:
```javascript
const sortedNumbers = numbers.slice().sort((a, b) => a - b); // Sort a copy

const secondHighest = sortedNumbers[sortedNumbers.length - 2]; // Second-to-last element
const secondLowest = sortedNumbers[1]; // Second element
```
- Time Complexity: O(n log n)
- Explanation: Similar to Method 1, this method involves sorting the array, which has a time complexity of O(n log n).

The alternative method that removes duplicates using a Set before sorting also has a time complexity of O(n log n) due to the sorting operation.

</p>
</details>

###### 45. How can you find the most common element in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the reduce method to find the most common element
const mode = array.reduce((a, b, i, arr) =>
  (arr.filter(v => v === a).length >= arr.filter(v => v === b).length ? a : b), null);

// Method 2: 
const numbers = [10, 20, 30, 10, 10, 20];

const frequency = {};
for (const num of numbers) {
  frequency[num] = (frequency[num] || 0) + 1; // Initialize count if not present
}

let mostCommon = null;
let maxCount = 0;
for (const num in frequency) {
  if (frequency[num] > maxCount) {
    mostCommon = num;
    maxCount = frequency[num];
  }
}

console.log(mostCommon); // 10 (most frequent element)

// Method 3: 
const numbers = [10, 20, 30, 10, 10, 20];

const frequency = numbers.reduce((acc, num) => {
  acc[num] = (acc[num] || 0) + 1;
  return acc;
}, {}); // Initialize accumulator as an empty object

let mostCommon = null;
let maxCount = 0;
for (const num in frequency) {
  if (frequency[num] > maxCount) {
    mostCommon = num;
    maxCount = frequency[num];
  }
}

console.log(mostCommon); // 10 (most frequent element)
```

Method 2: Object to store frequency and finding the max frequency (same as mode): This approach leverages the same logic as finding the mode. The element with the highest frequency in the frequency object is the most common element.

Method 3: reduce with object creation: Creates an object to store element counts and uses reduce to iterate through the array, updating the object accordingly. The element with the highest count in the final object is the most common.


### Time Complexity
#### Method 1: Using the reduce method to find the most common element
- Time Complexity: O(n^2)
- Explanation: In this method, for each element in the array, the filter method is used to create a new array containing only elements that are equal to the current element. This filter operation has a time complexity of O(n) for each element, resulting in an overall time complexity of O(n^2).

#### Method 2:
- Time Complexity: O(n)
- Explanation: This method uses a single loop to iterate over the array and create a frequency object. This loop has a time complexity of O(n). The subsequent loop to find the most common element also has a time complexity of O(n) since it iterates over the keys of the frequency object. Overall, the time complexity is O(n).

#### Method 3:
- Time Complexity: O(n)
- Explanation: Similar to Method 2, this method uses a single loop to iterate over the array and create a frequency object. The subsequent loop to find the most common element also has a time complexity of O(n). Overall, the time complexity is O(n).
</p>
</details>

###### 46. How can you find the least common element in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the reduce method and an object to store frequencies
const freq = array.reduce((acc, curr) => {
  acc[curr] = (acc[curr] || 0) + 1;
  return acc;
}, {});
const leastCommon = Object.keys(freq).reduce((a, b) => freq[a] < freq[b] ? a : b);

// Method 2: Object to store frequency and finding the min frequency
const numbers = [10, 20, 30, 10, 10, 20, 40];

const frequency = {};
for (const num of numbers) {
  frequency[num] = (frequency[num] || 0) + 1; // Initialize count if not present
}

let leastCommon = null;
let minCount = Infinity; // Initialize with a high value
for (const num in frequency) {
  if (frequency[num] < minCount) {
    leastCommon = num;
    minCount = frequency[num];
  }
}

console.log(leastCommon); // 40 (assuming all elements appear at least once)
```

- Similar to finding the most common element, this approach iterates through the array, building a frequency object.
- It then iterates through the frequency object to find the element with the lowest count (least common).

### Time Complexity
#### Method 1: Using the reduce method and an object to store frequencies
```javascript
const freq = array.reduce((acc, curr) => {
  acc[curr] = (acc[curr] || 0) + 1;
  return acc;
}, {});
const leastCommon = Object.keys(freq).reduce((a, b) => freq[a] < freq[b] ? a : b);
```
- Time Complexity: O(n)
- Explanation: In this method, the array is iterated over once using the reduce method to create an object with frequencies. This operation has a time complexity of O(n). The subsequent reduction to find the least common element also has a time complexity of O(n) since it iterates over the keys of the frequency object. Overall, the time complexity is O(n).

#### Method 2: Object to store frequency and finding the min frequency
```javascript
const numbers = [10, 20, 30, 10, 10, 20, 40];

const frequency = {};
for (const num of numbers) {
  frequency[num] = (frequency[num] || 0) + 1; // Initialize count if not present
}

let leastCommon = null;
let minCount = Infinity; // Initialize with a high value
for (const num in frequency) {
  if (frequency[num] < minCount) {
    leastCommon = num;
    minCount = frequency[num];
  }
}

console.log(leastCommon); // 40 (assuming all elements appear at least once)
```
- Time Complexity: O(n)
- Explanation: This method also uses a single loop to iterate over the array and create a frequency object. The subsequent loop to find the least common element also has a time complexity of O(n) since it iterates over the keys of the frequency object. Overall, the time complexity is O(n).


</p>
</details>

###### 47. How can you find the index of the first occurrence of a value in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: indexOf(): Returns the index of the first occurrence of the specified value in the array, or -1 if not found.
const numbers = [10, 20, 30, 10, 10];
const index1 = numbers.indexOf(20); // 1
console.log(index1); // 1

// Method 2: findIndex(): Returns the index of the first element in the array that satisfies the provided testing function.
const index2 = numbers.findIndex(num => num === 10); // 0
console.log(index2); // 0
```

- indexOf() is a built-in method that efficiently searches for the first occurrence.
- findIndex() offers more flexibility for custom search criteria using a callback function.

### Time Complexity
#### Method 1: Using indexOf()
```javascript
const numbers = [10, 20, 30, 10, 10];
const index1 = numbers.indexOf(20); // 1
console.log(index1); // 1
```
- Time Complexity: O(n)
- Explanation: The indexOf method iterates through the array to find the first occurrence of the specified value. In the worst case, it may need to check each element once, resulting in a time complexity of O(n), where n is the number of elements in the array.

#### Method 2: Using findIndex()
```javascript
const index2 = numbers.findIndex(num => num === 10); // 0
console.log(index2); // 0
```
- Time Complexity: O(n)
- Explanation: The findIndex method also iterates through the array to find the first element that satisfies the provided testing function. Similar to indexOf, it may need to check each element once in the worst case, resulting in a time complexity of O(n), where n is the number of elements in the array.

</p>
</details>

###### 48. How can you find the index of the last occurrence of a value in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: lastIndexOf(): Returns the index of the last occurrence of the specified value in the array, or -1 if not found.
const numbers = [10, 20, 30, 10, 10];
const index1 = numbers.lastIndexOf(10); // 3
console.log(index1); // 3


// Method 2: Loop from the end: Iterates through the array from the end, checking for the value and returning the index upon finding it.
const index2 = numbers.length - 1 - numbers.slice(0).reverse().indexOf(10); // 3
console.log(index2); // 3
```

- lastIndexOf() is a built-in method specifically designed for finding the last occurrence.
- Looping from the end can be a more manual approach but might be useful for understanding the concept.

### Time Complexity
#### Method 1: Using lastIndexOf()
```javascript
const numbers = [10, 20, 30, 10, 10];
const index1 = numbers.lastIndexOf(10); // 3
console.log(index1); // 3
```
- Time Complexity: O(n)
- Explanation: The lastIndexOf method iterates through the array from the end to find the last occurrence of the specified value. In the worst case, it may need to check each element once, resulting in a time complexity of O(n), where n is the number of elements in the array.

#### Method 2: Loop from the end using reverse() and indexOf()
```javascript
const index2 = numbers.length - 1 - numbers.slice(0).reverse().indexOf(10); // 3
console.log(index2); // 3
```
- Time Complexity: O(n)
- Explanation: This method involves three steps: slicing the array, reversing it, and then finding the index of the specified value. Each of these operations has a time complexity of O(n), leading to an overall time complexity of O(n). Specifically:

</p>
</details>

###### 49. How can you remove specific elements from an array by value?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: filter(): Creates a new array with all elements that pass the test implemented by the provided function.
const numbers = [10, 20, 30, 10, 10];
const filteredNumbers = numbers.filter(num => num !== 10); // [20, 30]

console.log(filteredNumbers); // [20, 30]


// Method 2: splice() (with caution): Removes elements from an array and (optionally) replaces them with other elements. It modifies the original array, so use it with care.
JavaScript
const numbers = [10, 20, 30, 10, 10];
numbers.splice(1, 2); // Remove 20 and 30 (starting from index 1)

console.log(numbers); // [10, 10, 10]
```

- filter() creates a new array without modifying the original one, excluding elements that match the filter condition (not equal to 10 in this case).
- splice() modifies the original array in place. Use it cautiously and consider creating a copy of the array if necessary to

### Time Complexity
#### Method 1: Using filter()
```javascript
const numbers = [10, 20, 30, 10, 10];
const filteredNumbers = numbers.filter(num => num !== 10); // [20, 30]

console.log(filteredNumbers); // [20, 30]
```
Time Complexity: O(n)
Explanation:
The filter method iterates through all elements of the array to apply the provided function.
In the worst case, it will check each element exactly once, resulting in a time complexity of O(n), where n is the number of elements in the array.

#### Method 2: Using splice()
```javascript
const numbers = [10, 20, 30, 10, 10];
numbers.splice(1, 2); // Remove 20 and 30 (starting from index 1)

console.log(numbers); // [10, 10, 10]
```
- Time Complexity: O(n)
- Explanation:
  - The splice method removes elements from an array starting at a specified index.
  - Removing k elements from an array using splice has a complexity of O(k), but since it also shifts the remaining elements in the array to fill the gaps, the overall time complexity can be considered O(n), where n is the number of elements in the array after the splice operation.
</p>
</details>

###### 50. How can you convert a sparse array to a dense array in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: filter(Boolean): Uses filter with a callback that coerces elements to booleans. Only elements that become true (non-empty values) are included in the new array.
const sparseArray = [1, , , 4, , 5]; // , represents empty slots
const denseArray = sparseArray.filter(Boolean); // [1, 4, 5]
console.log(denseArray); // [1, 4, 5]

// Method 2: reduce with concatenation: Employs reduce to iterate through the original array and concatenate non-empty values into a new array.
const sparseArray = [1, , , 4, , 5];
const denseArray = sparseArray.reduce((acc, num) => num ? acc.concat(num) : acc, []); // Initialize accumulator as an empty array
console.log(denseArray); // [1, 4, 5]

// Method 3:  Using the forEach method
const denseArray = [];
sparseArray.forEach(value => {
  if (value !== undefined) {
    denseArray.push(value);
  }
});
```

### Time Complexity
#### Method 1: Using filter(Boolean)
```javascript
const sparseArray = [1, , , 4, , 5]; // , represents empty slots
const denseArray = sparseArray.filter(Boolean); // [1, 4, 5]
console.log(denseArray); // [1, 4, 5]
```
- Time Complexity: O(n)
- Explanation:
    - The filter method iterates through all elements of the array, applying the Boolean callback to each element.
    - The callback Boolean checks if the element is truthy.
    - This results in a time complexity of O(n), where n is the number of elements in the array.
#### Method 2: Using reduce with concatenation
```javascript
const sparseArray = [1, , , 4, , 5];
const denseArray = sparseArray.reduce((acc, num) => num ? acc.concat(num) : acc, []); // Initialize accumulator as an empty array
console.log(denseArray); // [1, 4, 5]
```
- Time Complexity: O(n)
- Explanation:
    - The reduce method iterates through all elements of the array.
    - The callback function checks if each element is truthy and concatenates non-empty values into the accumulator array.
    - Since concatenation and checking each element are O(1) operations, the overall time complexity is O(n).
#### Method 3: Using forEach
```javascript
const sparseArray = [1, , , 4, , 5];
const denseArray = [];
sparseArray.forEach(value => {
  if (value !== undefined) {
    denseArray.push(value);
  }
});
console.log(denseArray); // [1, 4, 5]
```
- Time Complexity: O(n)
- Explanation:
    - The forEach method iterates through all elements of the array.
    - The callback function checks if each element is not undefined and pushes non-empty values into the denseArray.
    - Since pushing elements into an array and checking each element are O(1) operations, the overall time complexity is O(n).

</p>
</details>

###### 51. How can you merge multiple arrays into a single array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the concat method
const mergedArray = array1.concat(array2, array3);

// Method 2: Using the spread operator
const mergedArray = [...array1, ...array2, ...array3];
```

- concat(): Concatenates multiple arrays (spread syntax can be used for readability).
- Spread syntax with ...: Uses the spread operator to expand each array into individual elements during concatenation.

### Time Complexity
#### Method 1: Using the concat method
```javascript
const mergedArray = array1.concat(array2, array3);
```
- Time Complexity: O(n + m + p)
- Explanation:
    - The concat method creates a new array and iterates over each element of array1, array2, and array3 to copy them into the new array.
    - If array1 has n elements, array2 has m elements, and array3 has p elements, the time complexity is O(n + m + p).
#### Method 2: Using the spread operator
```javascript
const mergedArray = [...array1, ...array2, ...array3];
```
- Time Complexity: O(n + m + p)
- Explanation:
    - The spread operator ... also creates a new array and iterates over each element of array1, array2, and array3 to copy them into the new array.
    - Similar to the concat method, if array1 has n elements, array2 has m elements, and array3 has p elements, the time complexity is O(n + m + p).
</p>
</details>

###### 52. How can you find the difference between two arrays, excluding common elements?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: filter and comparison: Filters elements from the second array that are not present in the first array.
const array1 = [1, 2, 3, 4];
const array2 = [2, 3, 5, 6];

const difference = array2.filter(num => !array1.includes(num)); // [5, 6]

console.log(difference); // [5, 6]

// Method 2: Set difference: Utilizes the Set data structure to efficiently remove duplicates and find the difference.
JavaScript
const set1 = new Set(array1);
const difference = array2.filter(num => !set1.has(num)); // [5, 6]

console.log(difference); // [5, 6]
```

- The first method iterates through the second array, keeping only elements not found (using includes) in the first array.
- The second method leverages Sets, which don't allow duplicates. By creating a Set from the first array and filtering the second array based on the Set's membership, you get the difference.

### Time Complexity
#### Method 1: Filter and Comparison
```javascript
const array1 = [1, 2, 3, 4];
const array2 = [2, 3, 5, 6];

const difference = array2.filter(num => !array1.includes(num)); // [5, 6]

console.log(difference); // [5, 6]
```
- Time Complexity: O(m * n)
- Explanation:
    - The filter method iterates over array2, which has m elements.
    - For each element in array2, the includes method checks if the element is in array1, which has n elements.
    - The includes method itself is O(n) since it performs a linear search.
    - Therefore, the time complexity is O(m * n).
#### Method 2: Set Difference
```javascript
const array1 = [1, 2, 3, 4];
const array2 = [2, 3, 5, 6];

const set1 = new Set(array1);
const difference = array2.filter(num => !set1.has(num)); // [5, 6]

console.log(difference); // [5, 6]
```
- Time Complexity: O(n + m)
- Explanation:
    - Creating a Set from array1 takes O(n) time, where n is the number of elements in array1.
    - The filter method iterates over array2, which has m elements.
    - For each element in array2, the has method of the Set checks if the element is in the set. The has method is O(1) on average.
    - Therefore, the time complexity is O(n + m).
- Summary
    - Method 1: Filter and Comparison has a time complexity of O(m * n).
    - Method 2: Set Difference has a time complexity of O(n + m).
    - The Set-based method is more efficient for finding the difference between two arrays, especially when the arrays are large.

</p>
</details>

###### 53. How can you find the index of the first occurrence of an element in an array from a specific index?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: slice and indexOf(): Creates a subarray starting from the specified index and uses indexOf to find the element's index within that subarray.
const numbers = [10, 20, 30, 10, 10];
const startIndex = 2; // Start searching from index 2
const element = 10;

const subarray = numbers.slice(startIndex);
const index = subarray.indexOf(element);

console.log(index === -1 ? -1 : index + startIndex); // 3 (if element is found)
// Method 2: for loop 
function findIndexFrom(array, targetElement, startIndex) {
  for (let i = startIndex; i < array.length; i++) {
    if (array[i] === targetElement) {
      return i;
    }
  }
  return -1; // Return -1 if the element is not found
}

// Example usage
const array = [1, 2, 3, 4, 5, 3, 6];
const startIndex = 3;
const targetElement = 3;
const index = findIndexFrom(array, targetElement, startIndex);

console.log(index); // Output: 5
```

- slice extracts a portion of the array from the specified starting index (inclusive).
- indexOf is then used on the subarray to find the element's index relative to the starting index. We add startIndex to account for the original array's starting position.

### Time Complexity
#### Method 1: Slice and IndexOf
```javascript
const numbers = [10, 20, 30, 10, 10];
const startIndex = 2; // Start searching from index 2
const element = 10;

const subarray = numbers.slice(startIndex);
const index = subarray.indexOf(element);

console.log(index === -1 ? -1 : index + startIndex); // 3 (if element is found)
```
- Time Complexity: O(n - startIndex)
- Explanation:
    - The slice method creates a subarray starting from startIndex. This takes O(n - startIndex) time.
    - The indexOf method searches for the element in the subarray. This takes O(n - startIndex) time.
    - Therefore, the overall time complexity is O(n - startIndex) + O(n - startIndex) = O(n - startIndex).
#### Method 2: For Loop
```javascript
function findIndexFrom(array, targetElement, startIndex) {
  for (let i = startIndex; i < array.length; i++) {
    if (array[i] === targetElement) {
      return i;
    }
  }
  return -1; // Return -1 if the element is not found
}

// Example usage
const array = [1, 2, 3, 4, 5, 3, 6];
const startIndex = 3;
const targetElement = 3;
const index = findIndexFrom(array, targetElement, startIndex);

console.log(index); // Output: 5
```
- Time Complexity: O(n - startIndex)
- Explanation:
    - The for loop iterates through the array starting from startIndex to the end of the array. This takes O(n - startIndex) time.
    - In each iteration, it performs a constant-time comparison.
    - Therefore, the overall time complexity is O(n - startIndex).
- Summary
    - Method 1: Slice and IndexOf has a time complexity of O(n - startIndex).
    - Method 2: For Loop has a time complexity of O(n - startIndex).
    - Both methods have the same time complexity, but the for loop method avoids creating an additional subarray and might be slightly more efficient in practice due to lower overhead.

</p>
</details>

###### 54. How can you check if an array contains only unique values?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Set comparison: Creates a Set from the array and compares its size to the original array's length.
const numbers = [1, 2, 3, 4];
const unique = new Set(numbers).size === numbers.length; // true (no duplicates)

console.log(unique); // true

// method 2: indexOf with comparison: Iterates through the array, checking if the current element's index using indexOf is the same as its current position (no previous occurrences).
const numbers = [1, 2, 3, 4];
let unique = true;
for (let i = 0; i < numbers.length; i++) {
  if (numbers.indexOf(numbers[i]) !== i) {
    unique = false;
    break;
  }
}

console.log(unique); // true
```

- The Set approach is generally faster and more concise, especially for larger arrays.
- The indexOf approach might be helpful if you need to perform additional actions upon finding a duplicate element.

### Time Complexity
#### Method 1: Set Comparison
```javascript
const numbers = [1, 2, 3, 4];
const unique = new Set(numbers).size === numbers.length; // true (no duplicates)
console.log(unique); // true
```
- Time Complexity: O(n)
- Explanation:
    - Creating a Set from an array involves iterating through the array and inserting each element into the set. This takes O(n) time.
    - Checking the size of the set and comparing it to the array's length is a constant-time operation, O(1).
    - Therefore, the overall time complexity is O(n).
#### Method 2: IndexOf with Comparison
```javascript
const numbers = [1, 2, 3, 4];
let unique = true;
for (let i = 0; i < numbers.length; i++) {
  if (numbers.indexOf(numbers[i]) !== i) {
    unique = false;
    break;
  }
}
console.log(unique); // true
```
- Time Complexity: O(n^2)
- Explanation:
    - The for loop iterates through the array, taking O(n) time.
    - Inside the loop, indexOf is called for each element. In the worst case, indexOf iterates through the entire array to find the element, which takes O(n) time.
    - Therefore, for each of the n elements, indexOf could take O(n) time, resulting in an overall time complexity of O(n) * O(n) = O(n^2).
- Summary
    - Method 1: Set Comparison has a time complexity of O(n).
    - Method 2: IndexOf with Comparison has a time complexity of O(n^2).
Method 1 is significantly more efficient than Method 2 for checking the uniqueness of elements in an array.
</p>
</details>

###### 55. How can you find the longest consecutive sequence of a specific value in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Loop with counters: Iterates through the array, keeping track of the current sequence length and the longest sequence found so far.
const numbers = [1, 2, 2, 3, 4, 2, 2, 2, 5];
const value = 2;
let currentCount = 0;
let longestCount = 0;
for (const num of numbers) {
  if (num === value) {
    currentCount++;
  } else {
    longestCount = Math.max(longestCount, currentCount);
    currentCount = 0;
  }
}
longestCount = Math.max(longestCount, currentCount); // Account for potential sequence at the end
console.log(longestCount); // 3 (longest sequence of 2s)

// Method 2: reduce with conditional accumulation: Uses reduce to iterate through the array and build the longest sequence length based on conditions.
const numbers = [1, 2, 2, 3, 4, 2, 2, 2, 5];
const value = 2;

const longestCount = numbers.reduce((longest, num) => {
  return (num === value) ? Math.max(longest + 1, 0) : longest; // Update or reset based on value
}, 0); // Initialize longest with 0

console.log(longestCount); // 3 (longest sequence of 2s)
```

- The first approach uses a loop with counters to track the current sequence length and the longest sequence encountered so far.
- The second approach utilizes reduce to iterate and conditionally update the longest variable. If the current element matches the value, the longest is potentially extended by 1. Otherwise, it's reset to 0 to start counting a new sequence.

### Time Complexity
#### Method 1: Loop with Counters
```javascript
const numbers = [1, 2, 2, 3, 4, 2, 2, 2, 5];
const value = 2;
let currentCount = 0;
let longestCount = 0;
for (const num of numbers) {
  if (num === value) {
    currentCount++;
  } else {
    longestCount = Math.max(longestCount, currentCount);
    currentCount = 0;
  }
}
longestCount = Math.max(longestCount, currentCount); // Account for potential sequence at the end
console.log(longestCount); // 3 (longest sequence of 2s)
```
- Time Complexity: O(n)
- Explanation:
    - The for loop iterates through the array once, taking O(n) time, where n is the length of the array.
    - Inside the loop, the operations (conditional check, increment, assignment) are all O(1) constant-time operations.
    - Therefore, the overall time complexity is O(n).
#### Method 2: Reduce with Conditional Accumulation
```javascript
const numbers = [1, 2, 2, 3, 4, 2, 2, 2, 5];
const value = 2;

const longestCount = numbers.reduce((longest, num) => {
  return (num === value) ? Math.max(longest + 1, 0) : longest; // Update or reset based on value
}, 0); // Initialize longest with 0

console.log(longestCount); // 3 (longest sequence of 2s)
```
- Time Complexity: O(n)
- Explanation:
    - The reduce method iterates through the array once, taking O(n) time, where n is the length of the array.
    - The operations inside the reduce callback (conditional check, arithmetic operations, and Math.max function) are all O(1) constant-time operations.
    - Therefore, the overall time complexity is O(n).
- Summary
    - Method 1: Loop with Counters has a time complexity of O(n).
    - Method 2: Reduce with Conditional Accumulation also has a time complexity of O(n).
    - Both methods are efficient and have the same linear time complexity for finding the longest sequence of a specified value in an array.
</p>
</details>

###### 56. How can you find the number of occurrences of each element in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using a Map
function countOccurrences(array) {
  const map = new Map();
  array.forEach(item => {
    map.set(item, (map.get(item) || 0) + 1);
  });
  return map;
}

// Method 2: Using an Object
function countOccurrences(array) {
  const counts = {};
  array.forEach(item => {
    counts[item] = (counts[item] || 0) + 1;
  });
  return counts;
}

// Example usage
const array = [1, 2, 1, 3, 4, 2, 1, 3];
console.log(countOccurrences(array));

// Method 3: 
const numbers = [10, 20, 30, 10, 10, 20];

const frequency = numbers.reduce((acc, num) => {
  acc[num] = (acc[num] || 0) + 1;
  return acc;
}, {}); // Initialize accumulator as an empty object

console.log(frequency); // {10: 3, 20: 2, 30: 1}

```

- Method 1: Using a Map: This method uses a Map to store the count of each element.
- Method 2: Using an Object: This method uses an object to store the count of each element.
- Method 3: reduce with object creation: Employs reduce to iterate through the array and build an object where keys are elements and values are their frequencies.

### Time Complexity
#### Method 1: Using a Map
```javascript
function countOccurrences(array) {
  const map = new Map();
  array.forEach(item => {
    map.set(item, (map.get(item) || 0) + 1);
  });
  return map;
}
```
- Time Complexity: O(n)
- Explanation:
    - The forEach method iterates through the array once, taking O(n) time, where n is the length of the array.
    - The operations inside the forEach callback (getting and setting values in the Map) are O(1) on average.
    - Therefore, the overall time complexity is O(n).
#### Method 2: Using an Object
```javascript
function countOccurrences(array) {
  const counts = {};
  array.forEach(item => {
    counts[item] = (counts[item] || 0) + 1;
  });
  return counts;
}
```
- Time Complexity: O(n)
- Explanation:
    - The forEach method iterates through the array once, taking O(n) time, where n is the length of the array.
    - The operations inside the forEach callback (getting and setting properties in the object) are O(1) on average.
    - Therefore, the overall time complexity is O(n).
#### Method 3: Using Reduce
```javascript
const numbers = [10, 20, 30, 10, 10, 20];

const frequency = numbers.reduce((acc, num) => {
  acc[num] = (acc[num] || 0) + 1;
  return acc;
}, {}); // Initialize accumulator as an empty object

console.log(frequency); // {10: 3, 20: 2, 30: 1}
```
- Time Complexity: O(n)
- Explanation:
    - The reduce method iterates through the array once, taking O(n) time, where n is the length of the array.
    - The operations inside the reduce callback (getting and setting properties in the object) are O(1) on average.
    - Therefore, the overall time complexity is O(n).
- Summary
    - Method 1: Using a Map has a time complexity of O(n).
    - Method 2: Using an Object has a time complexity of O(n).
    - Method 3: Using Reduce also has a time complexity of O(n).
All three methods are efficient and have the same linear time complexity for counting the occurrences of elements in an array.
</p>
</details>

###### 57. How can you remove the last n elements from an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using the slice
const numbers = [10, 20, 30, 40, 50];
const n = 2;

const shortenedArray = numbers.slice(0, -n); // Exclude the last n elements

console.log(shortenedArray); // [10, 20, 30]

// Method 2: Using the splice
const numbers = [10, 20, 30, 40, 50];
const n = 2;

numbers.splice(-n); // Remove the last n elements

console.log(numbers); // [10, 20, 30]
```

- Method 1: Using slice method: This method creates a new array containing all elements except the last n elements.
- Method 2: Using splice method: This method modifies the original array by removing elements starting from index array.length - n.

### Time Complexity
#### Method 1: Using the slice
- Time Complexity: O(1) (constant time complexity)
- Explanation: The slice() method creates a new array and copies the elements from the original array, excluding the last n elements. This operation takes constant time, as it does not depend on the size of the input array.

#### Method 2: Using the splice
- Time Complexity: O(n)
- Explanation: The splice() method modifies the original array by removing the last n elements. This operation takes linear time, as it needs to iterate through the array to find the last n elements.
</p>
</details>

###### 58. How can you add elements to an array at specific indexes?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using splice method
function addElementsAtIndex(array, index, ...elements) {
  array.splice(index, 0, ...elements);
  return array;
}

const numbers = [10, 20, 30];
const index = 1; // Insert after the first element
const elementsToAdd = [40, 50];

numbers.splice(index, 0, ...elementsToAdd); // Insert at index, remove 0 elements, spread the elements to add

console.log(numbers); // [10, 40, 50, 20, 30]

// Method 2: Using spread operator and splice method
function addElementsAtIndex(array, index, ...elements) {
  return [...array.slice(0, index), ...elements, ...array.slice(index)];
}

// Example usage
let array = [1, 2, 3, 4, 5];
console.log(addElementsAtIndex(array, 2, 6, 7)); // Output: [1, 2, 6, 7, 3, 4, 5]
```

- Method 1: Using splice method: This method modifies the original array by adding elements at the specified index.
- Method 2: Using spread operator and splice method: This method creates a new array with the added elements without modifying the original array.

### Time Complexity
#### Method 1: Using splice method
  - Time Complexity: O(n)
  - Explanation: The splice() method modifies the original array by inserting the new elements at the specified index, which takes linear time proportional to the number of elements in the array.

#### Method 2: Using spread operator and slice method
  - Time Complexity: O(n)
  - Explanation: The slice() method creates a new array by copying elements from the original array up to the specified index, which takes linear time proportional to the number of elements in the array. The spread operator (...) creates a new array by concatenating multiple arrays, which also takes linear time proportional to the total number of elements being concatenated. Therefore, the overall time complexity is O(n)

</p>
</details>

###### 59. How can you remove elements from an array at specific indexes?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using filter method
function removeElementsByIndex(array, indexes) {
  return array.filter((_, index) => !indexes.includes(index));
}

// Method 2: Using splice method
function removeElementsByIndex(array, indexes) {
  indexes.sort((a, b) => b - a).forEach(index => {
    array.splice(index, 1);
  });
  return array;
}

// Example usage
let array = [1, 2, 3, 4, 5];
console.log(removeElementsByIndex(array, [1, 3])); // Output: [1, 3, 5]

const numbers = [10, 20, 30, 40, 50];
const index = 2; // Remove starting from the second element
const countToRemove = 2; // Remove 2 elements

numbers.splice(index, countToRemove);

console.log(numbers); // [10, 20, 50]
```

- Method 1: Using filter method: This method creates a new array with elements that do not match the specified indexes.
- Method 2: Using splice method: This method modifies the original array by removing elements at the specified indexes.

### Time Complexity
#### Method 1: Using filter method
  - Time Complexity: O(n)
  - Explanation: The filter() method iterates through the array once, taking O(n) time, where n is the length of the array. The includes() method also takes O(n) time in the worst case (when searching for an element at the end of the array), so the overall time complexity is O(n).

#### Method 2: Using splice method
  - Time Complexity: O(n)
  - Explanation: The splice() method modifies the original array by removing elements at specific indices, which takes linear time proportional to the number of elements being removed. In this case, we are removing multiple elements, so the overall time complexity is O(n), where n is the number of elements being removed.

</p>
</details>

###### 60. How can you convert a multidimensional array into a flat array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using concat and apply methods
function flattenArray(array) {
  return [].concat.apply([], array.map(item => Array.isArray(item) ? flattenArray(item) : item));
}

// Method 2: Using the flat method
function flattenArray2(array) {
  return array.flat(Infinity);
}

// Example usage
let array = [1, [2, 3], [4, [5, 6]]];
console.log(flattenArray(array)); // Output: [1, 2, 3, 4, 5, 6]
console.log(flattenArray2(array));
```

- Method 1: Using concat and apply methods: This method flattens the array recursively.
- Method 2: Using the flat method: This method flattens the array up to a specified depth.

### Time Complexity
#### Method 1: Using concat and apply methods
  - Time Complexity: O(n)
  - Explanation: The map() method iterates through the array once, taking O(n) time, where n is the length of the array. The concat.apply() method also takes O(n) time because it concatenates all the elements in the array. The recursion in the flattenArray function adds an additional factor of n to the time complexity, so the overall time complexity is O(n^2).

#### Method 2: Using the flat method
  - Time Complexity: O(n)
  - Explanation: The flat() method is optimized for deeply nested arrays and uses a iterative approach to flatten the array. It has a linear time complexity of O(n), where n is the total number of elements in the array.
</p>
</details>

###### 61. How can you find the difference between two arrays, including duplicates?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using filter() and includes()
const array11 = [1, 2, 3, 2, 1];
const array22 = [2, 3, 4];
const difference = array11.filter(num => !array22.includes(num));

console.log(difference); // [1]

// Method 2: Using reduce()
const array1 = [1, 2, 2, 3, 4];
const array2 = [2, 3, 5];
const difference2 = array1.reduce((acc, curr) => {
  if (!array2.includes(curr) || acc.includes(curr)) {
    acc.push(curr);
  }
  return acc;
}, []);

console.log(difference2); // [1, 4]
```

Method 1: filter with comparison: Filters elements from the first array that are not included in the second array (might be less performant for larger arrays).

### Time Complexity
#### Method 1: Using filter() and includes()
  - Time Complexity: O(n^2)
  - Explanation: The filter() method iterates through the array once, taking O(n) time, where n is the length of the array. The includes() method inside the callback function also iterates through the array array22 for each element in array11, making it O(n) time. Since this happens for each element in array11, the overall time complexity is O(n^2), where n is the length of array11.

#### Method 2: Using reduce()
  - Time Complexity: O(n)
  - Explanation: The reduce() method iterates through the array once, taking O(n) time, where n is the length of the array. The inner condition !array2.includes(curr) || acc.includes(curr) checks for the existence of each element in both arrays, which takes constant time O(1). Therefore, the overall time complexity is O(n), where n is the length of array1.

</p>
</details>

###### 62. How can you find the index of the first non-repeating element in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const array = [1, 1, 2, 2, 3, 4, 4, 5];

// Method 1: Using findIndex() and indexOf()
const firstNonRepeatingIndex = array.findIndex((item, index) => array.indexOf(item) === array.lastIndexOf(item));

console.log(firstNonRepeatingIndex); // 0 (index of 1)


// Method 2: Loop with object to store frequency
const numbers = [10, 20, 30, 10, 10, 20];

const frequency = {};
for (const num of numbers) {
  frequency[num] = (frequency[num] || 0) + 1; // Initialize count if not present
}

let firstNonRepeatingIndex = null;
for (let i = 0; i < numbers.length; i++) {
  if (frequency[numbers[i]] === 1) {
    firstNonRepeatingIndex = i;
    break;
  }
}

console.log(firstNonRepeatingIndex !== null ? firstNonRepeatingIndex : -1); // 2 (or -1 if no non-repeating element)
```

Method 2: The second approach iterates through the array, building a frequency object. Then, it iterates through the array again to find the index of the first element with a count of 1 (meaning it appears only once).

### Time Complexity
#### Method 1: Using findIndex() and indexOf()
  - Time Complexity: O(n^2)
  - Explanation: The findIndex() method iterates through the array once, taking O(n) time, where n is the length of the array. Inside the callback function, the indexOf() method is called, which also iterates through the array for each element, taking O(n) time. Therefore, the overall time complexity is O(n^2), where n is the length of array.

#### Method 2: Loop with object to store frequency
  - Time Complexity: O(n)
  - Explanation: The outer loop iterates through the array once, taking O(n) time, where n is the length of numbers. The inner loop checks for non-repeating elements in a single pass through the array, also taking O(n) time. Therefore, the overall time complexity is O(n), where n is the length of numbers.

Note that Method 2 is more efficient than Method 1 because it only requires a single pass through the array to store frequencies and find the first non-repeating element. Method 1 uses nested iterations, leading to a higher time complexity.

</p>
</details>


###### 63. How can you check if two arrays have at least one common element?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const array1 = [1, 2, 3];
const array2 = [3, 4, 5];

// Using some()
const hasCommonElement = array1.some(item => array2.includes(item));

console.log(hasCommonElement); // true
```

- Uses some on one array to iterate through its elements.
- The callback function checks if the current element (num) is present in the other array using includes.
- If includes returns true for any element, it means there's a common element, and some stops iterating and returns true

### Time Complexity
The time complexity for this code is O(n), where n is the length of array1.

The some() method iterates through array1 and checks if the callback function returns a truthy value. The callback function uses the includes() method to check if each element of array1 is present in array2. This operation takes O(n) time, where n is the length of array2.

Since the some() method stops iterating as soon as it finds a truthy value, the overall time complexity is still O(n), where n is the length of array1. However, in practice, the actual time complexity may be closer to O(min(n, m)), where m is the length of array2, because includes() may terminate early when it finds a match.

Note that if you were to use every() instead of some(), the time complexity would be O(m), where m is the length of array2, because every() would need to check every element in array2 for each element in array1.

</p>
</details>

###### 64. How can you find the index of the last occurrence of an element in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const array = [1, 2, 3, 2, 4, 5, 2];

// Method 1: Using reverse() and findIndex()
const lastIndex = array.length - 1 - array.reverse().findIndex(item => item === 2);

console.log(lastIndex); // 6

// Method 2: lastIndexOf (Built-in Method)
const array = [1, 2, 3, 2, 4, 5, 2];
const element = 2;

const lastIndex = array.lastIndexOf(element);

console.log(lastIndex !== -1 ? lastIndex : -1); // 3 (index of the last occurrence)

// Method 3: Loop with Comparison
const array = [1, 2, 3, 2, 4, 5, 2];
const element = 2;

let lastIndex = -1;
for (let i = array.length - 1; i >= 0; i--) {
  if (array[i] === element) {
    lastIndex = i;
    break; // Stop iterating once found
  }
}

console.log(lastIndex); // 3 (index of the last occurrence)
```

- Method 2:
    - lastIndexOf searches the array backwards from the end and returns the index of the last occurrence of the specified element.
    - If the element is not found, it returns -1.
- Method 3:
    - Loop with Comparison Iterates through the array backwards using a loop (for...of or for...in can also be used).
    - If the current element (numbers[i]) matches the target element (element), the index (i) is stored in lastIndex.
    - The loop breaks after finding the first occurrence (last occurrence while iterating backwards) to avoid unnecessary iterations.

### Time Complexity
#### Method 1: Using reverse() and findIndex()
  - Time Complexity: O(n)
  - Explanation: The reverse() method takes O(n) time, where n is the length of the array. The findIndex() method then iterates through the reversed array, also taking O(n) time. Therefore, the overall time complexity is O(n).

#### Method 2: lastIndexOf (Built-in Method)
  - Time Complexity: O(n)
  - Explanation: The built-in lastIndexOf() method iterates through the array from the end to find the last occurrence of the element, taking O(n) time, where n is the length of the array.

#### Method 3: Loop with Comparison
  - Time Complexity: O(n)
  - Explanation: The loop iterates through the array in reverse order, comparing each element with the target element. The loop stops once it finds a match, so it takes O(n) time in the worst case, where n is the length of the array.

In all three methods, the time complexity is linear, but Method 2 is more efficient as it uses a built-in method that is optimized for this specific task.

</p>
</details>

###### 65. How can you remove elements from an array that satisfy a specific condition?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const array = [1, 2, 3, 4, 5, 6];

// Method 1: Using filter()
const filteredArray = array.filter(item => item % 2 === 0);

console.log(filteredArray); // [2, 4, 6]

// Method 2: Loops through the array and uses splice
const numbers = [10, 20, 30, 40, 50];
const condition = num => num < 30; // Remove elements less than 30

let i = 0; // Index to keep track of modified array
while (i < numbers.length) {
  if (condition(numbers[i])) {
    numbers.splice(i, 1); // Remove the element at index i (1 element)
  } else {
    i++; // Move to the next element if not removed
  }
}

console.log(numbers); // [30, 40, 50]
```

- Method 2: A loop iterates through the array.
    - If the current element (numbers[i]) satisfies the condition (condition(numbers[i])), splice is used to remove that element at index i (removing 1 element).
    - If the condition is not met, the i index is incremented to move to the next element.
    - This process continues until the entire array is scanned.

### Time Complexity
#### Method 2: A loop iterates through the array.
  - If the current element (numbers[i]) satisfies the condition (condition(numbers[i])), splice is used to remove that element at index i (removing 1 element).
  - If the condition is not met, the i index is incremented to move to the next element.
  - This process continues until the entire array is scanned.

</p>
</details>

###### 66. How can you replace specific elements in an array with new values?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Loop with Condition
const numbers = [10, 20, 30, 40, 50];
const condition = num => num < 30; // Replace elements less than 30
const newValue = 100;

for (let i = 0; i < numbers.length; i++) {
  if (condition(numbers[i])) {
    numbers[i] = newValue;
  }
}

console.log(numbers);

// Method 2: Using map()
const numbers = [10, 20, 30, 40, 50];
const condition = num => num < 30; // Replace elements less than 30
const newValue = 100;

const replacedArray = numbers.map(num => (condition(num) ? newValue : num));

console.log(replacedArray); // [100, 20, 30, 40, 50] (original array remains unchanged)

// Method 3: Using forEach
const newArray2 = [];const array = [1, 2, 3, 4, 5];
array.forEach(element => {
  newArray2.push(element === 3 ? 10 : element);
});
console.log(newArray2); // [1, 2, 10, 4, 5]
```

- Method 1: Loop with Condition:
    - Iterates through the array, replacing elements that meet a specific condition with a new value.
- Method 2: map with Condition
    - Creates a new array with elements replaced based on a callback function.

### Time Complexity
#### Method 1: Loop with Condition
  - Time Complexity: O(n)
  - The loop iterates through the array, checking each element to see if it meets the condition. If it does, it replaces the element. This operation takes O(n) time, where n is the length of the array.

#### Method 2: Using map()
  - Time Complexity: O(n)
  - The map() method iterates through the array, applying the condition and replacing elements as needed. This operation also takes O(n) time, where n is the length of the array.

#### Method 3: Using forEach
  - Time Complexity: O(n)
  - The forEach() method iterates through the array, applying the condition and pushing elements to a new array. This operation also takes O(n) time, where n is the length of the array.

In all three methods, the time complexity is linear, meaning they all have a direct relationship with the size of the input array. However, Method 2 using map() is often considered more efficient because it creates a new array without modifying the original one, which can be beneficial in certain situations.
</p>
</details>

###### 67. How can you find the largest and smallest numbers in an array without using the Math object?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Loop with Variables
const numbers = [10, 20, 30, 40, 5];

let largest = numbers[0];
let smallest = numbers[0];

for (const num of numbers) {
  if (num > largest) {
    largest = num;
  }
  if (num < smallest) {
    smallest = num;
  }
}

console.log("Largest:", largest); // Largest: 40
console.log("Smallest:", smallest); // Smallest: 5

// Method 2: Recursive Approach (Divide and Conquer)
const numbers = [10, 20, 30, 40, 5];

function findLargestSmallest(arr, low = 0, high = arr.length - 1) {
  if (low === high) {
    return { largest: arr[low], smallest: arr[low] }; // Base case: single element
  }

  const mid = Math.floor((low + high) / 2);
  const left = findLargestSmallest(arr, low, mid);
  const right = findLargestSmallest(arr, mid + 1, high);

  return {
    largest: Math.max(left.largest, right.largest),
    smallest: Math.min(left.smallest, right.smallest),
  };
}

const result = findLargestSmallest(numbers);
console.log("Largest:", result.largest); // Largest: 40
console.log("Smallest:", result.smallest); // Smallest: 5

// Method 3: Using reduce():
const array = [1, 2, 3, 4, 5];
const max = array.reduce((acc, curr) => (acc > curr ? acc : curr));
const min = array.reduce((acc, curr) => (acc < curr ? acc : curr));
console.log(`Max: ${max}, Min: ${min}`);

// Method 4: Using sort():
const array = [1, 2, 3, 4, 5];
array.sort((a, b) => a - b);
const min2 = array[0];
const max2 = array[array.length - 1];
console.log(`Max: ${max2}, Min: ${min2}`);
```

Method 1: filter with comparison: Filters elements from the first array that are not included in the second array (might be less performant for larger arrays).

### Time Complexity
#### Method 1: Loop with Variables
  - Time Complexity: O(n)
  - The loop iterates through the array, checking each element to find the largest and smallest values. This operation takes O(n) time, where n is the length of the array.

#### Method 2: Recursive Approach (Divide and Conquer)
  - Time Complexity: O(log n)
  - The recursive function divides the array into two halves and finds the largest and smallest values in each half. This operation takes O(log n) time, where n is the length of the array.

#### Method 3: Using reduce()
  - Time Complexity: O(n)
  - The reduce() method iterates through the array, applying a callback function to each element to find the maximum and minimum values. This operation takes O(n) time, where n is the length of the array.

#### Method 4: Using sort()
  - Time Complexity: O(n log n)
  - The sort() method sorts the array, which takes O(n log n) time, and then extracts the maximum and minimum values. This operation takes O(n log n) time, where n is the length of the array.

Note that Method 2 has a better time complexity than the other methods because it uses a divide-and-conquer approach, which reduces the problem size by half at each recursive step. The other methods iterate through the entire array, making them less efficient for large inputs.
</p>
</details>

###### 68. How can you find the sum of all elements in an array using recursion?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Using recursion
const sumArray = arr => {
  if (arr.length === 0) return 0;
  return arr[0] + sumArray(arr.slice(1));
};
console.log(sumArray([1, 2, 3, 4, 5])); // 15



const numbers = [10, 20, 30, 40];

function sumRecursive(arr) {
  if (arr.length === 0) {
    return 0; // Base case: empty array
  }
  return arr[0] + sumRecursive(arr.slice(1)); // Add first element and recurse on remaining elements
}

const totalSum = sumRecursive(numbers);
console.log("Sum:", totalSum); // Sum: 100
```

- Explanation:
    - The sumRecursive function takes an array (arr).
    - The base case checks for an empty array and returns 0 (no sum).
    - Otherwise, it returns the sum of the first element (arr[0]) and the recursive call on the remaining elements obtained using slice(1).


- Choosing the Right Method:
    While recursion can be used for finding the sum, a simple loop (for...of or reduce) or array methods like reduce are generally more efficient and easier to understand for this purpose. Recursion might have overhead due to function calls.

### Time Complexity
The time complexity of the recursive function sumArray and sumRecursive is O(n), where n is the length of the input array.

Here's a breakdown of the time complexity:

In each recursive call, the function processes one element of the array (by adding it to the sum).
The function then recursively calls itself on the remaining elements of the array (i.e., arr.slice(1)).
This process repeats until the base case is reached, which is when the array is empty (length 0).
Since each recursive call processes one element and makes another recursive call, the time complexity is proportional to the number of elements in the array. Therefore, the time complexity is O(n), where n is the length of the input array.

Note that while recursion can be an elegant way to solve problems, it's often less efficient than iterative solutions because it creates a new stack frame for each recursive call, which can lead to stack overflow errors for large inputs. In this case, an iterative solution using a simple loop would have a similar time complexity but would be more efficient in terms of memory usage.

</p>
</details>

###### 69. How can you check if an array is sorted in ascending order?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using every()
const isSorted = arr => arr.every((element, index) => index === 0 || element >= arr[index - 1]);
console.log(isSorted([1, 2, 3, 4, 5])); // true
console.log(isSorted([1, 3, 2, 4, 5])); // false

// Method 2: Loop with comparison
const sortedArray = [10, 20, 30, 40];
const unsortedArray = [10, 30, 20, 40];

function isSorted(arr) {
  for (let i = 0; i < arr.length - 1; i++) {
    if (arr[i] > arr[i + 1]) {
      return false; // Not sorted if current element is greater than next
    }
  }
  return true; // Sorted if loop completes without finding violations
}

console.log("Sorted array:", isSorted(sortedArray)); // true
console.log("Unsorted array:", isSorted(unsortedArray)); // false
```

- Explanation (Loop with Comparison):
    - The isSorted function takes an array (arr).
    - The loop iterates from index 0 to the second-last element (length - 1) to compare consecutive elements.
    - If arr[i] (current element) is greater than arr[i + 1] (next element), the array is not sorted, and the function returns false.
    - If the loop completes without finding any violation, the array is considered sorted, and the function returns true.

### Time Complexity
#### Method 1: Using every()
  - Time Complexity: O(n)
  - Explanation: The every() method iterates through the array, checking each element to see if it's less than or equal to the previous element. This operation takes O(n) time, where n is the length of the array.

#### Method 2: Loop with comparison
  - Time Complexity: O(n)
  - Explanation: The loop iterates through the array, comparing each element to the next one. If a pair of elements is found where the current element is greater than the next one, the function returns false immediately. If the loop completes without finding any such pairs, it returns true. This operation also takes O(n) time, where n is the length of the array.

In both methods, the time complexity is O(n) because they both iterate through the array once. The every() method uses a callback function to check each element, while the loop uses a simple comparison operation.
</p>
</details>

###### 70. How can you check if an array is a subset of another array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using every with includes:
const isSubset = (arr1, arr2) => arr2.every(element => arr1.includes(element));
console.log(isSubset([1, 2], [1, 2, 3, 4, 5])); // true
console.log(isSubset([1, 2, 6], [1, 2, 3, 4, 5])); // false

// Method 2: Using some with Negation
const subset = [10, 20];
const superset = [10, 20, 30];
const notSubset = [10, 40];

const isSubset = !subset.some(num => !superset.includes(num));

console.log("Is subset:", isSubset); // true
console.log("Not subset:", !isSubset); // true (using negation)
```

- Method 1:
    Uses every to check if every element in the first array (subset) is present in the second array (superset).
- Method 2:  some with Negation
    Uses some with negation to check if any element in the first array (subset) is not present in the second array (superset).

### Time Complexity
#### Method 1: Using every with includes
  - Time Complexity: O(nm)
  - Explanation: The every() method iterates through each element of arr2, and for each element, it checks if it exists in arr1 using the includes() method. This operation takes O(nm) time, where n is the length of arr2 and m is the length of arr1.

#### Method 2: Using some with Negation
  - Time Complexity: O(n)
  - Explanation: The some() method iterates through each element of subset, and for each element, it checks if it exists in superset using the includes() method. If any element is not found, it returns true immediately. If the loop completes without finding any elements not in superset, it returns false. This operation takes O(n) time, where n is the length of subset.

In Method 1, the time complexity is O(n*m) because it has to check each element of arr2 against all elements of arr1. In Method 2, the time complexity is O(n) because it only needs to check each element of subset once.
</p>
</details>

###### 71. How can you find the frequency of each word in a string array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using reduce() and Object
const words = ["apple", "banana", "apple", "orange", "banana"];
const wordFrequency = words.reduce((acc, curr) => {
  acc[curr] = (acc[curr] || 0) + 1;
  return acc;
}, {});
console.log(wordFrequency);

// Method 2: Using forEach() and Map
const wordMap = new Map();
words.forEach(word => {
  wordMap.set(word, (wordMap.get(word) || 0) + 1);
});
console.log([...wordMap]);

// Method 3: for...of Loop with Object Creation
const stringArray = ["apple", "banana", "apple", "orange", "banana"];

const wordCounts = {};
for (const word of stringArray) {
  if (wordCounts[word]) {
    wordCounts[word]++;
  } else {
    wordCounts[word] = 1;
  }
}

console.log(wordCounts); // { apple: 2, banana: 2, orange: 1 }

```

- Method 1: Using reduce() and Object
    Iterates through the string array, building an object where each key is a unique word and the value is its frequency.
- Method 3: for...of Loop with Object Creation
    Iterates through the string array, creating or updating an object to store word frequencies.

### Time Complexity
#### Method 1: Using reduce() and Object
  - Time Complexity: O(n)
  - Explanation: The reduce() method iterates through the array, and for each element, it updates the accumulator object by incrementing the value for the corresponding key. This operation takes O(n) time, where n is the length of the array.

#### Method 2: Using forEach() and Map
  - Time Complexity: O(n)
  - Explanation: The forEach() method iterates through the array, and for each element, it updates the Map by incrementing the value for the corresponding key. This operation takes O(n) time, where n is the length of the array.

#### Method 3: for...of Loop with Object Creation
  - Time Complexity: O(n)
  - Explanation: The for...of loop iterates through the array, and for each element, it updates the object by incrementing the value for the corresponding key. This operation takes O(n) time, where n is the length of the array.

All three methods have a time complexity of O(n), where n is the length of the input array. This is because they all iterate through the array once to count the frequency of each word.
</p>
</details>

###### 72. How can you rotate the elements of an array to the right by a specific number of positions?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: slice and concat
const numbers = [10, 20, 30, 40, 50];
const positions = 2; // Rotate right by 2 positions

const rotatedArray = numbers.slice(numbers.length - positions).concat(numbers.slice(0, numbers.length - positions));

console.log(rotatedArray); // [40, 50, 10, 20, 30]

console.log(numbers);

const array = [1, 2, 3, 4, 5];
const rotateBy = 2;
const rotatedArray = array.slice(-rotateBy).concat(array.slice(0, -rotateBy));
console.log(rotatedArray);

// Method 2: Using splice() and unshift()
const array2 = [1, 2, 3, 4, 5];
const rotateBy2 = 2;
array2.unshift(...array2.splice(-rotateBy2));
console.log(array2);

// Method 3: Using forEach
const newArray2 = [];const array = [1, 2, 3, 4, 5];
array.forEach(element => {
  newArray2.push(element === 3 ? 10 : element);
});
console.log(newArray2); // [1, 2, 10, 4, 5]
```

- Method 1: slice and concat
    Creates a new array by extracting a portion from the end (slice), concatenating it with the remaining elements (concat)

### Time Complexity
#### Method 1: Slice and Concat
- Time Complexity: O(n)
- Explanation: The slice() method creates two new arrays, one for the part of the original array from the end and one for the part of the original array from the beginning, excluding the last positions elements. The concat() method concatenates these two arrays. This operation takes O(n) time, where n is the length of the original array.

#### Method 2: Using splice() and unshift()
- Time Complexity: O(1)
- Explanation: The splice() method removes and returns a part of the original array (from the end), which is stored in a new variable. The unshift() method adds an element at the beginning of this new array. This operation takes constant time, O(1).

#### Method 3: Using foreach
- Time Complexity: O(n)
- Explanation: The forEach() method iterates through each element of the original array and adds it to a new array if it's not equal to 3. This operation takes O(n) time, where n is the length of the original array.

Note that in Method 2, splice() and unshift() operations take constant time, but overall the operation takes O(1) time because they are performed only once.
</p>
</details>

###### 73. How can you find the intersection of multiple arrays?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using reduce() and filter():
const arrays = [[1, 2, 3], [2, 3, 4], [3, 4, 5]];
const intersection = arrays.reduce((acc, curr) => acc.filter(element => curr.includes(element)));
console.log(intersection);


// Method 2: Using reduce() and Set():
const intersection2 = arrays.reduce((acc, curr) => acc.filter(element => new Set(curr).has(element)));
console.log(intersection2);
```

### Time Complexity
#### Method 1: Using reduce() and filter():
- Time Complexity: O(nmk)
- Explanation: The reduce() method iterates through the array of arrays, and for each inner array, it calls the filter() method. The filter() method iterates through the inner array and checks if each element is present in the other inner arrays. This operation takes O(nmk) time, where n is the number of arrays, m is the maximum length of an inner array, and k is the average length of an inner array.

#### Method 2: Using reduce() and Set():
- Time Complexity: O(nm)
- Explanation: The reduce() method iterates through the array of arrays, and for each inner array, it creates a new Set. The Set operations (add and contains) take constant time on average. The overall operation takes O(nm) time, where n is the number of arrays and m is the maximum length of an inner array.

Note that Method 2 has a better time complexity than Method 1 because Set operations are faster than iterating through arrays.
</p>
</details>

###### 74. How can you remove elements from an array without mutating the original array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using filter():
const originalArray = [1, 2, 3, 4, 5];
const newArray = originalArray.filter(element => element !== 3);
console.log(newArray);

// Method 2: Using slice():
const newArray2 = [...originalArray.slice(0, 2), ...originalArray.slice(3)];
console.log(newArray2);
```

### Time Complexity
#### Method 1: Using filter():
  - Time Complexity: O(n)
  - The filter() method iterates through the original array and checks each element against the condition (element !== 3). This operation takes O(n) time, where n is the length of the original array.

#### Method 2: Using slice():
  - Time Complexity: O(n)
  - The slice() method creates two new arrays, one for the part of the original array from the beginning (up to the 2nd element) and one for the part of the original array from the end (from the 3rd element to the end). The spread operator (...) is used to concatenate these two arrays. This operation takes O(n) time, where n is the length of the original array.

Both methods have a linear time complexity, but filter() is generally faster because it can stop iterating early if the condition is not met, whereas slice() has to iterate through the entire array even if it only needs to copy a small part of it.

</p>
</details>

###### 75. How can you find the nth element from the end of an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: Using slice() and reverse():
const nthElementFromEnd = array.slice().reverse()[n - 1];
console.log(nthElementFromEnd);


// Method 2: Using length:
const nthElementFromEnd2 = array[array.length - n];
console.log(nthElementFromEnd2);
```

### Time Complexity
#### Method 1: Using slice() and reverse():
  - Time Complexity: O(n)
  - The slice() method creates a shallow copy of the original array, which takes O(n) time, where n is the length of the array. Then, the reverse() method reverses the copied array, which also takes O(n) time.         Therefore, the overall time complexity is O(2n), which simplifies to O(n).

#### Method 2: Using length:
  - Time Complexity: O(1)
  - The length property of an array returns the length of the array, which is a constant-time operation. Accessing the element at a specific index (in this case, array.length - n) also takes constant time. Therefore, the overall time complexity is O(1), which is constant.

Method 2 is much more efficient than Method 1 because it only requires accessing a single element, whereas Method 1 requires creating a copy of the array and reversing it.
</p>
</details>

###### 76. How can you find the missing number in a sequential array of numbers?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1:  reduce with Expected Sum
const numbers = [1, 2, 3, 5]; // Missing number is 4

const expectedSum = (numbers.length + 1) * (numbers.length + 2) / 2; // Formula for arithmetic series sum
const actualSum = numbers.reduce((sum, num) => sum + num, 0);

console.log("Missing number:", expectedSum - actualSum);

// Method 2: Use Array Methods and Filtering
const numbers = [1, 2, 3, 5]; // Missing number is 4

const expectedLength = numbers.length + 1; // Calculate expected length
const actualLength = new Set(numbers).size; // Get the actual number of unique elements

const missingNumber = expectedLength > actualLength
  ? 1 // Missing number is at index 0 (assuming sequence starts from 1)
  : numbers.filter((num, i) => num !== (i + 1)).pop(); // Find element not matching expected index + 1

console.log("Missing number:", missingNumber);

// Method 3: XOR method
const numbers = [1, 2, 3, 5]; // Missing number is 4
function findMissingNumber(arr) {
    let missing = arr.length + 1;
    for (let i = 0; i < arr.length; i++) {
        missing ^= (i + 1) ^ arr[i];
    }
    return missing;
}
console.log(findMissingNumber(numbers));
```

### Time Complexity
#### Method 1:  reduce with Expected Sum
  - Time Complexity: O(n)
  - The reduce() method iterates through the numbers array, adding each element to the sum. This operation takes O(n) time, where n is the length of the array.

#### Method 2: Use Array Methods and Filtering
  - Time Complexity: O(n)
  - The filter() method iterates through the numbers array, checking each element against the condition (num !== (i + 1)). This operation also takes O(n) time, where n is the length of the array.

#### Method 3: XOR method
  - Time Complexity: O(n)
  - The findMissingNumber() function uses a for loop to iterate through the arr array, performing a bitwise XOR operation at each iteration. This operation also takes O(n) time, where n is the length of the array.

All three methods have a linear time complexity, with Method 1 being slightly more efficient because it only requires a single pass through the array. However, for small arrays, the difference in performance may not be noticeable.
</p>
</details>

###### 77. How can you find the second highest and second lowest elements in an array without sorting?
<details><summary><b>Solution</b></summary>
<p>

```javascript
function findSecondHighestAndLowest(arr) {
    let highest = arr[0];
    let secondHighest = -Infinity;
    let lowest = arr[0];
    let secondLowest = Infinity;

    for (let i = 1; i < arr.length; i++) {
        if (arr[i] > highest) {
            secondHighest = highest;
            highest = arr[i];
        } else if (arr[i] > secondHighest && arr[i] !== highest) {
            secondHighest = arr[i];
        }

        if (arr[i] < lowest) {
            secondLowest = lowest;
            lowest = arr[i];
        } else if (arr[i] < secondLowest && arr[i] !== lowest) {
            secondLowest = arr[i];
        }
    }

    return { secondHighest, secondLowest };
}

// Example usage
const arr = [10, 5, 7, 3, 8, 2, 9];
const { secondHighest, secondLowest } = findSecondHighestAndLowest(arr);
console.log("Second highest:", secondHighest); // Output: 9
console.log("Second lowest:", secondLowest); // Output: 3
```

### Time Complexity
The time complexity of the findSecondHighestAndLowest function is O(n), where n is the length of the input array arr.

Here's a breakdown of the time complexity:

- The function iterates through the array using a single for loop, which takes O(n) time.
- Within the loop, it performs a constant amount of work for each iteration, including:
    - Comparing the current element with the highest and second-highest values, and updating them if necessary.
    - Comparing the current element with the lowest and second-lowest values, and updating them if necessary.
    - The number of comparisons and updates is proportional to the length of the array, so the overall time complexity is O(n).
    - The space complexity is O(1), as the function only uses a constant amount of space to store the variables highest, secondHighest, lowest, and secondLowest.

</p>
</details>

###### 78. How can you convert a string array to a 2D array of characters?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1:  map and split:
const words = ["apple", "banana", "apple", "orange", "banana"];
function convertTo2DArray(arr) {
    return arr.map(str => str.split(''));
}
console.log(convertTo2DArray(words))

// Method 2: Nested for...of Loops:
const stringArray = ["hello", "world"];

const charArray = [];
for (const str of stringArray) {
  const charSubArray = [];
  for (const char of str) {
    charSubArray.push(char);  // Add each character to the sub-array
  }
  charArray.push(charSubArray); // Add the sub-array of characters to the main array
}

console.log(charArray); // [["h", "e", "l", "l", "o"], ["w", "o", "r", "l", "d"]]
```

- Method 1: This method iterates through the string array, using map to create a new array where each element is a sub-array of characters obtained by splitting the original string.
- Method 3: This method iterates through the string array using outer and inner loops. The outer loop iterates through each string, and the inner loop iterates through each character, creating a new sub-array for each string.

### Time Complexity
#### Method 1: map and split
  - Time Complexity: O(nm)
  - The map() function iterates through the words array, and for each element, it calls the split() function, which iterates through the string and creates an array of characters. Therefore, the total time complexity is O(nm), where n is the length of the words array and m is the average length of a string in the array.

#### Method 2: Nested for...of Loops
  - Time Complexity: O(nm)
  - The outer loop iterates through the stringArray (n times), and for each iteration, it iterates through each character of the string (m times) using the inner loop. Therefore, the total time complexity is also O(nm), where n is the length of the stringArray and m is the average length of a string in the array.

In both methods, the time complexity is quadratic because they both involve iterating through the input array and then iterating through each element of that array to create a new 2D array.
</p>
</details>

###### 79. How can you check if two arrays are circularly identical?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: 
function areCircularlyIdentical(arr1, arr2) {
  // Check if lengths are equal, otherwise not circularly identical
  if (arr1.length !== arr2.length) {
    return false;
  }

  // Concatenate the first array with itself to create a longer array
  const joined = arr1.concat(arr1);

  // Iterate through the concatenated array
  for (let i = 0; i < joined.length; i++) {
    let isEqual = true;

    // Check if a sub-array of length arr2.length starting from i in joined
    // is equal to arr2
    for (let j = 0; j < arr2.length; j++) {
      if (arr2[j] !== joined[i + j]) {
        isEqual = false;
        break;
      }
    }

    // If a match is found, return true
    if (isEqual) {
      return true;
    }
  }

  // If no match is found after iterating through all positions, return false
  return false;
}

// Example usage
const arr1 = [4, 5, 6];
const arr2 = [5, 6, 4];

const areIdentical = areCircularlyIdentical(arr1, arr2);
console.log("Arrays are circularly identical:", areIdentical);

// Method 2: 
function areCircularlyIdentical(arr1, arr2) {
  if (arr1.length !== arr2.length) {
    return false;
  }

  const combined = arr1.concat(arr1);

  for (let i = 0; i < arr1.length; i++) {
    const sliced = combined.slice(i, i + arr2.length); // Get sub-array of length arr2.length
    if (sliced.every((element, index) => element === arr2[index])) {
      return true;
    }
  }

  return false;
}

// Example usage
const arr1 = [1, 2, 3];
const arr2 = [2, 3, 1];

const areIdentical = areCircularlyIdentical(arr1, arr2);
console.log("Arrays are circularly identical:", areIdentical); // Output: true
```

This code effectively determines if two arrays are circularly identical by checking for the pattern of one array within the other array at different starting positions using a combined array.

### Time Complexity
#### Method 1:
The time complexity for Method 1 is O(n*m), where n is the length of the first array and m is the length of the second array. 

Here's a breakdown:

- The outer loop iterates through the concatenated array (which has a length of 2n), so that's O(n).
- The inner loop also iterates through the second array (of length m), so that's O(m).
- Since these are nested, the total time complexity is O(n*m).

#### Method 2:
The time complexity for Method 2 is also O(n*m), where n is the length of the first array and m is the length of the second array. 

Here's a breakdown:

- The outer loop iterates through the first array (of length n), so that's O(n).
- The inner loop iterates through a sub-array of length m, so that's O(m).
- Since these are nested, the total time complexity is O(n*m).

In both methods, the time complexity is quadratic because they both involve iterating through the input arrays in a nested manner.
</p>
</details>

###### 80. How can you find the index of the first element that is not equal to its index in an array?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Method 1: simple for loop
const numbers = [1, 2, 3, 5];
function findIndexNotEqualToIndex(arr) {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] !== i) {
            return i;
        }
    }
    return -1; // If all elements are equal to their index
}
console.log(findIndexNotEqualToIndex(numbers))

// Method 2: Using find()
const numbers = [1, 2, 3, 4, 6];

const indexMismatch = numbers.find((num, i) => num !== i);

console.log(numbers.indexOf(indexMismatch));  // Index of the mismatch
```

### Time Complexity
#### Method 1: Simple for loop
    The time complexity for Method 1 is O(n), where n is the length of the array.

Here's a breakdown:

- The loop iterates through the array once, so that's O(n).
- Method 2: Using find()
- The time complexity for Method 2 is also O(n), where n is the length of the array.

Here's a breakdown:

- The find() function iterates through the array once, so that's O(n).
- The indexOf() function after that also iterates through the array once, so that's O(n) again.
- Since these are chained together, the total time complexity is O(n).
- In both methods, the time complexity is linear because they both involve iterating through the input array once.
</p>
</details>
