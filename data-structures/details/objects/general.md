<div align="center">
  <img height="60" src="https://img.icons8.com/color/344/javascript.png">
  <h1>JavaScript Objects Questions</h1>
</div>

<p align="center">Create, Traverse & Manipulate Objects</p>


###### 1. How do you create an empty object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
// Using object literal notation
let obj1 = {};

// Using Object constructor
let obj2 = new Object();
```

### Time Complexity
The time complexity for creating an object in JavaScript using either object literal notation or the Object constructor is 𝑂(1).

In both cases, the steps to create an empty object are minimal and do not depend on any input size or other variable factors. Therefore, the time complexity for both methods is 
𝑂(1).

</p>
</details>

###### 2. How do you access properties of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
let obj = { name: "John", age: 30 };

// Dot notation
console.log(obj.name); // John

// Bracket notation
console.log(obj["age"]); // 30
```

### Time Complexity
In JavaScript, accessing properties of an object using dot notation or bracket notation has a time complexity of O(1), which is constant time. This is because JavaScript objects are implemented as hash tables, and accessing a value by its key in a hash table is an average-case O(1) operation.

Both operations are efficient and quick because they involve looking up the key in the hash table and retrieving the corresponding value.
</p>
</details>

###### 3. How do you add a new property to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
let obj = { name: "John" };

// Dot notation
obj.age = 30;

// Bracket notation
obj["city"] = "New York";
```

### Time Complexity
The time complexity of both dot notation and bracket notation for adding properties to a JavaScript object is generally considered to be O(1). This is because adding a property to an object typically involves a constant amount of work, regardless of the size of the object.
</p>
</details>

###### 4. How do you delete a property from an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
let obj = { name: "John", age: 30 };

// Using delete keyword
delete obj.age;
```

### Time Complexity
The time complexity of the delete operation in JavaScript is generally considered to be O(1) (constant time). This means that the operation takes a constant amount of time, regardless of the size of the object.
</p>
</details>

###### 5. How do you check if a property exists in an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
let obj = { name: "John", age: 30 };

// Using the 'in' operator
console.log("name" in obj); // true
console.log("city" in obj); // false
```

### Time Complexity
The time complexity of using the in operator to check if a property exists in an object is O(1) on average.

In JavaScript, objects are typically implemented using hash tables. When you check for the existence of a property using the in operator, the underlying implementation uses a hash function to find the property, which generally results in constant time complexity.

Here’s a summary of the time complexity:

- Average Case: O(1)
- Worst Case: O(n), where n is the number of properties in the object. This can happen in rare cases due to hash collisions or if the object is implemented using a different data structure.

However, for practical purposes and most use cases, you can consider the time complexity to be O(1).

</p>
</details>

###### 6. How do you iterate over the properties of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
let obj = { name: "John", age: 30 };

// Using for...in loop
for (let key in obj) {
  console.log(`${key}: ${obj[key]}`);
}

// Using Object.keys()
Object.keys(obj).forEach(key => {
  console.log(`${key}: ${obj[key]}`);
});

// Using Object.entries()
Object.entries(obj).forEach(([key, value]) => {
  console.log(`${key}: ${value}`);
});
```

### Time Complexity

#### Using for...in loop:
```javascript
let obj = { name: "John", age: 30 };
for (let key in obj) {
  console.log(`${key}: ${obj[key]}`);
}
```
- Time Complexity: O(n)
- Explanation: The for...in loop iterates over all enumerable properties of an object. The time complexity is O(n), where n is the number of enumerable properties in the object.

#### Using Object.keys():
```javascript
Object.keys(obj).forEach(key => {
  console.log(`${key}: ${obj[key]}`);
});
```
- Time Complexity: O(n)
- Explanation: Object.keys(obj) returns an array of the object's own enumerable property names. The forEach method then iterates over this array. Creating the array with Object.keys() takes O(n) time, and iterating over the array also takes O(n) time. Therefore, the overall time complexity is O(n).

#### Using Object.entries():
```javascript
Object.entries(obj).forEach(([key, value]) => {
  console.log(`${key}: ${value}`);
});
```
- Time Complexity: O(n)
- Explanation: Object.entries(obj) returns an array of the object's own enumerable property [key, value] pairs. The forEach method then iterates over this array. Creating the array with Object.entries() takes O(n) time, and iterating over the array also takes O(n) time. Therefore, the overall time complexity is O(n).

In all three cases, the time complexity is linear in relation to the number of properties in the object.
</p>
</details>

###### 7. How do you clone an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>
  
1. Using Object.assign: This method creates a shallow copy of the object.
```javascript
const clone = Object.assign({}, originalObject);
```
2. Using the Spread Operator: This also creates a shallow copy of the object.
```javascript
const clone = { ...originalObject };
```
3. Using JSON.stringify and JSON.parse: This creates a deep copy, but it has limitations (e.g., cannot clone functions or circular references).
```javascript
const clone = JSON.parse(JSON.stringify(originalObject));
```

### Time Complexity
#### Using Object.assign:
- Time Complexity: O(n)
- Explanation: The Object.assign method copies all enumerable own properties from one or more source objects to a target object. The time complexity depends on the number of properties in the originalObject, hence it is O(n), where n is the number of properties in the object.
#### Using the Spread Operator:
- Time Complexity: O(n)
- Explanation: The spread operator (...) creates a shallow copy of the object by copying all enumerable own properties to the new object. Similar to Object.assign, the time complexity is O(n), where 
n is the number of properties in the object.
#### Using JSON.stringify and JSON.parse:
- Time Complexity: O(n)
- Explanation: The JSON.stringify method converts a JavaScript object to a JSON string, and JSON.parse parses the JSON string back into an object. The combined process involves iterating over all properties of the object twice (once for stringify and once for parse). Therefore, the time complexity is (n), where n is the number of properties in the object. However, it also depends on the size of the values within the object, which can affect the time complexity in practice.

In summary:
- Object.assign: O(n)
- Spread Operator: O(n)
- JSON.stringify and JSON.parse: O(n)
In all cases, n represents the number of properties in the object.
</p>
</details>

###### 8. How do you merge two objects in JavaScript?
<details><summary><b>Solution</b></summary>
<p>
  
1. Using Object.assign: This method merges two or more objects, modifying the target object.
```javascript
const merged = Object.assign({}, obj1, obj2);
```
2. Using the Spread Operator: This creates a new object by merging the properties of two objects.
```javascript
const merged = { ...obj1, ...obj2 };
```
3. Using a Library like Lodash: Lodash provides a merge function for deep merging.
```javascript
const merged = _.merge({}, obj1, obj2);
```

### Time Complexity
- Object.assign: O(n), where n is the total number of properties in the source objects.
- Spread Operator (...): O(n), where n is the total number of properties in the source objects.
- Lodash's _.merge: O(m) in the worst case, where m is the total number of properties across all levels of nesting in the source objects. O(n) if the objects are shallow.

In general, for shallow merges (i.e., objects without nested properties), all three methods have a linear time complexity, O(n). For deep merges, Lodash's _.merge can have higher time complexity depending on the depth and number of properties in the nested objects.

<details><summary><b>Details</b></summary>
<p>
The time complexity for merging objects in JavaScript depends on the number of properties in the objects being merged. Here's a breakdown of the time complexity for each method mentioned:

#### Using Object.assign: 
This method copies properties from one or more source objects to a target object. The time complexity is O(n), where n is the total number of properties in the source objects (obj1 and obj2). This is because each property needs to be iterated over and copied to the target object.

```javascript
const merged = Object.assign({}, obj1, obj2);
```
#### Using the Spread Operator: 
This method creates a new object by copying properties from the source objects. The time complexity is O(n), where n is the total number of properties in the source objects (obj1 and obj2). Similar to Object.assign, each property needs to be iterated over and copied to the new object.

```javascript
const merged = { ...obj1, ...obj2 };
```
#### Using a Library like Lodash's _.merge: 
Lodash's merge function performs a deep merge, meaning it recursively merges properties. The time complexity can vary depending on the depth of the objects. In the worst case, where the objects have nested properties, the time complexity can be O(m), where m is the total number of properties across all levels of nesting in the objects (obj1 and obj2). If the objects are shallow (no nested properties), the time complexity would be O(n), similar to the previous methods.

```javascript
const merged = _.merge({}, obj1, obj2);
```
</p>
</details>

</p>
</details>

###### 9. How do you compare two objects for equality in JavaScript?
<details><summary><b>Solution</b></summary>
<p>
  
1. Using JSON.stringify: This compares the JSON representation of two objects, but it only works for simple objects without functions or circular references.
```javascript
const isEqual = JSON.stringify(obj1) === JSON.stringify(obj2);
```
2. Using a Library like Lodash: Lodash provides a isEqual function for deep equality comparison.
```javascript
const isEqual = _.isEqual(obj1, obj2);
```
3. Using a Custom Recursive Function: This is a custom function that recursively compares each property of the objects.
```javascript
function isObject(obj) {
  return obj !== null && typeof obj === 'object';
}

function deepEqual(obj1, obj2) {
  if (obj1 === obj2) {
    return true;
  }

  if (!isObject(obj1) || !isObject(obj2)) {
    return false;
  }

  const keys1 = Object.keys(obj1);
  const keys2 = Object.keys(obj2);

  if (keys1.length !== keys2.length) {
    return false;
  }

  for (let key of keys1) {
    if (!keys2.includes(key) || !deepEqual(obj1[key], obj2[key])) {
      return false;
    }
  }

  return true;
}

// Examples
const obj1 = { a: 1, b: { c: "a", d: { e: [2,3] } } };
const obj2 = { a: 1, b: { c: "a", d: { e: [2,3] } } };
const obj3 = { a: 1, b: { c: 3 } };

console.log(deepEqual(obj1, obj2)); // Output: true
console.log(deepEqual(obj1, obj3)); // Output: false
```

### Time Complexity
#### 1. Using JSON.stringify
The time complexity of comparing two objects using JSON.stringify depends on two factors: the time complexity of JSON.stringify itself and the string comparison.

- `JSON.stringify` Time Complexity: O(n), where n is the size of the object (number of properties and the length of strings).
- String Comparison Time Complexity: O(m), where m is the length of the resulting JSON strings.

Therefore, the overall time complexity is O(n + m), which simplifies to O(n) if we assume the size of the object and the length of the JSON strings are proportional.

#### 2. Using Lodash _.isEqual
The time complexity of Lodash's _.isEqual function is O(n), where n is the number of properties in the objects being compared. Lodash's _.isEqual function is optimized for deep comparison, including handling circular references, arrays, and nested objects efficiently.

#### 3. Using a Custom Recursive Function
- The time complexity of a custom recursive function for deep equality comparison depends on the implementation, but generally, it can be approximated as O(n), where n is the number of properties in the objects being compared. This assumes a well-implemented function that checks all properties recursively.
- The time complexity of the deepEqual function is O(n) in the worst case, where n is the total number of properties in the objects being compared. This complexity arises because each property of the object and its sub-objects are compared recursively. Additionally, the use of `Object.keys()` and `Array.includes()` both have a time complexity of O(m), where m is the number of keys, making the overall complexity proportional to the size of the nested structure.

In summary:

- Using JSON.stringify: O(n)
- Using Lodash _.isEqual: O(n)
- Using a Custom Recursive Function: O(n)

