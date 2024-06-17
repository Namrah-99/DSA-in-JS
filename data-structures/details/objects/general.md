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
function isEqual(obj1, obj2) {
    // Implementation details
}
```

</p>
</details>

###### 10. How do you convert an object to a JSON string in JavaScript?
<details><summary><b>Solution</b></summary>
<p>
  
```javascript
const jsonString = JSON.stringify(obj);
```

</p>
</details>

###### 11. How do you convert a JSON string to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

```javascript
const obj = JSON.parse(jsonString);
```

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

</p>
</details>

###### 14. How do you call a method of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>
  
```javascript
obj.methodName();
```

</p>
</details>

###### 15. How do you define a getter and setter for a property in JavaScript?
<details><summary><b>Solution</b></summary>
<p>
  
Object.defineProperty:
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
Accessors (modern syntax):
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
Prototype-based getters and setters (advanced):
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

</p>
</details>

###### 16. How do you define a getter and setter for a property in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

- **Prototype:** An object that serves as a blueprint for creating new objects. It holds properties and methods that can be inherited by objects created from that prototype.
- **Prototype Chain:** The mechanism in JavaScript by which an object can inherit properties and methods from its prototype, and then its prototype's prototype, and so on, until a null prototype is reached.

</p>
</details>

###### 17. How do you create an object with a specific prototype in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

  
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

</p>
</details>

###### 18. How do you check the prototype of an object in JavaScript?
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

</p>
</details>

###### 19. How do you set the prototype of an object in JavaScript?
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

</p>
</details>

###### 20. How do you create an object without a prototype in JavaScript?
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

</p>
</details>

###### 21. How do you check if an object is an instance of a specific class in JavaScript?
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

</p>
</details>

###### 22. How do you define a class in JavaScript?
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

</p>
</details>

###### 23. How do you create an instance of a class in JavaScript?
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

</p>
</details>

###### 24. How do you define static methods in a class in JavaScript?
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

</p>
</details>

###### 25. How do you define private properties and methods in a class in JavaScript?
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

</p>
</details>

###### 26. How do you define inheritance in JavaScript?
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

</p>
</details>

###### 27. How do you call a superclass method from a subclass method in JavaScript?
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

</p>
</details>

###### 28. How do you override a method in a subclass in JavaScript?
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

</p>
</details>

###### 29. How do you check if an object is iterable in JavaScript?
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

</p>
</details>

###### 30. How do you iterate over the keys of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using the for...in loop:
```javascript
const person = { name: "Alice", age: 30 };

for (const key in person) {
  console.log(key); // Output: name, age
}
```
Using Object.keys (modern, doesn't iterate over inherited properties):
```javascript
const person = { name: "Alice", age: 30 };

const keys = Object.keys(person);
for (const key of keys) {
  console.log(key); // Output: name, age
}
```

</p>
</details>

###### 31. How do you iterate over the values of an object in JavaScript?
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
Using Object.values (modern, doesn't iterate over inherited properties):
```javascript
const person = { name: "Alice", age: 30 };

const values = Object.values(person);
for (const value of values) {
  console.log(value); // Output: Alice, 30
}
```

</p>
</details>

###### 32. How do you iterate over the entries of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using Object.entries (modern):
```javascript
const person = { name: "Alice", age: 30 };

for (const [key, value] of Object.entries(person)) {
  console.log(key, value); // Output: name Alice, age 30
}
```

</p>
</details>

###### 33. How do you convert an object to an array in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using Object.values for values (modern):
```javascript
const person = { name: "Alice", age: 30 };
const valuesArray = Object.values(person);
console.log(valuesArray); // Output: ["Alice", 30]
```
Using Object.keys and mapping for key-value pairs (modern):
```javascript
const person = { name: "Alice", age: 30 };
const entriesArray = Object.keys(person).map(key => [key, person[key]]);
console.log(entriesArray); // Output: [["name", "Alice"], ["age", 30]]
```
Using a loop with spread syntax (older approach):
```javascript
const person = { name: "Alice", age: 30 };
const valuesArray = [];
for (const key in person) {
  valuesArray.push(person[key]);
}
console.log(valuesArray); // Output: ["Alice", 30]
```

</p>
</details>

###### 34. How do you convert an array to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using Object.fromEntries (modern):
```javascript
const names = ["Alice", "Bob", "Charlie"];
const nameObject = Object.fromEntries(names.map((name, index) => [index, name]));
console.log(nameObject); // Output: {0: "Alice", 1: "Bob", 2: "Charlie"}
```
Using a loop with object literal syntax:
```javascript
const names = ["Alice", "Bob", "Charlie"];
const nameObject = {};
for (let i = 0; i < names.length; i++) {
  nameObject[i] = names[i];
}
console.log(nameObject); // Output: {0: "Alice", 1: "Bob", 2: "Charlie"}
```

</p>
</details>

###### 35. How do you freeze an object in JavaScript?
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

</p>
</details>

###### 36. How do you seal an object in JavaScript?
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

</p>
</details>

###### 37. How do you prevent extensions to an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Use Object.freeze (also prevents modifications):
```javascript
const person = { name: "Alice", age: 30 };
Object.freeze(person);

