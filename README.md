# 🚀 JavaScript Mastery Roadmap  
### From Fundamentals to Advanced + Interview Preparation

![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-yellow)
![Status](https://img.shields.io/badge/Status-Active-success)
![Level](https://img.shields.io/badge/Level-Beginner%20to%20Advanced-blue)
![Purpose](https://img.shields.io/badge/Purpose-Skill%20Inhancement-orange)

A structured and practical JavaScript repository covering everything from core concepts to advanced topics with real-world examples and interview-focused explanations.

This repo serves as a **complete JavaScript reference + preparation guide for frontend developers and React engineers.**

---

## 🎯 Why This Repository?

✔ Strong JavaScript foundations  
✔ Modern ES6+ practices  
✔ Real-world coding patterns  
✔ Interview-ready concepts  
✔ Clear explanations with examples

## 📑 Table of Contents

1. [Variables & Scope](#1-variables--scope)
2. [Data Types](#2-data-types)
3. [Type Coercion & Conversion](#3-type-coercion--conversion)
4. [Operators](#4-operators)
5. [Functions](#5-functions)
6. [Arrays & Array Methods](#6-arrays--array-methods)
7. [Objects & Object Methods](#7-objects--object-methods)
8. [Destructuring](#8-destructuring)
9. [Spread & Rest Operators](#9-spread--rest-operators)
10. [Control Flow](#10-control-flow)
11. [Loops](#11-loops)
12. [Scope & Hoisting](#12-scope--hoisting)
13. [Closures](#13-closures)
14. [this Keyword](#14-this-keyword)
15. [call, apply, bind](#15-call-apply-bind)
16. [Prototypes & Inheritance](#16-prototypes--inheritance)
17. [ES6+ Features](#17-es6-features)
18. [Asynchronous JavaScript](#18-asynchronous-javascript)
19. [Event Loop](#19-event-loop)
20. [Error Handling](#20-error-handling)
21. [DOM Manipulation](#21-dom-manipulation)
22. [Web Storage](#22-web-storage)
23. [Modules](#23-modules)
24. [API & Fetch](#24-api--fetch)
25. [Common Interview Questions](#25-common-interview-questions)

---

## 1. Variables & Scope

### Variable Declaration Types

```javascript
// var - Function scoped, hoisted, can be redeclared
var x = 10;
var x = 20; // ✅ Allowed
x = 30;     // ✅ Allowed

// let - Block scoped, hoisted but not initialized, cannot be redeclared
let y = 10;
// let y = 20; // ❌ Error: Cannot redeclare
y = 30;        // ✅ Allowed

// const - Block scoped, hoisted but not initialized, cannot be reassigned
const z = 10;
// const z = 20; // ❌ Error: Cannot redeclare
// z = 30;       // ❌ Error: Cannot reassign

// BUT: const with objects/arrays allows mutation
const obj = { name: "John" };
obj.name = "Jane"; // ✅ Allowed (mutation)
obj.age = 25;      // ✅ Allowed (adding property)
// obj = {};       // ❌ Error: Cannot reassign
```

### Key Differences

| Feature | var | let | const |
|---------|-----|-----|-------|
| Scope | Function | Block | Block |
| Hoisting | Yes (undefined) | Yes (TDZ) | Yes (TDZ) |
| Redeclaration | ✅ | ❌ | ❌ |
| Reassignment | ✅ | ✅ | ❌ |
| Temporal Dead Zone | No | Yes | Yes |

**Best Practice:** Use `const` by default, `let` when reassignment needed, avoid `var`.

---

## 2. Data Types

### Primitive Types (7)

```javascript
// 1. String
let str = "Hello World";
let str2 = 'Single quotes';
let str3 = `Template literal: ${str}`; // ES6

// 2. Number
let num = 42;
let float = 3.14;
let negative = -10;
let infinity = Infinity;
let notANumber = NaN;

// 3. BigInt (ES2020)
let bigInt = 1234567890123456789012345678901234567890n;
let bigInt2 = BigInt("9007199254740991");

// 4. Boolean
let isTrue = true;
let isFalse = false;

// 5. Undefined
let notDefined;
console.log(notDefined); // undefined

// 6. Null
let empty = null; // intentional absence of value

// 7. Symbol (ES6)
let sym1 = Symbol("description");
let sym2 = Symbol("description");
console.log(sym1 === sym2); // false - symbols are always unique
```

### Non-Primitive (Reference) Types

```javascript
// 1. Object
let person = {
  name: "John",
  age: 30,
  greet() {
    console.log(`Hello, I'm ${this.name}`);
  }
};

// 2. Array
let numbers = [1, 2, 3, 4, 5];
let mixed = [1, "hello", true, null, { key: "value" }];

// 3. Function
function greet(name) {
  return `Hello, ${name}!`;
}

// 4. Date
let now = new Date();

// 5. RegExp
let pattern = /[a-z]+/gi;

// 6. Map (ES6)
let map = new Map();
map.set('key', 'value');

// 7. Set (ES6)
let set = new Set([1, 2, 3, 3, 4]); // {1, 2, 3, 4}
```

### Type Checking

```javascript
typeof "hello"           // "string"
typeof 42                // "number"
typeof true              // "boolean"
typeof undefined         // "undefined"
typeof Symbol()          // "symbol"
typeof 123n              // "bigint"

typeof null              // "object" ⚠️ (JavaScript bug)
typeof []                // "object"
typeof {}                // "object"
typeof function(){}      // "function"

// Better type checking
Array.isArray([])        // true
null === null            // true (use strict equality)
```

---

## 3. Type Coercion & Conversion

### Implicit Coercion

```javascript
// String coercion
"5" + 3        // "53" (number to string)
"5" + true     // "5true"
"5" + null     // "5null"

// Number coercion
"5" - 3        // 2 (string to number)
"5" * "2"      // 10
"10" / "2"     // 5
"5" - true     // 4 (true = 1)

// Boolean coercion
Boolean(0)          // false
Boolean("")         // false
Boolean(null)       // false
Boolean(undefined)  // false
Boolean(NaN)        // false
Boolean([])         // true
Boolean({})         // true
Boolean("0")        // true
```

### Explicit Conversion

```javascript
// To String
String(123)              // "123"
(123).toString()         // "123"
123 + ""                 // "123"

// To Number
Number("123")            // 123
parseInt("123.45")       // 123
parseFloat("123.45")     // 123.45
+"123"                   // 123 (unary plus)

// To Boolean
Boolean(1)               // true
!!"hello"                // true (double negation)
```

### Equality Comparisons

```javascript
// == (loose equality - type coercion)
5 == "5"        // true
0 == false      // true
null == undefined // true

// === (strict equality - no coercion)
5 === "5"       // false
0 === false     // false
null === undefined // false

// Always use === for predictable behavior
```

---

## 4. Operators

### Arithmetic Operators

```javascript
let a = 10, b = 3;

a + b    // 13 (Addition)
a - b    // 7  (Subtraction)
a * b    // 30 (Multiplication)
a / b    // 3.333... (Division)
a % b    // 1  (Modulus/Remainder)
a ** b   // 1000 (Exponentiation - ES7)

// Increment/Decrement
let x = 5;
x++      // 5 (returns then increments: x becomes 6)
++x      // 7 (increments then returns)
x--      // 7 (returns then decrements: x becomes 6)
--x      // 5 (decrements then returns)
```

### Comparison Operators

```javascript
5 > 3     // true
5 < 3     // false
5 >= 5    // true
5 <= 3    // false
5 == "5"  // true (loose equality)
5 === "5" // false (strict equality)
5 != "5"  // false
5 !== "5" // true
```

### Logical Operators

```javascript
// AND (&&) - returns first falsy or last value
true && true           // true
true && false          // false
"hello" && "world"     // "world"
0 && "hello"           // 0 (short-circuit)

// OR (||) - returns first truthy or last value
true || false          // true
false || false         // false
0 || "hello"           // "hello"
null || undefined      // undefined

// NOT (!)
!true                  // false
!0                     // true
!"hello"               // false

// Nullish Coalescing (??) - ES2020
null ?? "default"      // "default"
undefined ?? "default" // "default"
0 ?? "default"         // 0 (only null/undefined trigger default)
"" ?? "default"        // ""
```

### Assignment Operators

```javascript
let x = 10;
x += 5   // x = x + 5  → 15
x -= 3   // x = x - 3  → 12
x *= 2   // x = x * 2  → 24
x /= 4   // x = x / 4  → 6
x %=  5  // x = x % 5  → 1
x **= 2  // x = x ** 2 → 1

// Logical Assignment (ES2021)
x ||= 10  // x = x || 10 (assign if falsy)
x &&= 20  // x = x && 20 (assign if truthy)
x ??= 30  // x = x ?? 30 (assign if null/undefined)
```

### Ternary Operator

```javascript
let age = 18;
let canVote = age >= 18 ? "Yes" : "No"; // "Yes"

// Nested ternary (use sparingly)
let grade = score >= 90 ? "A" : score >= 80 ? "B" : "C";
```

### Optional Chaining (?.) - ES2020

```javascript
let user = {
  name: "John",
  address: {
    city: "NYC"
  }
};

user.address?.city         // "NYC"
user.contact?.phone        // undefined (no error)
user.greet?.()             // undefined (method doesn't exist)
arr?.[0]                   // safe array access
```

---

## 5. Functions

### Function Declaration

```javascript
// Hoisted - can be called before declaration
function greet(name) {
  return `Hello, ${name}!`;
}

greet("John"); // "Hello, John!"
```

### Function Expression

```javascript
// Not hoisted - must be declared before use
const greet = function(name) {
  return `Hello, ${name}!`;
};

greet("Jane"); // "Hello, Jane!"
```

### Arrow Functions (ES6)

```javascript
// Basic syntax
const greet = (name) => {
  return `Hello, ${name}!`;
};

// Implicit return (single expression)
const greet = name => `Hello, ${name}!`;

// Multiple parameters
const add = (a, b) => a + b;

// No parameters
const sayHi = () => "Hi!";

// Returning object literal (wrap in parentheses)
const getPerson = () => ({ name: "John", age: 30 });

// ⚠️ Arrow functions don't have their own 'this'
const obj = {
  name: "John",
  regularFunc: function() {
    console.log(this.name); // "John"
  },
  arrowFunc: () => {
    console.log(this.name); // undefined (lexical this)
  }
};
```

### Parameters & Arguments

```javascript
// Default parameters (ES6)
function greet(name = "Guest", greeting = "Hello") {
  return `${greeting}, ${name}!`;
}

greet();              // "Hello, Guest!"
greet("John");        // "Hello, John!"
greet("Jane", "Hi");  // "Hi, Jane!"

// Rest parameters (ES6)
function sum(...numbers) {
  return numbers.reduce((acc, num) => acc + num, 0);
}

sum(1, 2, 3, 4, 5); // 15

// Arguments object (avoid in modern code)
function oldStyle() {
  console.log(arguments); // array-like object
}
```

### Higher-Order Functions

```javascript
// Function that takes a function as argument
function executeFunc(callback, value) {
  return callback(value);
}

executeFunc(x => x * 2, 5); // 10

// Function that returns a function
function multiplier(factor) {
  return function(number) {
    return number * factor;
  };
}

const double = multiplier(2);
const triple = multiplier(3);

double(5); // 10
triple(5); // 15

// Arrow function version
const multiplier = factor => number => number * factor;
```

### IIFE (Immediately Invoked Function Expression)

```javascript
// Classic pattern for module/scope isolation
(function() {
  let private = "I'm private";
  console.log("IIFE executed!");
})();

// With parameters
(function(name) {
  console.log(`Hello, ${name}!`);
})("John");

// Arrow IIFE
(() => {
  console.log("Arrow IIFE");
})();
```

### Pure Functions

```javascript
// Pure function: same input → same output, no side effects
function add(a, b) {
  return a + b;
}

// Impure function: modifies external state
let total = 0;
function addToTotal(value) {
  total += value; // side effect
  return total;
}

// Impure function: depends on external state
function getTime() {
  return new Date(); // different output each call
}
```

---

## 6. Arrays & Array Methods

### Creating Arrays

```javascript
// Array literal
let arr1 = [1, 2, 3, 4, 5];

// Array constructor
let arr2 = new Array(1, 2, 3);
let arr3 = new Array(5); // creates array with 5 empty slots

// Array.from() - ES6
let arr4 = Array.from("hello"); // ['h', 'e', 'l', 'l', 'o']
let arr5 = Array.from({ length: 5 }, (_, i) => i); // [0, 1, 2, 3, 4]

// Array.of() - ES6
let arr6 = Array.of(1, 2, 3); // [1, 2, 3]
```

### Mutating Methods (Change original array)

```javascript
let arr = [1, 2, 3, 4, 5];

// push() - add to end
arr.push(6);           // [1, 2, 3, 4, 5, 6], returns 6 (new length)

// pop() - remove from end
arr.pop();             // [1, 2, 3, 4, 5], returns 6

// unshift() - add to beginning
arr.unshift(0);        // [0, 1, 2, 3, 4, 5], returns 6

// shift() - remove from beginning
arr.shift();           // [1, 2, 3, 4, 5], returns 0

// splice() - add/remove at any position
arr.splice(2, 1);      // [1, 2, 4, 5] (removed 3)
arr.splice(2, 0, 3);   // [1, 2, 3, 4, 5] (added 3 at index 2)
arr.splice(1, 2, 'a', 'b'); // [1, 'a', 'b', 4, 5]

// reverse() - reverse array
arr.reverse();         // [5, 4, 3, 2, 1]

// sort() - sort array
arr.sort();                    // alphabetical sort
arr.sort((a, b) => a - b);     // ascending numbers
arr.sort((a, b) => b - a);     // descending numbers

// fill() - ES6
arr.fill(0);           // [0, 0, 0, 0, 0]
arr.fill(1, 2, 4);     // [0, 0, 1, 1, 0] (fill 1 from index 2 to 4)
```

### Non-Mutating Methods (Return new array/value)

```javascript
let arr = [1, 2, 3, 4, 5];

// slice() - extract portion
arr.slice(1, 3);       // [2, 3] (index 1 to 3, excluding 3)
arr.slice(2);          // [3, 4, 5] (from index 2 to end)
arr.slice(-2);         // [4, 5] (last 2 elements)

// concat() - combine arrays
arr.concat([6, 7]);    // [1, 2, 3, 4, 5, 6, 7]
[...arr, 6, 7];        // [1, 2, 3, 4, 5, 6, 7] (spread alternative)

// join() - array to string
arr.join();            // "1,2,3,4,5"
arr.join('-');         // "1-2-3-4-5"

// indexOf() - find index of element
arr.indexOf(3);        // 2
arr.indexOf(10);       // -1 (not found)

// lastIndexOf() - find last occurrence
[1, 2, 3, 2, 1].lastIndexOf(2); // 3

// includes() - ES7
arr.includes(3);       // true
arr.includes(10);      // false

// toString()
arr.toString();        // "1,2,3,4,5"
```

### Iteration Methods

```javascript
let arr = [1, 2, 3, 4, 5];

// forEach() - execute function for each element
arr.forEach((item, index, array) => {
  console.log(`${index}: ${item}`);
});

// map() - transform each element, returns new array
let doubled = arr.map(x => x * 2); // [2, 4, 6, 8, 10]

// filter() - select elements matching condition
let evens = arr.filter(x => x % 2 === 0); // [2, 4]

// reduce() - reduce to single value
let sum = arr.reduce((acc, curr) => acc + curr, 0); // 15
let product = arr.reduce((acc, curr) => acc * curr, 1); // 120

// reduceRight() - reduce from right to left
let result = [1, 2, 3].reduceRight((acc, curr) => acc - curr, 10); // 4

// find() - ES6, returns first matching element
let found = arr.find(x => x > 3); // 4

// findIndex() - ES6, returns index of first match
let index = arr.findIndex(x => x > 3); // 3

// findLast() - ES2023, returns last matching element
let last = [1, 2, 3, 4, 5].findLast(x => x > 3); // 5

// findLastIndex() - ES2023
let lastIndex = [1, 2, 3, 4, 5].findLastIndex(x => x > 3); // 4

// some() - check if at least one element matches
let hasEven = arr.some(x => x % 2 === 0); // true

// every() - check if all elements match
let allPositive = arr.every(x => x > 0); // true

// flat() - ES2019, flatten nested arrays
let nested = [1, [2, 3], [4, [5, 6]]];
nested.flat();        // [1, 2, 3, 4, [5, 6]]
nested.flat(2);       // [1, 2, 3, 4, 5, 6]
nested.flat(Infinity); // fully flatten

// flatMap() - ES2019, map + flat(1)
let words = ["hello world", "foo bar"];
words.flatMap(str => str.split(' ')); // ['hello', 'world', 'foo', 'bar']
```

### Array Destructuring

```javascript
let arr = [1, 2, 3, 4, 5];

// Basic destructuring
let [first, second] = arr; // first = 1, second = 2

// Skip elements
let [a, , c] = arr; // a = 1, c = 3

// Rest pattern
let [head, ...tail] = arr; // head = 1, tail = [2, 3, 4, 5]

// Default values
let [x = 0, y = 0] = [1]; // x = 1, y = 0

// Swapping variables
let a = 1, b = 2;
[a, b] = [b, a]; // a = 2, b = 1
```

---

## 7. Objects & Object Methods

### Creating Objects

```javascript
// Object literal
let person = {
  name: "John",
  age: 30,
  greet() {
    return `Hello, I'm ${this.name}`;
  }
};

// Object constructor
let obj = new Object();
obj.name = "Jane";

// Object.create()
let proto = { greet() { return "Hi!"; } };
let person2 = Object.create(proto);
person2.name = "Bob";
```

### Accessing Properties

```javascript
let person = { name: "John", age: 30, "full-name": "John Doe" };

// Dot notation
person.name;           // "John"

// Bracket notation
person["age"];         // 30
person["full-name"];   // "John Doe" (required for special chars)

// Dynamic property access
let prop = "name";
person[prop];          // "John"
```

### Adding/Modifying Properties

```javascript
let obj = { name: "John" };

// Add property
obj.age = 30;
obj["city"] = "NYC";

// Modify property
obj.name = "Jane";

// Computed property names (ES6)
let key = "dynamicKey";
let obj2 = {
  [key]: "value",
  [`${key}_2`]: "value2"
};
```

### Deleting Properties

```javascript
let obj = { name: "John", age: 30 };

delete obj.age;
console.log(obj); // { name: "John" }
```

### Object Methods

```javascript
let person = {
  firstName: "John",
  lastName: "Doe",
  age: 30
};

// Object.keys() - returns array of keys
Object.keys(person); // ["firstName", "lastName", "age"]

// Object.values() - ES2017
Object.values(person); // ["John", "Doe", 30]

// Object.entries() - ES2017
Object.entries(person); // [["firstName", "John"], ["lastName", "Doe"], ["age", 30]]

// Object.assign() - shallow copy/merge
let copy = Object.assign({}, person);
let merged = Object.assign({}, person, { city: "NYC" });

// Object.freeze() - prevent all changes
Object.freeze(person);
person.age = 31;       // ❌ Silently fails (strict mode: error)
delete person.age;     // ❌ Silently fails
person.city = "LA";    // ❌ Silently fails

// Object.seal() - prevent add/delete, allow modify
let obj = { name: "John" };
Object.seal(obj);
obj.name = "Jane";     // ✅ Allowed
obj.age = 30;          // ❌ Not allowed
delete obj.name;       // ❌ Not allowed

// Object.isFrozen(), Object.isSealed()
Object.isFrozen(person); // true
Object.isSealed(obj);     // true

// Object.preventExtensions() - prevent adding properties
let obj2 = { name: "John" };
Object.preventExtensions(obj2);
obj2.age = 30;         // ❌ Not allowed
obj2.name = "Jane";    // ✅ Allowed
delete obj2.name;      // ✅ Allowed

// hasOwnProperty() - check if property exists
person.hasOwnProperty("name"); // true
person.hasOwnProperty("toString"); // false (inherited)

// in operator - checks own and inherited properties
"name" in person;      // true
"toString" in person;  // true (inherited from Object.prototype)

// Object.fromEntries() - ES2019
let entries = [["name", "John"], ["age", 30]];
Object.fromEntries(entries); // { name: "John", age: 30 }

// Object.getOwnPropertyNames()
Object.getOwnPropertyNames(person); // ["firstName", "lastName", "age"]
```

### Shorthand Properties (ES6)

```javascript
let name = "John";
let age = 30;

// Shorthand property
let person = { name, age }; // { name: "John", age: 30 }

// Method shorthand
let obj = {
  greet() {
    return "Hello!";
  }
  // instead of: greet: function() { return "Hello!"; }
};
```

### Object Destructuring

```javascript
let person = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  address: {
    city: "NYC",
    country: "USA"
  }
};

// Basic destructuring
let { firstName, age } = person;

// Rename variables
let { firstName: fName, lastName: lName } = person;

// Default values
let { firstName, city = "Unknown" } = person;

// Nested destructuring
let { address: { city, country } } = person;

// Rest pattern
let { firstName, ...rest } = person;
// rest = { lastName: "Doe", age: 30, address: {...} }
```

---

## 8. Destructuring

### Array Destructuring

```javascript
// Basic
let [a, b, c] = [1, 2, 3];

// Skip elements
let [first, , third] = [1, 2, 3]; // first=1, third=3

// Rest operator
let [head, ...tail] = [1, 2, 3, 4]; // head=1, tail=[2,3,4]

// Default values
let [x = 5, y = 10] = [1]; // x=1, y=10

// Nested arrays
let [a, [b, c]] = [1, [2, 3]]; // a=1, b=2, c=3

// Swapping
let a = 1, b = 2;
[b, a] = [a, b]; // a=2, b=1
```

### Object Destructuring

```javascript
// Basic
let { name, age } = { name: "John", age: 30 };

// Rename
let { name: userName, age: userAge } = { name: "John", age: 30 };

// Default values
let { name = "Guest", role = "User" } = { name: "John" };
// name="John", role="User"

// Nested objects
let user = {
  id: 1,
  profile: {
    name: "John",
    address: {
      city: "NYC"
    }
  }
};

let { profile: { name, address: { city } } } = user;

// Rest operator
let { name, ...rest } = { name: "John", age: 30, city: "NYC" };
// rest = { age: 30, city: "NYC" }
```

### Function Parameter Destructuring

```javascript
// Array destructuring in params
function sum([a, b]) {
  return a + b;
}
sum([1, 2]); // 3

// Object destructuring in params
function greet({ name, age = 18 }) {
  return `Hello ${name}, age ${age}`;
}
greet({ name: "John", age: 30 }); // "Hello John, age 30"
greet({ name: "Jane" });          // "Hello Jane, age 18"

// Practical example
function processUser({ 
  id, 
  name, 
  email, 
  role = "user",
  permissions = [] 
}) {
  // Use destructured values directly
  console.log(`${name} (${role}) - ${email}`);
}
```

---

## 9. Spread & Rest Operators

### Spread Operator (...)

Expands iterables (arrays, objects, strings) into individual elements.

```javascript
// Array spreading
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];

// Combine arrays
let combined = [...arr1, ...arr2]; // [1, 2, 3, 4, 5, 6]

// Copy array (shallow)
let copy = [...arr1]; // [1, 2, 3]

// Add elements
let extended = [0, ...arr1, 4]; // [0, 1, 2, 3, 4]

// String to array
let chars = [..."hello"]; // ['h', 'e', 'l', 'l', 'o']

// Object spreading (ES2018)
let obj1 = { a: 1, b: 2 };
let obj2 = { c: 3, d: 4 };

// Combine objects
let merged = { ...obj1, ...obj2 }; // { a: 1, b: 2, c: 3, d: 4 }

// Copy object (shallow)
let objCopy = { ...obj1 };

// Override properties
let updated = { ...obj1, b: 20 }; // { a: 1, b: 20 }

// Add properties
let extended = { ...obj1, c: 3 }; // { a: 1, b: 2, c: 3 }

// Function arguments
function sum(x, y, z) {
  return x + y + z;
}

let numbers = [1, 2, 3];
sum(...numbers); // 6 (same as sum(1, 2, 3))

// Math functions
Math.max(...[1, 5, 3, 9, 2]); // 9
```

### Rest Operator (...)

Collects multiple elements into a single array/object.

```javascript
// Rest in function parameters
function sum(...numbers) {
  return numbers.reduce((acc, num) => acc + num, 0);
}

sum(1, 2, 3, 4, 5); // 15

// Mix regular params with rest
function greet(greeting, ...names) {
  return `${greeting} ${names.join(", ")}!`;
}

greet("Hello", "John", "Jane", "Bob"); // "Hello John, Jane, Bob!"

// Rest in array destructuring
let [first, second, ...rest] = [1, 2, 3, 4, 5];
// first=1, second=2, rest=[3, 4, 5]

// Rest in object destructuring
let { name, age, ...otherInfo } = {
  name: "John",
  age: 30,
  city: "NYC",
  country: "USA"
};
// name="John", age=30, otherInfo={ city: "NYC", country: "USA" }
```

### Spread vs Rest

```javascript
// SPREAD: Expands (unpacks)
let arr = [1, 2, 3];
console.log(...arr); // 1 2 3 (expands into individual elements)

// REST: Collects (packs)
function foo(...args) {
  console.log(args); // [1, 2, 3] (collects into array)
}
foo(1, 2, 3);
```

**Key Difference:** 
- **Spread**: Right side of assignment `let arr = [...original]`
- **Rest**: Left side of assignment `let [...rest] = arr` or in function parameters

---

## 10. Control Flow

### if Statement

```javascript
let age = 18;

if (age >= 18) {
  console.log("You can vote");
}

// Single line (avoid unless very simple)
if (age >= 18) console.log("You can vote");
```

### if...else Statement

```javascript
let age = 16;

if (age >= 18) {
  console.log("You can vote");
} else {
  console.log("You cannot vote");
}
```

### if...else if...else Statement

```javascript
let score = 85;

if (score >= 90) {
  console.log("Grade: A");
} else if (score >= 80) {
  console.log("Grade: B");
} else if (score >= 70) {
  console.log("Grade: C");
} else if (score >= 60) {
  console.log("Grade: D");
} else {
  console.log("Grade: F");
}
```

### switch Statement

```javascript
let day = "monday";

switch (day) {
  case "monday":
    console.log("Start of the work week");
    break;
  case "tuesday":
  case "wednesday":
  case "thursday":
    console.log("Midweek");
    break;
  case "friday":
    console.log("TGIF!");
    break;
  case "saturday":
  case "sunday":
    console.log("Weekend!");
    break;
  default:
    console.log("Invalid day");
}

// ⚠️ Without break, it falls through
let x = 1;
switch (x) {
  case 1:
    console.log("One");
    // no break - falls through!
  case 2:
    console.log("Two"); // This also executes!
    break;
}
// Output: "One" "Two"
```

### Ternary Operator

```javascript
// condition ? expressionIfTrue : expressionIfFalse

let age = 20;
let canVote = age >= 18 ? "Yes" : "No";

// Nested ternary (use sparingly - readability!)
let grade = score >= 90 ? "A" 
          : score >= 80 ? "B"
          : score >= 70 ? "C"
          : "F";

// Multiple operations
let result = condition 
  ? (console.log("True"), "value1")
  : (console.log("False"), "value2");
```

### Truthy and Falsy Values

```javascript
// Falsy values (only 7!)
if (false) { }        // false
if (0) { }            // 0
if (-0) { }           // -0
if (0n) { }           // 0n (BigInt zero)
if ("") { }           // empty string
if (null) { }         // null
if (undefined) { }    // undefined
if (NaN) { }          // NaN

// Everything else is truthy!
if (true) { }         // ✅
if (1) { }            // ✅
if ("0") { }          // ✅ (string)
if ("false") { }      // ✅ (string)
if ([]) { }           // ✅ (empty array)
if ({}) { }           // ✅ (empty object)
if (function(){}) { } // ✅

// Practical usage
let user = getUserData(); // might return null
if (user) {
  console.log(user.name); // safe to access
}
```

### Short-Circuit Evaluation

```javascript
// && returns first falsy or last value
let result = true && "hello" && 42; // 42
let result = true && false && 42;   // false
let result = 0 && "hello";          // 0

// Practical: conditional execution
isLoggedIn && redirectToDashboard();

// || returns first truthy or last value
let result = false || 0 || "hello"; // "hello"
let result = null || undefined;     // undefined

// Practical: default values
let username = inputName || "Guest";

// ?? (nullish coalescing) - only null/undefined
let username = inputName ?? "Guest";
let count = 0 ?? 10; // 0 (not replaced, unlike ||)
```

---

## 11. Loops

### for Loop

```javascript
// Classic for loop
for (let i = 0; i < 5; i++) {
  console.log(i); // 0, 1, 2, 3, 4
}

// Iterate array
let arr = [10, 20, 30, 40];
for (let i = 0; i < arr.length; i++) {
  console.log(arr[i]);
}

// Reverse loop
for (let i = arr.length - 1; i >= 0; i--) {
  console.log(arr[i]); // 40, 30, 20, 10
}

// Multiple variables
for (let i = 0, j = 10; i < 5; i++, j--) {
  console.log(i, j); // 0 10, 1 9, 2 8, 3 7, 4 6
}
```

### while Loop

```javascript
// while loop - condition checked before execution
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}

// Practical: unknown iterations
let input;
while (input !== "quit") {
  input = getUserInput();
  processInput(input);
}
```

### do...while Loop

```javascript
// do-while - executes at least once
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);

// Executes even when condition is false initially
let j = 10;
do {
  console.log(j); // Prints 10 once
} while (j < 5);

// Practical: menu systems
let choice;
do {
  displayMenu();
  choice = getChoice();
} while (choice !== "exit");
```

### for...of Loop (ES6)

**Best for:** Arrays, Strings, Maps, Sets, NodeLists

```javascript
// Iterate array values
let arr = [10, 20, 30];
for (let value of arr) {
  console.log(value); // 10, 20, 30
}

// Iterate string characters
for (let char of "hello") {
  console.log(char); // h, e, l, l, o
}

// With index using entries()
for (let [index, value] of arr.entries()) {
  console.log(index, value); // 0 10, 1 20, 2 30
}

// Iterate Map
let map = new Map([["a", 1], ["b", 2]]);
for (let [key, value] of map) {
  console.log(key, value);
}

// Iterate Set
let set = new Set([1, 2, 3]);
for (let value of set) {
  console.log(value);
}

// ⚠️ Cannot iterate objects directly
let obj = { a: 1, b: 2 };
// for (let item of obj) { } // ❌ Error

// Workaround for objects:
for (let key of Object.keys(obj)) {
  console.log(key, obj[key]);
}
```

### for...in Loop

**Best for:** Object properties (avoid for arrays)

```javascript
// Iterate object properties
let person = {
  name: "John",
  age: 30,
  city: "NYC"
};

for (let key in person) {
  console.log(key, person[key]);
  // name John
  // age 30
  // city NYC
}

// ⚠️ for...in on arrays (not recommended)
let arr = [10, 20, 30];
for (let index in arr) {
  console.log(index, arr[index]); // index is STRING "0", "1", "2"
}

// Check own properties (not inherited)
for (let key in person) {
  if (person.hasOwnProperty(key)) {
    console.log(key, person[key]);
  }
}
```

### Loop Control: break & continue

```javascript
// break - exit loop completely
for (let i = 0; i < 10; i++) {
  if (i === 5) break;
  console.log(i); // 0, 1, 2, 3, 4
}

// continue - skip current iteration
for (let i = 0; i < 5; i++) {
  if (i === 2) continue;
  console.log(i); // 0, 1, 3, 4 (skips 2)
}

// Labeled statements (rare, but useful)
outer: for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    if (i === 1 && j === 1) break outer;
    console.log(i, j);
  }
}
```

### Array Iteration Methods (Preferred)

```javascript
let arr = [1, 2, 3, 4, 5];

// forEach - execute for each element
arr.forEach((item, index) => {
  console.log(index, item);
});

// map - transform array
let doubled = arr.map(x => x * 2);

// filter - select elements
let evens = arr.filter(x => x % 2 === 0);

// reduce - accumulate value
let sum = arr.reduce((acc, val) => acc + val, 0);

// some - check if any match
let hasEven = arr.some(x => x % 2 === 0);

// every - check if all match
let allPositive = arr.every(x => x > 0);

// find - first matching element
let found = arr.find(x => x > 3);

// findIndex - index of first match
let index = arr.findIndex(x => x > 3);
```

---

## 12. Scope & Hoisting

### Scope Types

**Scope** determines where variables are accessible in your code.

```javascript
// 1. Global Scope
var globalVar = "I'm global";
let globalLet = "Also global";

function test() {
  console.log(globalVar); // ✅ Accessible
}

// 2. Function Scope (var)
function myFunc() {
  var functionScoped = "Only in function";
  
  if (true) {
    var stillFunctionScoped = "Still in function";
  }
  
  console.log(stillFunctionScoped); // ✅ Accessible
}

// console.log(functionScoped); // ❌ ReferenceError

// 3. Block Scope (let, const)
{
  let blockScoped = "Only in block";
  const alsoBlockScoped = "Also only in block";
  var notBlockScoped = "I escape!";
}

// console.log(blockScoped); // ❌ ReferenceError
console.log(notBlockScoped); // ✅ Accessible (var ignores blocks)

// if/for blocks
if (true) {
  let x = 10;
  var y = 20;
}
// console.log(x); // ❌ Error
console.log(y);    // ✅ 20

for (let i = 0; i < 3; i++) {
  // i is block-scoped to this loop
}
// console.log(i); // ❌ Error

for (var j = 0; j < 3; j++) {
  // j is function/global scoped
}
console.log(j); // ✅ 3
```

### Lexical Scope (Static Scope)

Functions are executed using the scope chain from where they were **defined**, not where they're **called**.

```javascript
let name = "Global";

function outer() {
  let name = "Outer";
  
  function inner() {
    console.log(name); // "Outer" (looks up scope chain)
  }
  
  return inner;
}

let func = outer();
func(); // "Outer" (not "Global")

// Practical example
function makeCounter() {
  let count = 0; // Private variable
  
  return function() {
    return ++count;
  };
}

let counter = makeCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
```

### Hoisting

**Hoisting** is JavaScript's behavior of moving declarations to the top of their scope before code execution.

```javascript
// Variable Hoisting

// var - hoisted and initialized with undefined
console.log(x); // undefined (not error!)
var x = 5;

// Actual behavior:
var x; // hoisted to top
console.log(x); // undefined
x = 5;

// let & const - hoisted but NOT initialized (TDZ)
// console.log(y); // ❌ ReferenceError: Cannot access before initialization
let y = 10;

// console.log(z); // ❌ ReferenceError
const z = 20;

// Function Hoisting

// Function declarations - fully hoisted
greet(); // ✅ "Hello!" (works before declaration)

function greet() {
  console.log("Hello!");
}

// Function expressions - NOT hoisted
// sayHi(); // ❌ TypeError: sayHi is not a function

var sayHi = function() {
  console.log("Hi!");
};

// Arrow functions - NOT hoisted
// greet2(); // ❌ ReferenceError

const greet2 = () => {
  console.log("Hello!");
};
```

### Temporal Dead Zone (TDZ)

```javascript
// TDZ - period between entering scope and variable declaration

{
  // TDZ starts
  // console.log(x); // ❌ ReferenceError
  // console.log(y); // ❌ ReferenceError
  
  let x = 10; // TDZ ends for x
  const y = 20; // TDZ ends for y
  
  console.log(x); // ✅ 10
  console.log(y); // ✅ 20
}

// typeof is not safe in TDZ
{
  // typeof x; // ❌ ReferenceError (x is in TDZ)
  let x = 10;
}

// But safe for undeclared variables
console.log(typeof undeclaredVar); // ✅ "undefined"
```

### Scope Chain

```javascript
let global = "global";

function outer() {
  let outer = "outer";
  
  function middle() {
    let middle = "middle";
    
    function inner() {
      let inner = "inner";
      
      // Scope chain: inner → middle → outer → global
      console.log(inner);  // "inner" (found in local scope)
      console.log(middle); // "middle" (found in parent scope)
      console.log(outer);  // "outer" (found in grandparent scope)
      console.log(global); // "global" (found in global scope)
    }
    
    inner();
  }
  
  middle();
}

outer();
```

---

## 13. Closures

**Closure:** A function bundled together with references to its surrounding state (lexical environment). Closures give functions access to outer scope even after the outer function has returned.

### Basic Closure

```javascript
function outer() {
  let count = 0; // Private variable
  
  function inner() {
    count++;
    console.log(count);
  }
  
  return inner;
}

let counter = outer();
counter(); // 1
counter(); // 2
counter(); // 3

// count is not accessible from outside
// console.log(count); // ❌ ReferenceError
```

### Practical Examples

```javascript
// 1. Data Privacy / Encapsulation
function createBankAccount(initialBalance) {
  let balance = initialBalance; // Private
  
  return {
    deposit(amount) {
      balance += amount;
      return balance;
    },
    withdraw(amount) {
      if (amount <= balance) {
        balance -= amount;
        return balance;
      }
      return "Insufficient funds";
    },
    getBalance() {
      return balance;
    }
  };
}

let account = createBankAccount(100);
account.deposit(50);     // 150
account.withdraw(30);    // 120
account.getBalance();    // 120
// account.balance;      // ❌ undefined (can't access directly)

// 2. Function Factory
function multiplier(factor) {
  return function(number) {
    return number * factor;
  };
}

let double = multiplier(2);
let triple = multiplier(3);

double(5); // 10
triple(5); // 15

// 3. Event Handlers
function setupButtons() {
  for (let i = 0; i < 5; i++) {
    let button = document.createElement('button');
    button.textContent = `Button ${i}`;
    
    // Closure captures current value of i
    button.onclick = function() {
      console.log(`Button ${i} clicked`);
    };
    
    document.body.appendChild(button);
  }
}

// ⚠️ Common mistake with var:
function setupButtonsWrong() {
  for (var i = 0; i < 5; i++) {
    let button = document.createElement('button');
    button.textContent = `Button ${i}`;
    
    button.onclick = function() {
      console.log(`Button ${i} clicked`); // Always logs 5!
    };
    
    document.body.appendChild(button);
  }
}

// Fix with IIFE:
function setupButtonsFix() {
  for (var i = 0; i < 5; i++) {
    (function(index) {
      let button = document.createElement('button');
      button.textContent = `Button ${index}`;
      
      button.onclick = function() {
        console.log(`Button ${index} clicked`);
      };
      
      document.body.appendChild(button);
    })(i);
  }
}

// 4. Memoization (Caching)
function memoize(fn) {
  let cache = {};
  
  return function(...args) {
    let key = JSON.stringify(args);
    
    if (key in cache) {
      console.log("Returning cached result");
      return cache[key];
    }
    
    console.log("Calculating result");
    let result = fn(...args);
    cache[key] = result;
    return result;
  };
}

function expensiveOperation(n) {
  return n * n;
}

let memoized = memoize(expensiveOperation);
memoized(5); // "Calculating result", returns 25
memoized(5); // "Returning cached result", returns 25

// 5. Curry Functions
function curry(fn) {
  return function curried(...args) {
    if (args.length >= fn.length) {
      return fn.apply(this, args);
    }
    return function(...nextArgs) {
      return curried.apply(this, args.concat(nextArgs));
    };
  };
}

function sum(a, b, c) {
  return a + b + c;
}

let curriedSum = curry(sum);
curriedSum(1)(2)(3);  // 6
curriedSum(1, 2)(3);  // 6
curriedSum(1)(2, 3);  // 6
```

### Closure with setTimeout

```javascript
// Problem: var doesn't create closure properly
for (var i = 1; i <= 3; i++) {
  setTimeout(function() {
    console.log(i); // Prints: 4, 4, 4
  }, i * 1000);
}

// Solution 1: Use let (block scope)
for (let i = 1; i <= 3; i++) {
  setTimeout(function() {
    console.log(i); // Prints: 1, 2, 3
  }, i * 1000);
}

// Solution 2: IIFE with var
for (var i = 1; i <= 3; i++) {
  (function(j) {
    setTimeout(function() {
      console.log(j); // Prints: 1, 2, 3
    }, j * 1000);
  })(i);
}

// Solution 3: Extra parameter to setTimeout
for (var i = 1; i <= 3; i++) {
  setTimeout(function(j) {
    console.log(j); // Prints: 1, 2, 3
  }, i * 1000, i);
}
```

---

## 14. this Keyword

**`this`** refers to the object that is executing the current function. Its value depends on **how the function is called**.

### Global Context

```javascript
console.log(this); // Window (browser) or global (Node.js)

function showThis() {
  console.log(this);
}

showThis(); // Window (non-strict) or undefined (strict mode)

"use strict";
function strictThis() {
  console.log(this); // undefined
}
strictThis();
```

### Object Method

```javascript
let person = {
  name: "John",
  greet: function() {
    console.log(this); // person object
    console.log(this.name); // "John"
  },
  
  // Method shorthand (ES6)
  sayHi() {
    console.log(this.name);
  }
};

person.greet(); // this = person

// ⚠️ Losing context
let greetFunc = person.greet;
greetFunc(); // this = window/undefined (not person!)
```

### Constructor Function

```javascript
function Person(name, age) {
  this.name = name;
  this.age = age;
  
  this.greet = function() {
    console.log(`Hi, I'm ${this.name}`);
  };
}

let john = new Person("John", 30);
john.greet(); // this = john instance

// What 'new' does:
// 1. Creates empty object: {}
// 2. Sets this = that object
// 3. Sets object.__proto__ = Person.prototype
// 4. Returns this (unless constructor returns object)
```

### Arrow Functions

Arrow functions **don't have their own `this`**. They inherit `this` from the enclosing lexical context.

```javascript
let person = {
  name: "John",
  
  regularFunc: function() {
    console.log(this.name); // "John"
    
    setTimeout(function() {
      console.log(this.name); // undefined (this = window)
    }, 100);
  },
  
  arrowFunc: function() {
    console.log(this.name); // "John"
    
    setTimeout(() => {
      console.log(this.name); // "John" (inherits this from arrowFunc)
    }, 100);
  }
};

person.regularFunc();
person.arrowFunc();

// ⚠️ Arrow function as method
let obj = {
  name: "Jane",
  greet: () => {
    console.log(this.name); // undefined (this = window, not obj)
  }
};

obj.greet();

// ✅ Use regular function for methods
let obj2 = {
  name: "Jane",
  greet() {
    console.log(this.name); // "Jane"
  }
};
```

### Event Handlers

```javascript
// DOM event
button.addEventListener('click', function() {
  console.log(this); // button element
});

// Arrow function in event
button.addEventListener('click', () => {
  console.log(this); // window (not button)
});

// React class component
class MyComponent extends React.Component {
  handleClick() {
    console.log(this); // undefined (unless bound)
  }
  
  handleClickArrow = () => {
    console.log(this); // component instance
  }
  
  render() {
    return (
      <>
        <button onClick={this.handleClick}>Wrong</button>
        <button onClick={this.handleClick.bind(this)}>Correct</button>
        <button onClick={this.handleClickArrow}>Also Correct</button>
      </>
    );
  }
}
```

### Explicit Binding (call, apply, bind)

Covered in detail in section 15.

```javascript
function greet() {
  console.log(`Hi, I'm ${this.name}`);
}

let person = { name: "John" };

greet.call(person);  // "Hi, I'm John"
greet.apply(person); // "Hi, I'm John"

let boundGreet = greet.bind(person);
boundGreet(); // "Hi, I'm John"
```

---

## 15. call, apply, bind

These methods allow you to set the `this` value explicitly and borrow methods from other objects.

### call()

Calls a function with a given `this` value and arguments provided **individually**.

```js
function greet(greeting, punctuation) {
  console.log(`${greeting}, I'm ${this.name}${punctuation}`);
}

let person = { name: "John" };

greet.call(person, "Hello", "!"); // "Hello, I'm John!"

// Borrowing methods
let person1 = {
  name: "John",
  greet() {
    console.log(`Hi, I'm ${this.name}`);
  }
};

let person2 = { name: "Jane" };

person1.greet.call(person2); // "Hi, I'm Jane"

// Array-like to Array conversion
function toArray() {
  return Array.prototype.slice.call(arguments);
}

toArray(1, 2, 3); // [1, 2, 3]
```

### apply()

Same as `call()`, but arguments provided as an **array**.

```javascript
function greet(greeting, punctuation) {
  console.log(`${greeting}, I'm ${this.name}${punctuation}`);
}

let person = { name: "John" };

greet.apply(person, ["Hello", "!"]); // "Hello, I'm John!"

// Math.max with apply
let numbers = [1, 5, 3, 9, 2];
Math.max.apply(null, numbers); // 9

// Modern alternative: spread
Math.max(...numbers); // 9

// Finding max in array of objects
let people = [
  { name: "John", age: 30 },
  { name: "Jane", age: 25 },
  { name: "Bob", age: 35 }
];

let ages = people.map(p => p.age);
Math.max.apply(null, ages); // 35
```

### bind()

Returns a **new function** with `this` bound to the provided value. Doesn't execute immediately.

```
function greet(greeting, punctuation) {
  console.log(`${greeting}, I'm ${this.name}${punctuation}`);
}

let person = { name: "John" };

let boundGreet = greet.bind(person);
boundGreet("Hello", "!"); // "Hello, I'm John!"

// Partial application (currying)
let greetJohn = greet.bind(person, "Hello");
greetJohn("!"); // "Hello, I'm John!"
greetJohn("?"); // "Hello, I'm John?"

// Event handlers
let user = {
  name: "John",
  handleClick: function() {
    console.log(`${this.name} clicked`);
  }
};

// ❌ Wrong: loses context
button.addEventListener('click', user.handleClick);

// ✅ Correct: bind context
button.addEventListener('click', user.handleClick.bind(user));

// React class components
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.handleClick = this.handleClick.bind(this);
  }
  
  handleClick() {
    console.log(this.props);
  }
  
  render() {
    return <button onClick={this.handleClick}>Click</button>;
  }
}

// setTimeout context
let person = {
  name: "John",
  greet() {
    setTimeout(function() {
      console.log(this.name); // undefined
    }, 100);
  },
  
  greetBound() {
    setTimeout(function() {
      console.log(this.name); // "John"
    }.bind(this), 100);
  },
  
  greetArrow() {
    setTimeout(() => {
      console.log(this.name); // "John"
    }, 100);
  }
};
```

### Comparison

```javascript
let person = {
  name: "John",
  age: 30
};

function introduce(greeting, city) {
  console.log(`${greeting}, I'm ${this.name}, ${this.age} years old, from ${city}`);
}

// call - execute immediately, args individually
introduce.call(person, "Hello", "NYC");
// "Hello, I'm John, 30 years old, from NYC"

// apply - execute immediately, args as array
introduce.apply(person, ["Hi", "LA"]);
// "Hi, I'm John, 30 years old, from LA"

// bind - returns function, can be called later
let boundIntroduce = introduce.bind(person, "Hey");
boundIntroduce("Chicago");
// "Hey, I'm John, 30 years old, from Chicago"
```

### Interview Question: Implement bind()

```javascript
Function.prototype.myBind = function(context, ...args) {
  let fn = this;
  
  return function(...newArgs) {
    return fn.apply(context, [...args, ...newArgs]);
  };
};

// Usage
function greet(greeting, punctuation) {
  console.log(`${greeting}, I'm ${this.name}${punctuation}`);
}

let person = { name: "John" };
let boundGreet = greet.myBind(person, "Hello");
boundGreet("!"); // "Hello, I'm John!"
```

---

## 16. Prototypes & Inheritance

### Prototype Chain

Every JavaScript object has an internal `[[Prototype]]` property (accessible via `__proto__` or `Object.getPrototypeOf()`).

```javascript
// Every object has a prototype
let obj = {};
console.log(obj.__proto__ ===
```
----

---

## 17. ES6+ Features

Modern JavaScript introduced powerful features to write cleaner, faster, and more maintainable code.

### Key Concepts Covered:
- `let` & `const`
- Arrow functions
- Template literals
- Destructuring
- Spread & Rest operators
- Default parameters
- Modules (`import/export`)
- Optional chaining
- Nullish coalescing

```js
const user = { name: "Alex", age: 25 };

const greet = ({ name }) => `Hello ${name}!`;

const numbers = [1, 2, 3];
const newNumbers = [...numbers, 4];

console.log(greet(user));
```

### Why It Matters:
ES6+ is the industry standard. Most modern frameworks like React rely heavily on these features.

---

## 18. Asynchronous JavaScript

Handles operations that take time such as API calls, file loading, and timers without blocking execution.

### Key Concepts Covered:
- Callbacks
- Promises
- `async/await`
- Chaining promises
- Error handling in async code

 ```js

  function fetchData() {
  return new Promise(resolve => {
    setTimeout(() => resolve("Data loaded"), 1000)
  })
}

async function loadData() {
  const result = await fetchData();
  console.log(result);
}

loadData();

```

### Why It Matters:
Async programming is essential for building fast, responsive web applications.

---

## 19. Event Loop

The JavaScript engine mechanism that manages asynchronous tasks.

### Key Concepts Covered:
- Call Stack
- Web APIs
- Callback Queue
- Microtask Queue
- Promise execution

```js
console.log("Start");

setTimeout(() => {
  console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
  console.log("Promise");
});

console.log("End");

// Start → End → Promise → Timeout

```

### Why It Matters:
Understanding the event loop helps debug async behavior and write optimized code.

---

## 20. Error Handling

Techniques to handle runtime issues gracefully.

### Key Concepts Covered:
- `try...catch`
- `finally`
- Custom errors
- Promise error handling
- Debugging best practices

```
try {
  const data = JSON.parse("invalid json");
} catch (error) {
  console.error("Something went wrong:", error.message);
} finally {
  console.log("Execution completed");
}

```
### Why It Matters:
Proper error handling prevents crashes and improves user experience.

---

## 21. DOM Manipulation

Interact with and update HTML elements dynamically using JavaScript.

### Key Concepts Covered:
- Selecting elements
- Creating/removing nodes
- Event listeners
- Class & style updates
- Form handling
```
const button = document.querySelector("button");

button.addEventListener("click", () => {
  document.body.style.background = "lightblue";
});

```

### Why It Matters:
DOM manipulation powers interactive web applications.

---

## 22. Web Storage

Store data in the browser for persistence.

### Key Concepts Covered:
- `localStorage`
- `sessionStorage`
- Storing objects
- Retrieving & deleting data
- Use cases

```
localStorage.setItem("user", JSON.stringify({ name: "Alex" }));

const user = JSON.parse(localStorage.getItem("user"));
console.log(user.name);

```
### Why It Matters:
Used for saving user preferences, auth tokens, and app state.

---

## 23. Modules

Organize JavaScript code into reusable files.

### Key Concepts Covered:
- `export` / `import`
- Named vs default exports
- Module scope
- Code reusability
```
//  - named export - 
//  math.js
export function add(a, b) {
  return a + b;
}

// main.js
import { add } from "./math.js";
console.log(add(2, 3));

```
### Why It Matters:
Modules keep code clean, scalable, and maintainable.

---

## 24. API & Fetch

Communicating with backend services and external APIs.

### Key Concepts Covered:
- HTTP methods (GET, POST, PUT, DELETE)
- Fetch API
- Handling JSON
- Error responses
- Loading states
```
async function getUsers() {
  const response = await fetch("https://api.example.com/users");
  const data = await response.json();
  console.log(data);
}

getUsers();

```
### Why It Matters:
APIs power real-world applications, like dashboards, e-commerce, and authentication.

---

## 25. Common Interview Questions

A curated set of frequently asked JavaScript interview questions with explanations.

### Topics Include:
- Closures & hoisting
- Event loop behavior
- `this` keyword
- Promise vs async/await
- Shallow vs deep copy
- Var vs let vs const
- Array & object tricks
```
// Clousers Example 
function outer() {
  let count = 0;

  return function inner() {
    count++;
    return count;
  };
}

const counter = outer();
console.log(counter());
console.log(counter());

```
### Why It Matters:
Strengthens conceptual clarity and boosts interview confidence.

---

## 📌 Project Goals

- Master JavaScript from beginner to advanced level  
- Understand how JavaScript works behind the scenes  
- Write clean, modern, and efficient code  
- Be fully prepared for technical interviews  

---

## 📚 Recommended Usage

1. Study topics in order  
2. Practice each concept with code  
3. Review interview questions regularly  
4. Build mini-projects using learned concepts  

---

## 📈 Future Enhancements

- Advanced performance optimization  
- Real-world project examples  
- System design basics for frontend  
- Testing with Jest  
----

### Happy Coding! 🚀