In all cases, n represents the size of the objects, including the number of properties and the depth of nested structures. The specific constant factors and overhead may vary, but the asymptotic complexity remains O(n).
</p>
</details>

###### 10. How do you convert an object to a JSON string in JavaScript?
<details><summary><b>Solution</b></summary>
<p>
  
```javascript
const jsonString = JSON.stringify(obj);
```

### Time Complexity
The time complexity of JSON.stringify(obj) depends on the size and structure of the object obj.

- Primitive Values: If obj is a primitive value (like a number, string, or boolean), the time complexity is O(1).

- Simple Objects: For simple objects (those without nested objects or arrays), the time complexity is O(n), where n is the number of key-value pairs in the object. This is because each key-value pair needs to be processed.

- Nested Objects and Arrays: For objects that contain nested objects or arrays, the time complexity becomes O(m), where m is the total number of elements (including nested ones) that need to be serialized. This includes all nested properties and array elements.

In summary, the time complexity of JSON.stringify(obj) is:
- O(1) for primitive values.
- O(n) for simple objects with n key-value pairs.
- O(m) for complex objects with m total elements, including nested ones.

</p>
</details>

###### 11. How do you convert a JSON string to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const obj = JSON.parse(jsonString);
```

### Time Complexity
The time complexity of the JSON.parse function in JavaScript, which is used to parse a JSON string into an object, is generally O(n), where n is the length of the JSON string.

Explanation:
- The `JSON.parse` function needs to read and process each character of the JSON string to construct the corresponding JavaScript object.
- This involves iterating over the string and parsing the various components, such as objects, arrays, strings, numbers, booleans, and null values.

Since each character of the input string is processed exactly once, the time complexity is linear with respect to the length of the input string. Hence, the time complexity of JSON.parse(jsonString) is O(n).

</p>
</details>

###### 12. What is the difference between dot notation and bracket notation in accessing object properties?
<details><summary><b>Solution</b></summary>
<p>
  
Dot notation is used to access object properties using a fixed property name:
```javascript
const value = obj.propertyName;
```
Bracket notation allows you to access properties dynamically or when the property name is a reserved keyword:
```javascript
const value = obj['propertyName'];
```

### Time Complexity
Both dot notation and bracket notation provide O(1) time complexity for property access in JavaScript objects.
</p>
</details>

###### 13. How do you define a method for an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>
  
```javascript
const obj = {
    methodName() {
        // Method implementation
    }
};
```

### Time Complexity
The time complexity of defining a method within an object literal in JavaScript, as shown in your example, is O(1). This is because creating an object and assigning properties to it, including methods, involves constant time operations.
</p>
</details>

###### 14. How do you call a method of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>
  
```javascript
obj.methodName();
```

### Time Complexity
The time complexity of calling a method on an object in JavaScript (or any other programming language) depends on what the method is doing. The obj.methodName() syntax itself does not inherently have a specific time complexity because it is a way to invoke a function. The time complexity depends on the operations performed within methodName.

Here's a breakdown of factors that determine the time complexity:

- Constant Time Operations (O(1)): If the method performs a fixed number of operations regardless of the size of the input, it has constant time complexity. For example:
```javascript
obj.methodName = function() {
    return this.property; // Assuming accessing `property` is O(1)
}
```

- Linear Time Operations (O(n)): If the method iterates over an array or a list of length n, it has linear time complexity. For example:
```javascript
obj.methodName = function(arr) {
    for (let i = 0; i < arr.length; i++) {
        console.log(arr[i]);
    }
}
```

- Quadratic Time Operations (O(n^2)): If the method contains nested loops that iterate over an array or list, it may have quadratic time complexity. For example:
```javascript
obj.methodName = function(arr) {
    for (let i = 0; i < arr.length; i++) {
        for (let j = 0; j < arr.length; j++) {
            console.log(arr[i], arr[j]);
        }
    }
}
```
- Logarithmic Time Operations (O(log n)): If the method involves operations that reduce the problem size by a factor of two (e.g., binary search), it has logarithmic time complexity. For example:
```javascript
obj.methodName = function(arr, target) {
    let left = 0, right = arr.length - 1;
    while (left <= right) {
        const mid = Math.floor((left + right) / 2);
        if (arr[mid] === target) return mid;
        if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}
```
Other Complexities: Depending on the operations performed, the method can have other complexities like O(n log n), O(n^3), etc.

To determine the exact time complexity of obj.methodName(), you would need to analyze the code inside methodName. If you provide the code of the method, I can help you determine its time complexity.

</p>
</details>

###### 15. How do you define a getter and setter for a property in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

In JavaScript, you can define getters and setters for a property in several ways. Here are three common methods:

### 1. Using Object.defineProperty
The Object.defineProperty method allows you to define getters and setters for a property on an object.

```javascript
const person = {};
Object.defineProperty(person, "name", {
  get() {
    return this._name;
  },
  set(value) {
    this._name = value;
  }
});

person.name = "Alice";
console.log(person.name); // Output: Alice
```

#### Time Complexity
- Definition: O(1) - Object.defineProperty is a single operation.
- Get/Set: O(1) - Simple property access or assignment.


### 2. Using Accessors (Modern Syntax)
You can define getters and setters directly within an object literal using the get and set keywords.

```javascript
const person = {
  get name() {
    return this._name;
  },
  set name(value) {
    this._name = value;
  }
};

person.name = "Bob";
console.log(person.name); // Output: Bob
```

#### Time Complexity:
- Definition: O(1) - Directly defined within the object literal.
- Get/Set: O(1) - Simple property access or assignment.

### 3. Using Prototype-based Getters and Setters
If you are using constructor functions, you can define getters and setters on the prototype of the constructor.

```javascript
function Person() {
  this._name = undefined;
}

Person.prototype = {
  get name() {
    return this._name;
  },
  set name(value) {
    this._name = value;
  }
};

const person = new Person();
person.name = "Charlie";
console.log(person.name); // Output: Charlie
```

Explanation
- Getter (get): A getter allows you to define a method that will be called when the property is accessed.
- Setter (set): A setter allows you to define a method that will be called when a value is assigned to the property.

#### Time Complexity:
- Definition: O(1) - Defining the prototype with getters and setters is a single operation.
- Instantiation: O(1) - Creating a new instance with new Person() is also a single operation.
- Get/Set: O(1) - Simple property access or assignment within the getter and setter functions.

Using prototypes allows for the efficient sharing of methods among all instances of a constructor function, making it a powerful tool for defining methods like getters and setters in JavaScript.


### Using ES6 Classes
If you are using ES6 classes, you can define getters and setters within the class definition.

```javascript
class Person {
  constructor() {
    this._name = undefined;
  }

  get name() {
    return this._name;
  }

  set name(value) {
    this._name = value;
  }
}

const person = new Person();
person.name = "David";
console.log(person.name); // Output: David
```

### Time Complexity:
- Definition: O(1) - Defined within the class.
- Get/Set: O(1) - Simple property access or assignment.

Each of these methods allows you to create encapsulated properties, providing control over how properties are accessed and modified.

</p>
</details>

###### 16. How do you create an object with a specific prototype in JavaScript?
<details><summary><b>Solution</b></summary>
<p>


- **Prototype:** An object that serves as a blueprint for creating new objects. It holds properties and methods that can be inherited by objects created from that prototype.
- **Prototype Chain:** The mechanism in JavaScript by which an object can inherit properties and methods from its prototype, and then its prototype's prototype, and so on, until a null prototype is reached.
  
Object.create:
```javascript
const personPrototype = {
  greet() {
    console.log("Hello!");
  }
};

const person = Object.create(personPrototype);
person.greet(); // Output: Hello!
```

### Time Complexity:
Object.create: O(1) - Creating an object using Object.create is a single operation.

Constructor functions (with prototype property):
```javascript
function Person() {
  this.greet = function() {
    console.log("Hi!");
  };
}

Person.prototype.talk = function() {
  console.log("Talking...");
};

const person = new Person();
person.greet(); // Output: Hi!
person.talk();    // Output: Talking...
```

### Time Complexity:
- Constructor Function Execution: O(1) - Creating an instance using a constructor function is a single operation.
- Adding Methods to Prototype: O(1) - Adding a method to the prototype of a constructor function is also a single operation.
- Method Execution: O(1) - Calling a method on an object is a single operation.

In both cases, the time complexity is O(1) for creating objects, executing constructor functions, adding methods to prototypes, and executing methods.

</p>
</details>

###### 17. How do you check the prototype of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

  
Object.create:
```javascript
const obj = {};
console.log(obj.__proto__ === Object.prototype); // Output: true (default prototype)

function Person() {}
const person = new Person();
console.log(person.__proto__ === Person.prototype); // Output: true (custom prototype)
```

### Time Complexity:
- Object creation with {}: O(1) - Creating an object with an object literal {} is a single operation.
- Prototype Check (obj.__proto__): O(1) - Accessing the __proto__ property and comparing it to Object.prototype is a single operation.

- Constructor Function Execution (new Person()): O(1) - Creating an instance using a constructor function is a single operation.
- Prototype Check (person.__proto__): O(1) - Accessing the __proto__ property and comparing it to Person.prototype is a single operation.

Summary:

- Object Creation with {}:
    - Creation: O(1)
    - Prototype Check: O(1)
- Constructor Function (new Person()):
    - Creation: O(1)
    - Prototype Check: O(1)

</p>
</details>

###### 18. How do you set the prototype of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

  
Object.setPrototypeOf (modern):
```javascript
const obj = {};
const personPrototype = {
  greet() {
    console.log("Hello from prototype!");
  }
};
Object.setPrototypeOf(obj, personPrototype);
obj.greet(); // Output: Hello from prototype!
```
Direct assignment (legacy):
```javascript
obj.__proto__ = personPrototype; // Not recommended in modern JavaScript due to potential issues
```

### Time Complexity

#### 1. Object.setPrototypeOf (Modern):
- Object.setPrototypeOf: O(1) - Setting the prototype of an object is a single operation.
- Method Execution (obj.greet()): O(1) - Calling a method on the object is a single operation.

#### 2. Direct Assignment (__proto__) (Legacy):
- Direct Assignment (obj.__proto__ = personPrototype): O(1) - Directly assigning the prototype is a single operation.
- Method Execution (obj.greet()): O(1) - Calling a method on the object is a single operation.

Summary:
- Object.setPrototypeOf:
    - Prototype Setting: O(1)
    - Method Execution: O(1)
- Direct Assignment (__proto__):
    - Prototype Setting: O(1)
    - Method Execution: O(1)

</p>
</details>

###### 19. How do you create an object without a prototype in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Object.create(null):
```javascript
const obj = Object.create(null);
console.log(obj.hasOwnProperty('__proto__')); // Output: false (no prototype)
```
Using a constructor function that doesn't set a prototype:
```javascript
function NoPrototypeObject() {} // Function body empty

const obj = new NoPrototypeObject();
console.log(obj.hasOwnProperty('__proto__')); // Output: false (no prototype)
```
Important Note: Creating objects without a prototype is generally not recommended as it can lead to unexpected behavior and difficulty with inheritance.

### Time Complexity

#### 1. Object.create(null):
- Object.create(null): O(1) - Creating an object with Object.create(null) is a single operation, resulting in an object with no prototype.
- Property Check (obj.hasOwnProperty('__proto__')): O(1) - Checking if the object has its own property is a single operation.

#### 2. Using a Constructor Function That Doesn't Set a Prototype:
- Constructor Function Execution (new NoPrototypeObject()): O(1) - Creating an instance using an empty constructor function is a single operation.
- Property Check (obj.hasOwnProperty('__proto__')): O(1) - Checking if the object has its own property is a single operation.

Summary:

- Object.create(null):
    - Object Creation: O(1)
    - Property Check: O(1)
- Constructor Function Without Prototype:
    - Object Creation: O(1)
    - Property Check: O(1)

</p>
</details>

###### 20. How do you check if an object is an instance of a specific class in JavaScript?
<details><summary><b>Solution</b></summary>
<p>


```javascript
function Car(make, model) {
  this.make = make;
  this.model = model;
}

const car1 = new Car("Toyota", "Camry");

// Solution 1: instanceof operator (checks prototype chain)
console.log(car1 instanceof Car); // Output: true

// Solution 2: constructor property (less reliable, can be modified)
console.log(car1.constructor === Car); // Output: true (assuming `Car` constructor hasn't been changed)

// Solution 3: Custom Symbol.hasInstance method (advanced, for more control)
// (Implementation omitted for brevity, refer to advanced JavaScript references)
```

### Time Complexity
- Constructor Function Execution: O(1) - Creating an instance using a constructor function is a single operation.
- `instanceof` Operator: O(n) - The `instanceof` operator checks the prototype chain, which can take linear time in the worst case if the prototype chain is long. Here, n is the length of the prototype chain.
- `constructor` Property: O(1) - Accessing the `constructor` property and comparing it is a single operation.
- Custom `Symbol.hasInstance` Method (Advanced): This would depend on the custom implementation of the `Symbol.hasInstance` method. Generally, the custom implementation would be designed to be efficient, but specifics would vary based on how it's written. The check itself (once defined) would typically be O(1), but any additional logic within the method could vary.

Summary:
- Constructor Function Execution (new Car(...)): O(1)
- `instanceof` Operator: O(n) - Checks the prototype chain, linear time complexity.
- `constructor` Property Check: O(1) - Direct property access and comparison.
- Custom `Symbol.hasInstance` Method: Typically O(1) (depending on implementation details).

</p>
</details>

###### 21. How do you define a class in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Traditional constructor function:
```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
  this.introduce = function() {
    console.log(`Hi, I'm ${this.name} and I'm ${this.age} years old.`);
  };
}