person.newProperty = "New"; // This will not change the object (silent failure)
console.log(person.hasOwnProperty('newProperty')); // Output: false
```

</p>
</details>

###### 38. How do you check if an object is frozen, sealed, or extensible in JavaScript?
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

</p>
</details>

###### 39. How do you create a shallow copy of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using object literal syntax (spread syntax for modern JS):
```javascript
const person = { name: "Alice", age: 30 };
const shallowCopy = { ...person };

shallowCopy.name = "Bob";
console.log(person.name); // Output: also "Bob" (changes are reflected in original object)
```
Using Object.assign with a new empty object:
```javascript
const person = { name: "Alice", age: 30 };
const shallowCopy = Object.assign({}, person);

shallowCopy.name = "Bob";
console.log(person.name); // Output: still "Alice" (changes don't affect original)
```

</p>
</details>

###### 40. How do you create a deep copy of an object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

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
const deepCopy = deepCopy(person);

deepCopy.name = "Bob";
deepCopy.address.city = "London";
console.log(person.name); // Output: still "Alice" (original not affected)
console.log(person.address.city); // Output: still "New York" (deep copy for nested object)
```
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
##### Explanation:
The recursive function handles various data types (primitives, arrays, objects) and considers circular references.
Third-party libraries like Lodash often provide well-tested deep copy functionalities.

</p>
</details>

###### 41. How do you merge two or more objects into one object in JavaScript?
<details><summary><b>Solution</b></summary>
<p>

Using the spread syntax (modern JS):
```javascript
const obj1 = { name: "Alice", age: 30 };
const obj2 = { city: "New York", job: "Developer" };
const mergedObj = { ...obj1, ...obj2 };

console.log(mergedObj); // Output: { name: "Alice", age: 30, city: "New York", job: "Developer" }
```
Using Object.assign (can overwrite properties):
```javascript
const obj1 = { name: "Alice", age: 30 };
const obj2 = { city: "New York", age: 28 }; // Overwrites age from obj1
const mergedObj = Object.assign({}, obj1, obj2);

console.log(mergedObj); // Output: { name: "Alice", age: 28, city: "New York" }
```
Using a loop for selective merging:
```javascript
const obj1 = { name: "Alice", age: 30 };
const obj2 = { city: "New York", age: 28 }; // Overwrites age from obj1
const mergedObj = Object.assign({}, obj1, obj2);

console.log(mergedObj); // Output: { name: "Alice", age: 28, city: "New York" }
```

</p>
</details>

###### 42. How do you destructure an object in JavaScript?
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

</p>
</details>

###### 43. How do you set default values for object properties in JavaScript?
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
- Optional chaining (?.) provides a safe way to access nested properties and set default values if undefined.
- Default values can also be specified during object creation using the assignment operator (||).

</p>
</details>

###### 44. How do you get the number of properties in an object in JavaScript?
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
Using a library like FileSaver.js (for saving or downloading Blobs):
```javascript
// Assuming FileSaver.js is installed (ensure trusted source)
const person = { name: "Alice", age: 30 };
const jsonString = JSON.stringify(person);
const blob = new Blob([jsonString], { type: "application/json" });

FileSaver.saveAs(blob, "person.json"); // Save the Blob as a file (requires user interaction)
```
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
Using TextEncoder for string data and ArrayBuffer.from (modern JS):
```javascript
const person = { name: "Alice" };
const encoder = new TextEncoder();
const encodedString = encoder.encode(JSON.stringify(person)); // String encoded as Uint8Array
const arrayBuffer = ArrayBuffer.from(encodedString); // Create ArrayBuffer from the Uint8Array

console.log(arrayBuffer); // ArrayBuffer object representing the encoded JSON string
```
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
- Iterating over a WeakSet provides access to the weakly referenced objects themselves.
- If the objects hold simple data or can be converted to a suitable format (like JSON), you might be able

</p>
</details>

</div>
</details>