const person1 = new Person("Alice", 30);
person1.introduce(); // Output: Hi, I'm Alice and I'm 30 years old.
```
Modern class syntax (ES6+):
```javascript
class Student {
  constructor(name, major) {
    this.name = name;
    this.major = major;
  }

  greet() {
    console.log(`Hello, my name is ${this.name} and I'm majoring in ${this.major}.`);
  }
}

const student1 = new Student("Bob", "Computer Science");
student1.greet(); // Output: Hello, my name is Bob and I'm majoring in Computer Science.
```

### Time Complexity 
- Traditional Constructor Function:
    - Constructor Function Execution (new Person(...)): O(1) - Creating an instance and initializing properties is a single operation.
    - Method Execution (person1.introduce()): O(1) - Executing the introduce method is a single operation.

- Modern Class Syntax (ES6+):
    - Constructor Execution (new Student(...)): O(1) - Creating an instance and initializing properties is a single operation.
    - Method Execution (student1.greet()): O(1) - Executing the greet method is a single operation.

Summary:
- Traditional Constructor Function:
    - Instance Creation and Initialization: O(1)
    - Method Execution: O(1)
- Modern Class Syntax:
    - Instance Creation and Initialization: O(1)
    - Method Execution: O(1)

</p>
</details>

###### 22. How do you create an instance of a class in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using the new keyword:
```javascript
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}

const person1 = new Person("Alice", 30);
console.log(person1.name); // Output: Alice
console.log(person1.age); // Output: 30
```
Using a factory function (less common):
```javascript
function createPerson(name, age) {
  return { name, age };
}

const person2 = createPerson("Bob", 25);
console.log(person2.name); // Output: Bob
console.log(person2.age); // Output: 25
```

### Time Complexity
#### Using the new Keyword:
- Constructor Execution (new Person(...)): O(1) - Creating an instance and initializing properties is a single operation.
- Property Access (person1.name, person1.age): O(1) - Accessing properties of the object is a single operation.
#### Using a Factory Function (Less Common):
- Factory Function Execution (createPerson(...)): O(1) - Creating an object and initializing properties is a single operation.
- Property Access (person2.name, person2.age): O(1) - Accessing properties of the object is a single operation.

Summary:
- Using the new Keyword:
    - Instance Creation and Initialization: O(1)
    - Property Access: O(1)
- Using a Factory Function:
    - Instance Creation and Initialization: O(1)
    - Property Access: O(1)

</p>
</details>

###### 23. How do you define static methods in a class in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Declare methods directly on the class (using the static keyword):
```javascript
class MathUtils {
  static add(x, y) {
    return x + y;
  }

  static subtract(x, y) {
    return x - y;
  }
}

console.log(MathUtils.add(5, 3)); // Output: 8 (can be called without creating an instance)
```

### Time Complexity Analysis
- Static Method Declaration: O(1) - Declaring static methods on the class is a compile-time operation and does not affect runtime complexity.
- Static Method Execution:
    - MathUtils.add(5, 3): O(1) - Executing the add method involves a single addition operation, which is constant time.
    - MathUtils.subtract(5, 3): O(1) - Executing the subtract method involves a single subtraction operation, which is constant time.

Summary:
- Static Method Declaration: O(1)
- Static Method Execution (e.g., MathUtils.add, MathUtils.subtract): O(1)

</p>
</details>

###### 24. How do you define private properties and methods in a class in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Use weak maps (modern) or closures (older approach):
```javascript
class User {
  constructor(name) {
    const _email = name + "@example.com"; // Private property using closure

    this.getName = () => name; // Private method using arrow function

    this.getEmail = () => { // Public getter for private property
      return _email;
    };
  }
}

const user1 = new User("John");
console.log(user1.getName()); // Output: John (public method)
console.log(user1.getEmail()); // Output: John@example.com (public getter)
// console.log(user1._email); // Error: _email is not accessible outside the constructor
```
Note: JavaScript doesn't have true private properties and methods, but these techniques simulate privacy.

### Time Complexity
- Constructor Execution (new User("John")): O(1) - Creating an instance and initializing private properties using closures is a single operation.
- Method Execution (user1.getName()): O(1) - Executing the getName method involves returning a stored value, which is a constant time operation.
- Method Execution (user1.getEmail()): O(1) - Executing the getEmail method involves returning a value stored in the closure, which is a constant time operation.

Summary:
    - Instance Creation and Initialization: O(1)
    - Method Execution (getName, getEmail): O(1)

</p>
</details>

###### 25. How do you define inheritance in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Prototypal inheritance (traditional):
```javascript
function Animal(type) {
  this.type = type;
}

Animal.prototype.makeSound = function() {
  console.log("Generic animal sound");
};

function Dog(name, breed) {
  this.name = name;
  this.breed = breed;
}

// Set Dog's prototype to be an instance of Animal
Dog.prototype = Object.create(Animal.prototype);
Dog.prototype.constructor = Dog; // Reset constructor to Dog

const dog1 = new Dog("Buddy", "Labrador");
console.log(dog1.type); // Output: animal (inherited)
dog1.makeSound(); // Output: Generic animal sound (inherited)
```

### Time Complexity
- Instance Creation and Initialization (new Dog("Buddy", "Labrador")):
    - TC: O(1) - Creating an instance and setting up prototype chain is a single operation.
- Method Execution (dog1.makeSound()):
    - TC: O(1) - Executing the makeSound method involves a single method call.

Using classes (ES6+):
```javascript
class Animal {
  constructor(type) {
    this.type = type;
  }

  makeSound() {
    console.log("Generic animal sound");
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(type); // Call superclass constructor with arguments
    this.name = name;
    this.breed = breed;
  }

  bark() {
    console.log("Woof!");
  }
}

const dog2 = new Dog("Charlie", "Golden Retriever");
console.log(dog2.type); // Output: animal
dog2.makeSound(); // Output: Generic animal sound (inherited)
dog2.bark(); // Output: Woof! (specific to Dog)
```

### Time Complexity
- Instance Creation and Initialization (new Dog("Charlie", "Golden Retriever")):
    - Time Complexity: O(1) - Creating an instance and setting up prototype chain is a single operation.
- Method Execution (dog2.makeSound(), dog2.bark()):
    - Time Complexity: O(1) - Executing the methods involves single method calls.

Summary:
- Instance Creation and Initialization: O(1)
- Method Execution: O(1)

</p>
</details>

###### 26. How do you call a superclass method from a subclass method in JavaScript?
<details><summary><b>Solution</b></summary>
<p>


```javascript
class Animal {
  constructor(type) {
    this.type = type;
  }

  makeSound() {
    console.log("Generic animal sound");
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(type); // Call superclass constructor with arguments (if applicable)
    this.name = name;
    this.breed = breed;
  }

  bark() {
    console.log("Woof!");
    // Call the superclass makeSound method as well (optional)
    super.makeSound();
  }
}

const dog2 = new Dog("Charlie", "Golden Retriever");
dog2.bark(); // Output: Woof! (from Dog)
              //         Generic animal sound (from Animal)
```

##### Explanation:
The super keyword within the subclass method (bark in this case) allows you to access and call methods defined in the superclass (Animal).
You can optionally call the superclass method along with your subclass's specific behavior.

##### Additional Notes:
Inheritance in JavaScript is based on prototypes, not strict class-based inheritance like in some other languages.
Understanding prototypal inheritance is crucial for working effectively with JavaScript objects and classes.

### Time Complexity:
- Instance Creation and Initialization (new Dog("Charlie", "Golden Retriever")):
    - TC: O(1) - Creating an instance and setting up the prototype chain is a single operation.
- Method Execution (dog2.bark()):
    - TC: O(1) - Executing the bark method involves calling console.log, which is a constant time operation, and calling super.makeSound(), which also involves a single method call.

Summary:
- Instance Creation and Initialization: O(1)
- Method Execution: O(1)

</p>
</details>

###### 27. How do you override a method in a subclass in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Redefine the method in the subclass:
```javascript
class Animal {
  constructor(type) {
    this.type = type;
  }

  makeSound() {
    console.log("Generic animal sound");
  }
}

class Dog extends Animal {
  constructor(name, breed) {
    super(type); // Call superclass constructor (if applicable)
    this.name = name;
    this.breed = breed;
  }

  // Override the makeSound method in Dog
  makeSound() {
    console.log("Woof!");
  }
}

const dog1 = new Dog("Buddy", "Labrador");
dog1.makeSound(); // Output: Woof! (overrides Animal's makeSound)
```

### Time Complexity Analysis:
- Instance Creation and Initialization (new Dog("Buddy", "Labrador")):
    - TC: O(1) - Creating an instance and setting up the prototype chain is a single operation.
- Method Execution (dog1.makeSound()):
    - Time Complexity: O(1) - Executing the makeSound method in Dog involves calling console.log, which is a constant time operation.

Summary:
- Instance Creation and Initialization: O(1)
- Method Execution: O(1)

</p>
</details>

###### 28. How do you check if an object is iterable in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using the typeof operator (not always reliable):
```javascript
function isIterable(obj) {
  return typeof obj[Symbol.iterator] === "function";
}

const numbers = [1, 2, 3];
const text = "Hello"; // Not iterable

console.log(isIterable(numbers)); // Output: true
console.log(isIterable(text));   // Output: false
```

Time Complexity: O(1) - Checking the `typeof` operator and accessing the `Symbol.iterator` property is a constant time operation.

Using the Symbol.iterator property (more robust):
```javascript
function isIterable(obj) {
  return obj !== null && typeof obj[Symbol.iterator] === "function";
}

const map = new Map();
const set = new Set();

console.log(isIterable(map));  // Output: true
console.log(isIterable(set));  // Output: true
```

Time Complexity: O(1) - Checking the presence of `Symbol.iterator` property and its type is a constant time operation.

Summary:
- `typeof` Operator: O(1)
- `Symbol.iterator` Property Check: O(1)

</p>
</details>

###### 29. How do you iterate over the keys of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using the for...in loop:
```javascript
const person = { name: "Alice", age: 30 };

for (const key in person) {
  console.log(key); // Output: name, age
}
```

Time Complexity: O(n) - Where n is the number of enumerable properties in the object. The for...in loop iterates over all enumerable properties of an object, including inherited ones.

Using Object.keys (modern, doesn't iterate over inherited properties):
```javascript
const person = { name: "Alice", age: 30 };

const keys = Object.keys(person);
for (const key of keys) {
  console.log(key); // Output: name, age
}
```

Time Complexity: O(n) - Where n is the number of own enumerable properties in the object. Object.keys returns an array of a given object's own enumerable property names, iterating only over the object's own properties and not inherited ones.

Summary:
- for...in Loop: O(n) - Iterates over all enumerable properties, including inherited ones.
- Object.keys: O(n) - Iterates over only own enumerable properties, excluding inherited ones.

</p>
</details>

###### 30. How do you iterate over the values of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using a for...in loop with bracket notation (iterate over own properties only):
```javascript
const person = { name: "Alice", age: 30 };

for (const key in person) {
  if (person.hasOwnProperty(key)) {
    console.log(person[key]); // Output: Alice, 30
  }
}
```

Time Complexity: O(n) - Where n is the number of own enumerable properties in the object. The for...in loop iterates over all enumerable properties of an object, including inherited ones, but filtering out non-own properties using hasOwnProperty.

Using Object.values (modern, doesn't iterate over inherited properties):
```javascript
const person = { name: "Alice", age: 30 };

const values = Object.values(person);
for (const value of values) {
  console.log(value); // Output: Alice, 30
}
```

Time Complexity: O(n) - Where n is the number of own enumerable properties in the object. Object.values returns an array of a given object's own enumerable property values, iterating only over the object's own properties and not inherited ones.

Summary:
- `for...in` Loop with hasOwnProperty: O(n) - Iterates over all enumerable properties, including inherited ones, but filters out non-own properties using hasOwnProperty.
- `Object.values`: O(n) - Iterates over only own enumerable property values, excluding inherited ones.

</p>
</details>

###### 31. How do you iterate over the entries of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using Object.entries (modern):
```javascript
const person = { name: "Alice", age: 30 };

for (const [key, value] of Object.entries(person)) {
  console.log(key, value); // Output: name Alice, age 30
}
```

Time Complexity: O(n) - Where n is the number of own enumerable properties in the object. `Object.entries` returns an array of a given object's own enumerable property [key, value] pairs, iterating over only the object's own properties and not inherited ones.

</p>
</details>

###### 32. How do you convert an object to an array in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using Object.values for values (modern):
```javascript
const person = { name: "Alice", age: 30 };
const valuesArray = Object.values(person);
console.log(valuesArray); // Output: ["Alice", 30]
```

Time Complexity: Object.values O(n) - Iterates over only own enumerable properties, excluding inherited ones, to extract values from the object.

Using Object.keys and mapping for key-value pairs (modern):
```javascript
const person = { name: "Alice", age: 30 };
const entriesArray = Object.keys(person).map(key => [key, person[key]]);
console.log(entriesArray); // Output: [["name", "Alice"], ["age", 30]]
```

Time Complexity: Object.keys and Mapping O(n) - Iterates over only own enumerable properties, excluding inherited ones, to extract key-value pairs from the object.

Using a loop with spread syntax (older approach):
```javascript
const person = { name: "Alice", age: 30 };
const valuesArray = [];
for (const key in person) {
  valuesArray.push(person[key]);
}
console.log(valuesArray); // Output: ["Alice", 30]
```

Time Complexity: Loop with Spread Syntax O(n) - Iterates over only own enumerable properties, excluding inherited ones, to extract values from the object.

</p>
</details>

###### 33. How do you convert an array to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using Object.fromEntries (modern):
```javascript
const names = ["Alice", "Bob", "Charlie"];
const nameObject = Object.fromEntries(names.map((name, index) => [index, name]));
console.log(nameObject); // Output: {0: "Alice", 1: "Bob", 2: "Charlie"}
```

Time Complexity: Object.fromEntries O(n) - Iterates over each element in the array to create key-value pairs for the resulting object.

Using a loop with object literal syntax:
```javascript
const names = ["Alice", "Bob", "Charlie"];
const nameObject = {};
for (let i = 0; i < names.length; i++) {
  nameObject[i] = names[i];
}
console.log(nameObject); // Output: {0: "Alice", 1: "Bob", 2: "Charlie"}
```

Time Complexity: Loop with Object Literal Syntax O(n) - Iterates over each element in the array to assign values to the object with the corresponding index as the key.

</p>
</details>

###### 34. How do you freeze an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Use Object.freeze to prevent property modifications:
```javascript
const person = { name: "Alice", age: 30 };
Object.freeze(person);

person.name = "Bob"; // This will not change the object's name property (silent failure)
console.log(person.name); // Output: still "Alice"

try {
  person.newProperty = "New"; // Throws an error in strict mode
} catch (error) {
  console.error(error.message); // "Cannot add property newProperty to object"
}
```

Time Complexity: Object.freeze O(1) - Sets a flag on the object to make it immutable, preventing modifications to existing properties and addition of new properties.

</p>
</details>

###### 35. How do you seal an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Use Object.seal to prevent adding new properties but allow modifying existing ones:
```javascript
const person = { name: "Alice", age: 30 };
Object.seal(person);

person.name = "Bob";  // This will change the object's name property
console.log(person.name); // Output: "Bob"

try {
  person.newProperty = "New"; // Throws an error in strict mode
} catch (error) {
  console.error(error.message); // "Cannot add property newProperty to object"
}
```

Time Complexity: Object.seal O(1) - Sets a flag on the object to make it non-extensible, preventing addition of new properties while allowing modifications to existing ones.

</p>
</details>

###### 36. How do you prevent extensions to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Use Object.freeze (also prevents modifications):
```javascript
const person = { name: "Alice", age: 30 };
Object.freeze(person);

person.newProperty = "New"; // This will not change the object (silent failure)
console.log(person.hasOwnProperty('newProperty')); // Output: false
```

Time Complexity: Object.freeze O(1) - Sets a flag on the object to make it immutable, preventing modifications to existing properties and addition of new properties.

</p>
</details>

###### 37. How do you check if an object is frozen, sealed, or extensible in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Use Object.isFrozen, Object.isSealed, and Object.isExtensible (modern):
```javascript
const person = { name: "Alice", age: 30 };
const frozenPerson = Object.freeze(person);

console.log(Object.isExtensible(person));   // Output: true (before freeze)
console.log(Object.isExtensible(frozenPerson)); // Output: false (after freeze)
console.log(Object.isSealed(person));      // Output: true (after freeze)
console.log(Object.isFrozen(person));       // Output: false (sealed, not frozen)
console.log(Object.isFrozen(frozenPerson));  // Output: true (frozen)
```

Time Complexity: Object.isFrozen, Object.isSealed, Object.isExtensible O(1) - These methods have a constant time complexity as they directly check the mutability state of an object based on internal flags set by methods like Object.freeze and Object.seal.

</p>
</details>

###### 38. How do you create a shallow copy of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using object literal syntax (spread syntax for modern JS):
```javascript
const person = { name: "Alice", age: 30 };
const shallowCopy = { ...person };

shallowCopy.name = "Bob";
console.log(person.name); // Output: still "Alice" (changes don't affect original)
```

Time Complexity: O(n) - Where n is the number of own enumerable properties in the person object. The spread syntax { ...person } creates a new object and copies all enumerable own properties of person into it, which requires iterating over all properties of person.

Using Object.assign with a new empty object:
```javascript
const person = { name: "Alice", age: 30 };
const shallowCopy = Object.assign({}, person);

shallowCopy.name = "Bob";
console.log(person.name); // Output: still "Alice" (changes don't affect original)
```

Time Complexity: O(n) - Where n is the number of own enumerable properties in the person object. Object.assign({}, person) creates a new empty object and then copies all enumerable own properties of person into it, which requires iterating over all properties of person.

</p>
</details>

###### 39. How do you create a deep copy of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using JSON.parse(JSON.stringify(obj)):
```javascript
const person = { name: "Alice", age: 30, address: { city: "New York" } };
const deepCopy = JSON.parse(JSON.stringify(person));

deepCopy.name = "Bob";
deepCopy.address.city = "London";
console.log(person.name); // Output: still "Alice" (original not affected)
console.log(person.address.city); // Output: still "New York" (deep copy for nested object)
```
Time complexity: O(n) - The time complexity of deep cloning an object using JSON.parse(JSON.stringify(obj)) is O(n), where n is the size of the object, including all nested properties. This method involves serializing the object to a JSON string and then parsing that string back into an object, both of which are linear operations.
##### Explanation:
- Serialization: JSON.stringify(person) converts the object into a JSON string, which is O(n) in time complexity.
- Deserialization: JSON.parse(stringifiedObject) converts the JSON string back into an object, also O(n) in time complexity.
- Overall Complexity: The combined process is linear with respect to the size of the object, making the overall time complexity O(n).

Recursive function (consider circular references):
```javascript
function deepCopy(obj) {
  if (obj === null || typeof obj !== "object") {
    return obj; // Handle primitives and null
  }

  if (obj instanceof Array) {
    return obj.map(deepCopy); // Deep copy for arrays
  } else {
    const copy = {};
    for (const key in obj) {
      copy[key] = deepCopy(obj[key]); // Recursive deep copy for properties
    }
    return copy;
  }
}

const person = { name: "Alice", age: 30, address: { city: "New York" } };
const deepCopyObj = deepCopy(person);

deepCopyObj.name = "Bob";
deepCopyObj.address.city = "London";
console.log(person.name); // Output: still "Alice" (original not affected)
console.log(person.address.city); // Output: still "New York" (deep copy for nested object)
```

##### Explanation
- Primitive and Null Check:
    - if (obj === null || typeof obj !== "object") { return obj; }
    - This line checks if obj is either null or a primitive type (such as a number, string, boolean, etc.). If so, it returns the value directly because primitives and null do not require deep copying.
- Array Handling:
    - if (obj instanceof Array) { return obj.map(deepCopy); }
    - This line checks if obj is an instance of Array. If it is, it uses the map method to apply the deepCopy function to each element of the array, ensuring that nested arrays are also deeply copied.
- Object Handling:
    - If the object is neither a primitive nor an array, it is assumed to be a plain object. A new empty object (copy) is created.
    - for (const key in obj) { copy[key] = deepCopy(obj[key]); }
    - This loop iterates over all properties of the object and recursively applies the deepCopy function to each property. This ensures that nested objects are also deeply copied.

Time Complexity: O(n) - Where n is the total number of primitive values and non-primitive values (objects and arrays) in the person object. The function iterates through all properties of the object recursively, creating copies as it goes.

Third-party libraries (Lodash, for example):
```javascript
// Assuming Lodash is installed
const _ = require('lodash');

const person = { name: "Alice", age: 30, address: { city: "New York" } };
const deepCopy = _.cloneDeep(person);

deepCopy.name = "Bob";
deepCopy.address.city = "London";
console.log(person.name); // Output: still "Alice" (original not affected)
console.log(person.address.city); // Output: still "New York" (deep copy for nested object)
```

Time Complexity: O(n) - The complexity of Lodash's cloneDeep function is similar to the recursive function, as it also iterates through all properties of the object recursively, creating copies as it goes.

##### Explanation:
The recursive function handles various data types (primitives, arrays, objects) and considers circular references.
Third-party libraries like Lodash often provide well-tested deep copy functionalities.

</p>
</details>

###### 40. How do you merge two or more objects into one object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using the spread syntax (modern JS):
```javascript
const obj1 = { name: "Alice", age: 30 };
const obj2 = { city: "New York", job: "Developer" };
const mergedObj = { ...obj1, ...obj2 };

console.log(mergedObj); // Output: { name: "Alice", age: 30, city: "New York", job: "Developer" }
```

Time Complexity: O(n + m), where n is the number of properties in obj1 and m is the number of properties in obj2. The spread syntax iterates over all properties of both objects to create a new object.

Using Object.assign (can overwrite properties):
```javascript
const obj1 = { name: "Alice", age: 30 };
const obj2 = { city: "New York", age: 28 }; // Overwrites age from obj1
const mergedObj = Object.assign({}, obj1, obj2);

console.log(mergedObj); // Output: { name: "Alice", age: 28, city: "New York" }
```

Time Complexity: O(n + m), where n is the number of properties in obj1 and m is the number of properties in obj2. Object.assign iterates over all properties of the source objects to copy them into the target object.

Using a loop for selective merging:
```javascript
const obj1 = { name: "Alice", age: 30 };
const obj2 = { city: "New York", age: 28 }; // Overwrites age from obj1
const mergedObj = Object.assign({}, obj1, obj2);

console.log(mergedObj); // Output: { name: "Alice", age: 28, city: "New York" }
```

Time Complexity: O(n + m), where n is the number of properties in obj1 and m is the number of properties in obj2. The loop or Object.assign function iterates over all properties of the source objects to copy them into the target object. Note: The code provided here for "loop for selective merging" is the same as Object.assign, thus it has the same complexity.

Summary:

- Using Spread Syntax: O(n + m)
- Using Object.assign: O(n + m)
- Using a Loop for Selective Merging: O(n + m)

</p>
</details>

###### 41. How do you destructure an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using object destructuring syntax:
```javascript
const person = { name: "Alice", age: 30, city: "New York" };

const { name, age } = person; // Destructure name and age properties
console.log(name); // Output: "Alice"
console.log(age);  // Output: 30

const { city: location } = person; // Destructure city and rename to location
console.log(location); // Output: "New York"
```
##### Explanation:
Destructuring allows extracting properties from objects into variables with concise syntax.
You can also rename properties during destructuring.

 ### Time complexity: 
 TC of using object destructuring syntax to extract properties from an object is O(1).

</p>
</details>

###### 42. How do you set default values for object properties in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using optional chaining (modern JS, handles potential undefined values):
```javascript
const person = { name: "Alice" }; // No age property

const age = person.age ?? 25; // Use default value of 25 if age is undefined
console.log(age); // Output: 25

const address = person.address?.city ?? "Unknown"; // Handle nested undefined values
console.log(address); // Output: "Unknown" (no address property)
```
Using a default value during object creation:
```javascript
const person = {
  name: "Alice",
  age: 30,
  city: "New York",
  job: "Developer" || "Unemployed" // Default value for job if not defined
};

console.log(person.job); // Output: "Developer"
```
##### Explanation:
- Optional Chaining (?.) provides a safe way to access nested properties. If a property is undefined or null, it returns undefined instead of throwing an error.
- Nullish Coalescing Operator (??) provides a way to set default values if a value is null or undefined.
- Logical OR (||) provides a way to set default values but can have unintended results if the value is falsy (e.g., 0, '', false).

### Time Complexity:
TC for both using optional chaining with nullish coalescing and assigning default values during object creation is O(1). These operations involve direct property access and basic conditional checks, both of which are done in constant time.

- Optional Chaining and Nullish Coalescing:
    - Time Complexity: O(1)
- Default Value During Object Creation:
    - Time Complexity: O(1)

</p>
</details>

###### 43. How do you get the number of properties in an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Use Object.keys(obj).length (modern):
```javascript
const person = { name: "Alice", age: 30, city: "New York" };
const numProperties = Object.keys(person).length;

console.log(numProperties); // Output: 3
```
##### Explanation:
- Object.keys(obj) returns an array of the object's own enumerable property names.
- We then use the length property to get the number of elements in the array.

### Time Complexity
Time complexity for Object.keys(obj).length is O(n) because it requires iterating over all the properties of the object to create the array of keys.

</p>
</details>

###### 44. How do you convert an object to a Map in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using a loop:
```javascript
const person = { name: "Alice", age: 30 };
const personMap = new Map();

for (const key in person) {
  personMap.set(key, person[key]);
}

console.log(personMap); // Output: Map { "name" => "Alice", "age" => 30 }
```
Using the spread syntax (modern JS):
```javascript
const person = { name: "Alice", age: 30 };
const personMap = new Map(Object.entries(person));

console.log(personMap); // Output: Map { "name" => "Alice", "age" => 30 }
```
##### Explanation:
- The loop iterates through the object's properties and adds them as key-value pairs to the Map.
- The spread syntax with Object.entries(person) creates an array of key-value pairs, which is then used to construct the Map.

### Time Complexity

#### Using a Loop:
- Time Complexity: O(n)
- Analysis:
    - Iterating over the properties of the person object with a for...in loop takes O(n) time, where n is the number of properties in the object.
    - For each property, the personMap.set(key, person[key]) operation takes O(1) time. However, this step is performed n times, resulting in an overall complexity of O(n).

#### Using the Spread Syntax:
- Time Complexity: O(n)
- Analysis:
    - Object.entries(person) iterates over the properties of the person object and creates an array of key-value pairs. This operation takes O(n) time.
    - Constructing a new Map with the array of key-value pairs, new Map(Object.entries(person)), also takes O(n) time since it iterates over the array to populate the Map.

</p>
</details>

###### 45. How do you convert a Map to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using a loop and object literal syntax:
```javascript
const personMap = new Map([["name", "Alice"], ["age", 30]]);
const personObj = {};

for (const [key, value] of personMap.entries()) {
  personObj[key] = value;
}

console.log(personObj); // Output: { name: "Alice", age: 30 }
```
##### Explanation:
- The loop iterates through the Map's entries (key-value pairs) and adds them as properties to the object.

### Time Complexity
Time complexity of converting a Map to an object using a loop and object literal syntax is O(n), where n is the number of entries in the Map.

</p>
</details>

###### 46. How do you convert an object to a Set in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using the spread syntax with new Set() (modern JS):
```javascript
const colors = { red: "red", green: "green", blue: "blue" };
const colorSet = new Set([...colors.values()]); // Use values to avoid duplicates

console.log(colorSet); // Output: Set { "red", "green", "blue" } (order may vary)
```
##### Explanation:
- The spread syntax (...) expands the object's values into an array.
- We then create a Set using new Set() and pass the array of values.
- Using colors.values() ensures we only consider values and avoid potential duplicate keys.

### Time Complexity
Time complexity of using the spread syntax with new Set() to convert the values of an object into a Set is O(n), where n is the number of properties (key-value pairs) in the object.

</p>
</details>

###### 47. How do you convert a Set to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

1. Using a loop and object literal syntax (create a basic object representation):
```javascript
const colorsSet = new Set(["red", "green", "blue"]);
const colorObj = {};

for (const color of colorsSet) {
  colorObj[color] = true; // Or any default value you want to associate with each set element
}

console.log(colorObj); // Output: { red: true, green: true, blue: true }
```
##### Explanation:
- We cannot directly convert a Set to an object with the same key-value structure because Sets don't have unique keys associated with each value.
- This approach creates an object where each set element becomes a property with a chosen default value (here, true).

### Time Complexity: O(n)
- Iterating over the Set takes O(n) time, where n is the number of elements in the Set.
- Adding each element to the object as a property is an O(1) operation, done n times.

2. Using Object.fromEntries with a map (modern JS, for key-value pairs with transformation):
```javascript
const colorsSet = new Set(["red", "green", "blue"]);
const colorMap = new Map([...colorsSet.entries()].map(entry => [entry[0], entry[0].toUpperCase()])); // Transform values to uppercase
const colorObj = Object.fromEntries(colorMap);

console.log(colorObj); // Output: { red: "RED", green: "GREEN", blue: "BLUE" }
```
##### Explanation:
- We cannot directly use Object.fromEntries with a Set as it requires key-value pairs.
- This approach first creates a Map from the Set entries.
- Then, it uses map to transform the values to uppercase before creating the object using Object.fromEntries.

### Time Complexity: O(n)
- colorsSet.entries(): Creating an iterator over the Set entries is O(1).
- Array.from(colorsSet.entries()): Converting the Set iterator to an array takes O(n).
- .map(entry => [entry[0], entry[0].toUpperCase()]): Iterating over the array and transforming the values takes O(n).
- new Map(...): Creating a Map from the transformed array takes O(n).
- Object.fromEntries(colorMap): Converting the Map to an object takes O(n).
</p>
</details>

###### 48. How do you convert an object to an array of key-value pairs in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using Object.entries (modern JS):
```javascript
const person = { name: "Alice", age: 30 };
const keyValuePairs = Object.entries(person);

console.log(keyValuePairs); // Output: [["name", "Alice"], ["age", 30]]
```
Using a loop (traditional approach):
```javascript
const person = { name: "Alice", age: 30 };
const keyValuePairs = [];

for (const key in person) {
  keyValuePairs.push([key, person[key]]);
}

console.log(keyValuePairs); // Output: [["name", "Alice"], ["age", 30]]
```
##### Explanation
- Object.entries returns an array of key-value pairs from an object.
- The loop iterates through the object's properties and adds them as arrays to the keyValuePairs array.

### Time Complexity: O(n)
- Iterating over the object's properties with for...in takes O(n).
- Each push operation inside the loop is O(1), but since it is executed n times, it results in O(n) total.

</p>
</details>

###### 49. How do you convert an array of key-value pairs to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using Object.fromEntries (modern JS):
```javascript
const keyValuePairs = [["name", "Alice"], ["age", 30]];
const personObj = Object.fromEntries(keyValuePairs);

console.log(personObj); // Output: { name: "Alice", age: 30 }
```
##### Explanation
Object.fromEntries directly constructs an object from an array of key-value pairs.

### Time Complexity: O(n)
The method Object.fromEntries iterates over the array of key-value pairs to construct the object. Here, n is the number of key-value pairs in the array.

</p>
</details>

###### 50. How do you convert an object to a query string in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using URLSearchParams (modern JS, recommended):
```javascript
const person = { name: "Alice", age: 30 };
const params = new URLSearchParams(person);
const queryString = params.toString();

console.log(queryString); // Output: name=Alice&age=30
```
##### Explanation:
URLSearchParams(person) creates a URLSearchParams object from the person object, which is used to construct a query string.

### Time Complexity: O(n)
The creation of a URLSearchParams object involves iterating over the properties of the person object. Here, n is the number of properties in the object.

Using a loop and manual encoding (older approach, consider URLSearchParams for security):
```javascript
const person = { name: "Alice", age: 30 };
let queryString = "";

for (const key in person) {
  if (queryString) {
    queryString += "&"; // Add separator for subsequent key-value pairs
  }
  queryString += `${encodeURIComponent(key)}=${encodeURIComponent(person[key])}`;
}

console.log(queryString); // Output: name=Alice&age=30
````
##### Explanation
- The loop iterates through the object's properties.
- Inside the loop:
  - If queryString is not empty (meaning it's not the first key-value pair), a & is appended as a separator.
  - encodeURIComponent is used to encode both the key and value to ensure they are URL-safe (avoid special characters breaking the query string).
  - The encoded key and value are joined with an = sign to form a key-value pair.
  - The entire key-value pair is then concatenated to the queryString variable.

### Time Complexity: O(n)
The loop iterates over each property of the object, and the operations inside the loop (appending strings, encoding) are constant time operations. Thus, the overall time complexity is O(n), where n is the number of properties in the object.

</p>
</details>

###### 51. How do you convert a query string to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using URLSearchParams (modern JS, recommended):
```javascript
const queryString = "name=Alice&age=30";
const params = new URLSearchParams(queryString);
const personObj = Object.fromEntries(params);

console.log(personObj); // Output: { name: "Alice", age: "30" } (values are strings)
```

### Time Complexity: O(n)
Creating a URLSearchParams object and converting it to an object both involve iterating over the key-value pairs in the queryString. Here, n is the number of key-value pairs in the queryString.

Using a loop and manual parsing (older approach, consider URLSearchParams for complex logic):
```javascript
const queryString = "name=Alice&age=30";
const keyValuePairs = [];

for (const param of queryString.split("&")) {
  const [key, value] = param.split("=");
  keyValuePairs.push([decodeURIComponent(key), decodeURIComponent(value)]);
}

const personObj = Object.fromEntries(keyValuePairs);

console.log(personObj); // Output: { name: "Alice", age: "30" } (values are strings)
```

### Time Complexity: O(n)
Both splitting the queryString and iterating over the key-value pairs have a linear time complexity proportional to the number of key-value pairs in the queryString, denoted by n.

##### Explanation:
- URLSearchParams provides a built-in way to parse a query string into key-value pairs.
    - We then use Object.fromEntries to convert those pairs into an object.
- The loop approach manually splits the query string by & and then each key-value pair by =.
    - Decoding is done using decodeURIComponent to handle any encoded characters.
    - Finally, the key-value pairs are converted to an object.

##### Important Note:
While the loop approach works for simple cases, URLSearchParams is generally preferred for robustness and handling complex query strings.

</p>
</details>

###### 52. How do you convert an object to a FormData object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using a loop (standard approach):
```javascript
const person = { name: "Alice", age: 30, photo: new Blob(["This is a photo"], { type: "image/jpeg" }) };
const formData = new FormData();

for (const key in person) {
  formData.append(key, person[key]);
}

console.log(formData); // FormData object with key-value pairs
```
##### Explanation:
- FormData objects are used for sending form data with file uploads in AJAX requests.
- The loop iterates through the object's properties.
- formData.append(key, value) adds each key-value pair to the FormData object.

Note that you can directly append Blobs or File objects for file uploads.

### Time Complexity: O(n)
- In this case, n represents the number of properties in the person object.
- The loop's time complexity is linear with respect to the number of properties, as it iterates through each property exactly once.

</p>
</details>

###### 53. How do you convert a FormData object to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Unfortunately, due to limitations in the FormData API, directly converting it to a standard JavaScript object with the same structure is not possible. FormData objects are designed specifically for sending form data and don't provide a straightforward way to access their key-value pairs as a regular object.

##### Alternatives:
- If you need the data in a standard object format, consider iterating through the FormData object using its methods and constructing a new object manually.
- Explore libraries like form-data (https://www.npmjs.com/package/form-data) that provide additional functionalities for working with FormData objects.

</p>
</details>

###### 54. How do you convert an object to a URLSearchParams object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using a loop:
```javascript
const person = { name: "Alice", age: 30 };
const params = new URLSearchParams();

for (const key in person) {
  params.append(key, person[key]);
}

console.log(params); // URLSearchParams object with key-value pairs
```
##### Explanation:
- URLSearchParams is designed to work with key-value pairs.
- The loop iterates through the object's properties.
- params.append(key, value) adds each key-value pair to the URLSearchParams object.

##### Additional Notes:
- Remember that URLSearchParams automatically handles URL encoding for you, making it a secure choice for building query strings.
- You can also use params.toString() to get the query string representation of the URLSearchParams object.

### Time Complexity: O(n)
- In this case, n represents the number of properties in the person object.
- The loop's time complexity is linear with respect to the number of properties, as it iterates through each property exactly once.

</p>
</details>

###### 55. How do you convert a URLSearchParams object to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using Object.fromEntries (modern JS):
```javascript
const params = new URLSearchParams("name=Alice&age=30");
const personObj = Object.fromEntries(params);

console.log(personObj); // Output: { name: "Alice", age: "30" } (values are strings)
```
##### Explanation:
- URLSearchParams provides an iterable of key-value pairs.
- Object.fromEntries directly constructs an object from such iterables.

### Time Complexity
The time complexity for Object.fromEntries when used with URLSearchParams is O(n), where n is the number of key-value pairs in the URLSearchParams object.

</p>
</details>

###### 56. How do you convert an object to a Blob object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using a string and Blob constructor:
```javascript
const person = { name: "Alice", age: 30 };
const jsonString = JSON.stringify(person); // Convert to JSON string
const blob = new Blob([jsonString], { type: "application/json" });

console.log(blob); // Blob object representing the JSON string
```

### Time Complexity: O(n)
##### Explanation: 
The JSON.stringify operation has a time complexity of O(n), where n is the number of characters in the resulting JSON string. The Blob constructor also operates in O(n) time as it processes each character in the input string.

Using a library like FileSaver.js (for saving or downloading Blobs):
```javascript
// Assuming FileSaver.js is installed (ensure trusted source)
const person = { name: "Alice", age: 30 };
const jsonString = JSON.stringify(person);
const blob = new Blob([jsonString], { type: "application/json" });

FileSaver.saveAs(blob, "person.json"); // Save the Blob as a file (requires user interaction)
```

### Time Complexity: O(n)
##### Explanation: 
This approach involves the same steps as the first scenario for creating the JSON string and Blob, each with O(n) complexity. The FileSaver.saveAs method adds additional operations, but these are typically constant time, making the overall complexity still O(n).


##### Explanation:
- Blobs are binary data containers.
- The first approach creates a JSON string from the object and then uses the Blob constructor to create a Blob with the specified type (e.g., JSON).
- FileSaver.js is a popular library for saving or downloading Blobs as files. It's important to download libraries from trusted sources.

</p>
</details>

###### 57. How do you convert a Blob object to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using FileReader (asynchronous processing):
```javascript
const blob = new Blob(["This is some text data"], { type: "text/plain" });
const reader = new FileReader();

reader.onload = function(e) {
  const content = e.target.result;  // Content as string
  const obj = JSON.parse(content); // Parse if content is JSON

  console.log(obj); // Output: { text: "This is some text data" } (example for JSON content)
};

reader.readAsText(blob);  // Read the Blob content as text
```
##### Explanation:
- Blobs store raw data, not JavaScript objects directly.
- FileReader allows asynchronous reading of Blob content.
- We read the Blob as text (adjust the type based on the Blob's actual content) and then parse it as JSON if the content format is appropriate (e.g., JSON string).

### Time Complexity:
- Blob creation: The creation of a Blob is O(n), where n is the size of the data being stored in the Blob.
- FileReader.readAsText(blob): The read operation's complexity is O(n), where n is the size of the Blob content being read.
- Parsing JSON: The JSON.parse(content) operation is O(m), where m is the length of the string being parsed.
### Overall Time Complexity:
- Time Complexity: O(n + m)
- Explanation: The overall complexity is the sum of the time to read the Blob content and parse it as JSON. If the Blob content is directly parsed as JSON, n and m represent the same data, resulting in an effective complexity of O(n).

</p>
</details>

###### 58. How do you convert an object to a TypedArray object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using a typed array constructor (specify data type):
```javascript
const numbers = { data: [1, 2, 3, 4, 5] };
const typedArray = new Uint8Array(numbers.data); // Uint8Array for 8-bit unsigned integers

console.log(typedArray); // TypedArray object with the data
```
##### Explanation:
- TypedArrays are typed arrays of fixed-length, primitive data elements.
- You need to choose the appropriate TypedArray constructor based on the data type you want to store (e.g., Uint8Array, Float32Array).
- In this example, we create a Uint8Array from the object's data property (assuming it's an array of numbers).
- 
##### Important Note:
-TypedArrays are not directly interchangeable with objects. They offer efficient storage and operations for specific data types.
- Converting an object to a TypedArray might require restructuring the data depending on the object's structure and the desired TypedArray type.

### Time Complexity: O(n) 
The overall complexity is linear with respect to the number of elements in the input array numbers.data. The TypedArray constructor iterates through the input array to initialize the TypedArray.

</p>
</details>

###### 59. How do you convert a TypedArray object to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using a loop and a new object (create a basic object representation):
```javascript
const typedArray = new Uint8Array([1, 2, 3, 4, 5]);
const obj = {};

for (let i = 0; i < typedArray.length; i++) {
  obj[i] = typedArray[i]; // Assign each element to a property with its index as key
}

console.log(obj); // Output: { 0: 1, 1: 2, 2: 3, 3: 4, 4: 5 }
```
##### Explanation:
- TypedArrays don't have named properties like objects.
- This approach creates a new object with each TypedArray element assigned to a property using its index as the key.
##### Important Note:
This creates a basic object representation. The structure might not be ideal for all use cases, depending on your desired object format.

### Time Complexity O(n)
Loop Iteration: Iterating through the typedArray has a time complexity of O(n), where n is the length of the typedArray.
Object Assignment: Each assignment obj[i] = typedArray[i] is an O(1) operation.

</p>
</details>

###### 60. How do you convert an object to an ArrayBuffer object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using TypedArray.buffer (if the object holds a TypedArray):
```javascript
const numbers = { data: new Uint8Array([1, 2, 3]) };
const arrayBuffer = numbers.data.buffer; // Access the underlying ArrayBuffer

console.log(arrayBuffer); // ArrayBuffer object representing the data
```

### Time Complexity: O(1) 
Accessing the buffer property of a TypedArray is a constant time operation.

Using TextEncoder for string data and ArrayBuffer.from (modern JS):
```javascript
const person = { name: "Alice" };
const encoder = new TextEncoder();
const encodedString = encoder.encode(JSON.stringify(person)); // String encoded as Uint8Array
const arrayBuffer = ArrayBuffer.from(encodedString); // Create ArrayBuffer from the Uint8Array

console.log(arrayBuffer); // ArrayBuffer object representing the encoded JSON string
```

### Time Complexity: O(n)
Encoding the string using TextEncoder and creating an ArrayBuffer from the Uint8Array both involve iterating over the input data, making the operation linear with respect to the length of the string.

##### Explanation:
- ArrayBuffers are used as the underlying storage for TypedArrays.
- If the object holds a TypedArray, you can access its underlying ArrayBuffer using TypedArray.buffer.
- For other data types (like strings), you can convert them to Uint8Array using TextEncoder and then create an ArrayBuffer from the resulting Uint8Array.
</p>
</details>

###### 61. How do you convert an ArrayBuffer object to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using DataView to interpret the data (consider specific data format):
```javascript
const arrayBuffer = new ArrayBuffer(8);
const dataView = new DataView(arrayBuffer);
dataView.setInt32(0, 12345678, true); // Write a 32-bit integer at byte offset 0 (big-endian)

// Now, interpret the data based on its format (example assumes 32-bit integer)
const value = dataView.getInt32(0, true); // Read the integer

const obj = { value }; // Create an object with the interpreted value

console.log(obj); // Output: { value: 12345678 }
```
##### Explanation:
- ArrayBuffers are raw binary data. You need to interpret the data based on its format.
- DataView provides methods for reading and writing different data types at specific byte offsets within the ArrayBuffer.
##### Important Note:
- This is a simplified example assuming a specific data format (32-bit integer).
- Interpreting ArrayBuffers effectively requires understanding the data format and using appropriate DataView methods for reading/writing.

### Time Complexity:
- DataView Construction: O(1)
- Setting a value in DataView: O(1)
- Getting a value from DataView: O(1)
### Overall Time Complexity O(1)
Each operation (constructing the DataView, setting a value, and getting a value) is performed in constant time, O(1).

</p>
</details>

###### 62. How do you convert an object to a DataView object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

##### Important Note:
DataViews operate on existing ArrayBuffers. You cannot directly convert an object to a DataView.

##### Solutions:
- Create an ArrayBuffer first (based on your desired data format and size) and then use new DataView(arrayBuffer) to create a DataView for that ArrayBuffer.
- If your object already holds data in a format compatible with an ArrayBuffer (e.g., a TypedArray), you can access its underlying ArrayBuffer using TypedArray.buffer and then create a DataView for that ArrayBuffer.

##### Remember: When converting between these data structures, consider the intended use case and the desired data format. Choose the appropriate methods and libraries based on your specific needs.

Here are some additional points to keep in mind:
- **Error handling:** When working with TypedArrays, ArrayBuffers, and DataViews, it's important to handle potential errors like out-of-bounds access or invalid data types. Consider using try-catch blocks or appropriate library functions that provide error handling mechanisms.
- **Performance:** TypedArrays and ArrayBuffers offer efficient data storage and manipulation. However, frequent conversions between these structures and objects might impact performance. If performance is critical, consider optimizing your data access patterns and minimizing unnecessary conversions.
- **Libraries:** Explore libraries like buffer (https://nodejs.org/api/buffer.html) in Node.js or community-maintained libraries that provide additional functionalities for working with these data structures.

</p>
</details>

###### 63. How do you convert a DataView object to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

##### Important Note:
- DataViews operate on existing ArrayBuffers. You cannot directly convert a DataView to a standard JavaScript object with the same structure.
Solutions (2 - not directly but achieve similar results):

1. Interpret the data based on format and create a new object:
```javascript
const arrayBuffer = new ArrayBuffer(8);
const dataView = new DataView(arrayBuffer);
dataView.setInt32(0, 12345678, true); // Write a 32-bit integer at byte offset 0 (big-endian)

// Now, interpret the data based on its format (example assumes 32-bit integer)
const value = dataView.getInt32(0, true); // Read the integer

const obj = { value }; // Create an object with the interpreted value

console.log(obj); // Output: { value: 12345678 }
```

### Time Complexity: O(1)

##### Explanation:
- DataViews provide methods for reading/writing data based on a specific format.
- This approach interprets the data in the DataView (assuming a known format) and creates a new object with the extracted value(s).

- 2. Use a loop and helper functions to create an object representation (complex formats):
```javascript
// Assuming helper functions to interpret specific data types within the DataView
const arrayBuffer = new ArrayBuffer(16); // Example with more complex data
const dataView = new DataView(arrayBuffer);
// ... write data to the DataView using appropriate methods ...

const obj = {
  // Define properties based on data format
  value1: interpretInt32(dataView, 0),
  value2: interpretFloat64(dataView, 4),
  // ... add more properties based on data format and helper functions
};

console.log(obj); // Output: { value1: ..., value2: ..., ... } (values based on data format)
```

### Time Complexity: O(n), where n is the number of properties in the object.

##### Explanation:
- For complex data formats in the DataView, you might need to write custom helper functions to interpret different data types (e.g., interpretInt32, interpretFloat64).
- These functions would read the relevant sections of the DataView and return the extracted values.
- The main object then uses these extracted values to construct its properties.
</p>
</details>

###### 64. How do you convert an object to a JSONP object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>
JSONP itself isn't a JavaScript object but a technique for cross-origin requests. The response from a JSONP request is JSON data wrapped in a function call. Here's how to extract the actual object from a JSONP response in JavaScript:

Solutions (2 - avoiding eval for security):
1. Dynamic Function Creation:
```jJavaScript
const url = "https://api.example.com/data?callback=myCallback";
const data = { name: "Alice", age: 30 };

function createCallback(callbackName) {
  return new Function("data", `<span class="math-inline">\{callbackName\}\(</span>{JSON.stringify(data)})`);  // More secure than eval
}

fetch(url + "&" + new URLSearchParams(data))
  .then(response => response.text())
  .then(text => {
    const callbackFunction = createCallback(text.split("=")[0]); // Extract callback name
    const jsonData = JSON.parse(text.substring(text.indexOf("(") + 1, text.lastIndexOf(")"))); // Extract data from JSONP call
    callbackFunction(jsonData); // Execute the callback with extracted data (optional)
    console.log(jsonData); // Access the extracted object
  })
  .catch(error => console.error(error));
```

### Time Complexity: O(n), where n is the length of the response text.

##### Explanation:
- This approach fetches the JSONP response using fetch.
- It then extracts the callback name from the response text.
- A dynamic function is created using new Function based on the callback name.
- The data portion is extracted by slicing the response text between the opening parenthesis ( and the closing parenthesis ).
- JSON.parse is used to convert the extracted data string into a JavaScript object.
- The extracted object (jsonData) is now accessible and can be used further in your code.

2. Libraries for JSONP Handling:
- Explore libraries like jsonp (https://www.npmjs.com/package/jsonp) that offer safer and more robust ways to handle JSONP requests.
- These libraries typically manage the following aspects:
  - Creating a script element dynamically to fetch the JSONP data.
  - Handling the callback function creation and execution.
  - Extracting the data from the response and providing a Promise-based API for handling success and errors.
- Using libraries simplifies the process and reduces the risk of security vulnerabilities associated with eval.

### Time Complexity: O(n), where n is the length of the response text.

</p>
</details>

###### 65. How do you convert an object to a Promise object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using the Promise constructor (resolve or reject based on logic):
```javascript
function fetchData(url) {
  return new Promise((resolve, reject) => {
    // Simulate asynchronous operation (e.g., fetch data)
    setTimeout(() => {
      const data = { name: "Alice", age: 30 };
      resolve(data); // Resolve the Promise with the data
    }, 1000);
  });
}

fetchData("https://api.example.com/data")
  .then(data => console.log(data)) // Handle successful data retrieval
  .catch(error => console.error(error)); // Handle errors during the promise execution
```
##### Explanation:
- The Promise constructor takes an executor function with resolve and reject callbacks.
- Inside the executor, you perform the asynchronous operation (e.g., simulated here).
- Upon successful completion, call resolve with the data.
- In case of errors, call reject with the error object.
##### Important Note:
Converting a simple object to a Promise might not be necessary in all cases. Promises are typically used for handling asynchronous operations and managing their results.

### Time Complexity: O(1)
The complexity is O(1) because the operations inside the Promise constructor and the simulated asynchronous operation have constant time complexity. The setTimeout function's delay does not affect the computational complexity.

</p>
</details>

###### 66. How do you convert a Promise object to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

##### Important Note:
- Promises are designed to represent the eventual completion (or failure) of an asynchronous operation. They don't directly hold an object value initially.

Solutions (2 - alternative approaches):

Using then and destructuring (access resolved value):
```javascript
async function fetchData() {
  const promise = new Promise((resolve) => resolve({ name: "Alice", age: 30 }));
  const data = await promise; // Wait for the Promise to resolve
  console.log(data); // Output: { name: "Alice", age: 30 }
}

fetchData();
```

### Time Complexity O(1)
The time complexity is O(1) because the await keyword in the async function pauses the execution until the Promise is resolved, but it does not impact the overall time complexity of the function. The Promise itself resolves in constant time.

##### Explanation:
- The await keyword can only be used within async functions.
- It pauses the execution of the async function until the Promise resolves and then assigns the resolved value to the variable.
</p>
</details>

###### 67. How do you convert an object to a Proxy object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using the Proxy constructor with a handler (control object behavior):
```javascript
const person = { name: "Alice", age: 30 };

const handler = {
  get(target, propKey) {
    if (propKey in target) {
      return target[propKey];
    } else {
      console.warn(`Property "${propKey}" does not exist on the object`);
      return null;
    }
  },
  set(target, propKey, value) {
    target[propKey] = value;
    console.log(`Property "<span class="math-inline">\{propKey\}" set to "</span>{value}"`);
    return true;
  }
};

const personProxy = new Proxy(person, handler);

console.log(personProxy.name); // Output: "Alice"
personProxy.age = 31; // Output: "Property "age" set to "31""

console.log(personProxy.job); // Output: Property "job" does not exist on the object (handled in handler)
```
##### Explanation:
- The Proxy constructor creates a proxy object that intercepts operations on the target object (here, person).
- The handler object defines how these operations are handled.
- In this example, the get trap handles property access, and the set trap handles property assignment. You can define other traps for operations like deletion (deleteProperty), function calls (apply), etc.

### Time Complexity O(1)
The time complexity for accessing or setting a property through a Proxy is O(1) because the operation's performance does not depend on the size of the object or the number of properties. The Proxy intercepts the operation and performs the necessary actions directly.

</p>
</details>

###### 68. How do you convert a Proxy object to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Directly converting a Proxy object back to the original object it wraps isn't always possible in JavaScript. Proxy objects provide a layer of control over object behavior, and the handler can restrict access to the underlying object for security reasons.

However, here are some approaches you can consider depending on your specific needs:

1. Accessing Properties Through the Proxy:
```javascript
const person = { name: "Alice", age: 30 };
const personProxy = new Proxy(person, {}); // Empty handler for basic access

console.log(personProxy.name); // Output: "Alice" (access through the Proxy)
```
##### Explanation:
- Even though you can't directly convert the Proxy back, you can continue to access the underlying object's properties through the Proxy object itself. This approach works if you only need to read the data.

2. Checking Handler Permissions (if applicable):
```javascript
const person = { name: "Alice", age: 30 };
const handler = {
  get(target, propKey) {
    return Reflect.get(target, propKey); // Use Reflect API to access original property
  }
};

const personProxy = new Proxy(person, handler);

if (Reflect.getPrototypeOf(personProxy) === person) {
  console.log("Original object accessible through Proxy");
} else {
  console.log("Original object access restricted by handler");
}
```
##### Explanation:
- Some handlers might allow retrieving the target object using the Reflect API's Reflect.getPrototypeOf method. This approach depends on the specific handler implementation. If the handler doesn't allow access, this won't work.

3. Alternative Approaches:
- If you need a copy of the original object's data, consider creating a new object with the desired properties based on the information available through the Proxy object (assuming read access is allowed).
- Explore libraries that might offer functionalities to work with Proxy objects and potentially extract the underlying data under specific conditions.

##### Important Considerations:
- Converting a Proxy object back to the original object can be limited by the handler's design.
- If you need full control over modifying and accessing the data, consider avoiding Proxy objects and directly using a regular object.
- Proxy objects are valuable for controlling object behavior and intercepting operations, but they might not be suitable for all use cases where direct object manipulation is required.

### Time Complexity: N/A (Not Applicable)

</p>
</details>

###### 69. How do you convert an object to a RegExp object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using a regular expression string:
```javascript
const patternString = "color=([a-z]+)";
const colorRegExp = new RegExp(patternString);

const text = "My favorite color is blue";
const match = colorRegExp.exec(text);

if (match) {
  console.log(`Matched color: ${match[1]}`); // Output: Matched color: blue
} else {
  console.log("No color match found");
}
```
##### Explanation:
- You can create a RegExp object directly from a string containing the regular expression pattern.
- The pattern string defines the search criteria using special characters and metacharacters.
- The exec method of the RegExp object is used to search for matches in a given string.

### Time Complexity: O(n)
- Creating a RegExp object from a string involves parsing the string to build the regular expression pattern.
- The complexity of this process is linear relative to the length of the pattern string, as each character in the string needs to be processed to construct the regular expression.

Using flags (optional):
```javascript
const patternString = /color=([a-z]+)/i; // Case-insensitive search with flag 'i'
const colorRegExp = new RegExp(patternString);

const text = "My FAVORITE Color is BLUE";
const match = colorRegExp.exec(text);

if (match) {
  console.log(`Matched color (case-insensitive): ${match[1]}`); // Output: Matched color (case-insensitive): BLUE
} else {
  console.log("No color match found");
}
```
##### Explanation:
- You can add flags (like i for case-insensitive search) to the end of the pattern string.
- These flags modify the behavior of the regular expression search.

##### Important Note:
- Converting a simple object to a RegExp object might not be necessary in all cases. Regular expressions are specifically used for pattern matching in strings.

### Time Complexity: O(n)
- Adding flags to a regular expression string does not significantly affect the time complexity.
- The complexity remains linear relative to the length of the pattern string.

</p>
</details>

###### 70. How do you convert a RegExp object to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

##### Important Note:
Directly converting a RegExp object to a standard JavaScript object with the same structure isn't necessary in most cases. RegExp objects are designed for pattern matching in strings.

Access properties and methods of the RegExp object:
```javascript
const patternString = "color=([a-z]+)";
const colorRegExp = new RegExp(patternString);

console.log(colorRegExp.source); // Output: "color=([a-z]+)" (access the pattern string)
console.log(colorRegExp.flags); // Output: "" (empty string for flags in this case)
console.log(colorRegExp.test("My favorite color is blue")); // Output: true (test for match)
```
##### Explanation:
- RegExp objects provide properties like source (the pattern string) and flags (modifiers like case-insensitive search).
- You can use methods like test to check for matches in strings and exec to retrieve detailed information about the match.

### Time Complexity: O(1)
- Accessing properties and methods of a RegExp object, such as source, flags, test, exec, etc., has a constant time complexity.
- These operations directly access the internal properties of the RegExp object without iterating over any data structure.
</p>
</details>

###### 71. How do you convert an object to a Symbol object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using Symbol function (create unique symbols):
```javascript
const sym1 = Symbol("description");
const sym2 = Symbol("description"); // Creates a new symbol even with the same description

console.log(sym1 === sym2); // Output: false (Symbols are unique)
console.log(Symbol.keyFor(sym1)); // Output: undefined (Symbols don't have a reverse lookup for descriptions)
```
##### Explanation:
- The Symbol function creates unique and immutable Symbol objects.
- You can optionally provide a description string (not used for uniqueness).
- Symbols are primarily used as property keys to ensure unique object properties that won't conflict with other property names.

### Time Complexity: O(1)
- Creating a Symbol using the Symbol function has a constant time complexity.
- The creation of a Symbol is not dependent on the size of any input, as it always creates a new unique Symbol instance.

</p>
</details>

###### 72. How do you convert a Symbol object to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

##### Important Note:
Directly converting a Symbol object to a standard JavaScript object isn't possible. Symbols are primitive values and don't have properties like objects.


Use the Symbol object directly (access its description if available):
```javascript
const sym = Symbol("description");

if (Symbol.keyFor) { // Check for existence of the reverse lookup method (not guaranteed)
  const description = Symbol.keyFor(sym);
  console.log(description); // Output: "description" (if supported)
} else {
  console.log("Symbol description not directly accessible");
}
```
##### Explanation:
- While you cannot convert a Symbol to an object, you can use the Symbol object directly for its unique identity and optionally access its description if the Symbol.keyFor method is supported (which might not be available in all environments).

### Time Complexity: O(1)
- Creating a Symbol object and accessing its description (if available) is a constant-time operation.
- The complexity does not depend on the size of the description or any other factor.

</p>
</details>

###### 73. How do you convert an object to a WeakMap object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using the WeakMap constructor with key-value pairs:
```javascript
const person = { name: "Alice", age: 30 };
const details = { city: "New York" };

const personMap = new WeakMap();
personMap.set(person, details); // Use the object itself as the key (weak reference)

console.log(personMap.get(person)); // Output: { city: "New York" }

// Person object can be garbage collected without affecting the WeakMap
person = null;
```
##### Explanation:
- The WeakMap constructor creates a collection that holds key-value pairs where keys are weakly referenced.
- This means the garbage collector can reclaim the memory of the key object if there are no other references to it.
- In this example, the person object is used as the key, and the details object is the value.
- When the person object is no longer referenced elsewhere, it can be garbage collected even though it's a key in the WeakMap. The WeakMap itself remains functional as long as it's referenced.

##### Important Note:
WeakMaps are useful for scenarios where you want to associate data with objects without preventing those objects from being garbage collected. Consider using Map objects if you need strong references to both keys and values.

### Time Complexity: O(1) for set and get operations
- The time complexity of set and get operations in a WeakMap is considered to be O(1) on average.
- This is because the underlying implementation typically uses hashing to store and retrieve key-value pairs, leading to constant-time complexity for these operations in most cases.

</p>
</details>

###### 74. How do you convert a WeakMap object to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Important Note:
Directly converting a WeakMap to a standard JavaScript object isn't possible. WeakMaps are designed to hold key-value pairs with weak references to keys, and these weak references cannot be easily converted to a standard object structure.


Iterate and create a new object (limited functionality):
```javascript
const person = { name: "Alice", age: 30 };
const details = { city: "New York" };

const weakMap = new WeakMap();
weakMap.set(person, details);

const obj = {}; // Create a new object to hold extracted data
for (const [key, value] of weakMap.entries()) {
  // Key will be inaccessible due to weak reference nature
  obj[ /* key reference (not possible) */ ] = value; // Add value to the new object
}

console.log(obj); // Output: {} (keys cannot be retrieved)
```
##### Explanation:
- Due to weak references in WeakMaps, iterating over entries doesn't provide access to the original keys.
- This approach creates a new object and adds the values from the WeakMap, but the keys are lost because they cannot be strongly referenced.

### Time Complexity: O(n)
Iterating over entries in a WeakMap involves iterating over all key-value pairs in the WeakMap, which has a linear time complexity relative to the number of entries in the WeakMap.

Convert values to a suitable structure if possible:
```javascript
const person = { name: "Alice", age: 30 };
const details = { city: "New York" };

const weakMap = new WeakMap();
weakMap.set(person, details);

// Assuming values are simple objects or primitives
const valuesArray = Array.from(weakMap.values()); // Extract values as an array

console.log(valuesArray); // Output: [{ city: "New York" }] (if values are suitable for conversion)
```
##### Explanation:
- If the values in the WeakMap are simple objects or primitives, you might be able to convert them to a suitable structure like an array.
This approach depends on the type of data stored in the WeakMap.

### Time Complexity: O(n)
Converting the values of a WeakMap to a suitable structure, like an array, involves iterating over all values in the WeakMap, which has a linear time complexity relative to the number of entries in the WeakMap.

</p>
</details>

###### 75. How do you convert an object to a WeakSet object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using the WeakSet constructor with iterable of objects:
```javascript
const set1 = new Set(["apple", "banana", "orange"]); // Regular Set (strong references)
const weakSet = new WeakSet(set1); // Convert elements to weakly referenced objects

console.log(weakSet.has(set1)); // Output: false (original set object not in WeakSet)

const apple = { name: "apple" }; // Create a new object
weakSet.add(apple);

console.log(weakSet.has(apple)); // Output: true (new object with weak reference added)
```
##### Explanation:
- The WeakSet constructor creates a collection of weakly referenced objects.
- You can pass an iterable (like an array or another Set) containing the objects to the constructor.
- However, it's important to note that the original objects in the iterable are not stored in the WeakSet. Weak references are created for the objects themselves.

### Time Complexity
- Creation: O(n), where n is the number of elements in the iterable passed to the WeakSet constructor.
- Adding: O(1)
- Checking Membership: O(1)

##### Explanation:
- Creating a WeakSet from an iterable involves iterating over the elements in the iterable, resulting in a linear time complexity relative to the number of elements.
- Adding an element to a WeakSet and checking for membership have constant time complexities, as they involve direct operations on the underlying data structure.

</p>
</details>

###### 76. How do you convert a WeakSet object to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

##### Important Note:
- Directly converting a WeakSet to a standard JavaScript object isn't possible. Similar to WeakMaps, WeakSets hold weak references to objects, and these references cannot be easily converted to a standard object structure.

Iterate and potentially convert values (limited functionality):
```javascript
const apple = { name: "apple" };
const banana = { name: "banana" };

const weakSet = new WeakSet([apple, banana]);

const obj = []; // Create an array to hold converted values (if possible)
for (const value of weakSet.values()) {
  // `value` will be the weakly referenced object
  obj.push( /* convert value if possible */ value); // Limited conversion based on value type
}

console.log(obj); // Output: [ /* Converted values or original objects */ ] (conversion depends on value type)
```
##### Explanation:
The code attempts to iterate over a WeakSet and convert its values into a different format, storing them in an array. However, due to the weakly referenced nature of the objects in a WeakSet, direct conversion is limited. The success of conversion depends on the structure and content of the objects. The resulting array (obj) will contain the converted values if successful, or the original objects if conversion fails.

### Time Complexity:
- Iteration: O(n), where n is the number of elements in the WeakSet.
- Explanation:
    - Iterating over a WeakSet involves visiting each element once, resulting in a time complexity linear to the number of elements in the WeakSet.

</p>
</details>

</div>
</details>
