# JavaScript Data Types

## What is a Data Type?

In programming, a data type tells us what kind of value a variable holds. It helps the computer understand how to store that value in memory and what operations can be performed on it. JavaScript is a flexible language; it figures out the data type of a variable as your code runs, based on the value you assign.

---

## Key Distinctions: Primitive vs. Non-Primitive (Object)

JavaScript's data types are divided into two main categories, primarily based on whether their values can be changed and how they are stored in memory.

### Mutable vs. Immutable

- **Immutable:**  
  A value is immutable if it cannot be changed after it's created. Any operation that seems to modify an immutable value will instead produce a new value, leaving the original unchanged. In JavaScript, all primitive data types are immutable.

- **Mutable:**  
  A value is mutable if it can be changed after it's created. You can directly modify its contents, properties, or elements without creating a new value. In JavaScript, the Object data type (and all its variants like Arrays, Functions, etc.) is mutable.

---

## 1. Primitive Types

JavaScript has seven primitive data types. The most important thing to remember about primitive values is that they are immutable. This means that once you create a primitive value (like a number or a string), its content cannot be changed. If you perform an operation that seems to change it (like making a string uppercase), JavaScript actually creates a brand new value, leaving the original untouched. Primitive values are stored directly in a simple way in memory.

### The Primitive Types Are:

### 1. **String**  
Textual data.

```js
let greeting = "Hello World";
let language = 'JavaScript';
let template = `Hello from ${language}!`;
console.log(greeting); // "Hello World"
console.log(language); // "JavaScript"
console.log(template); // "Hello from JavaScript!"
```

---

### 2. **Number**  
Both whole numbers and numbers with decimal points.

```js
let integer = 10;
let decimal = 3.14;
let negative = -5;
let bigNum = 1.7976931348623157e+308; // Maximum representable number
let notANumber = NaN; // Result of an undefined or unrepresentable numeric operation
console.log(integer); // 10
console.log(decimal); // 3.14
console.log(negative); // -5
console.log(typeof notANumber); // "number"
```

---

### 3. **BigInt**  
Very large whole numbers that the standard Number type can't handle accurately.

```js
let largeNumber = 9007199254740991n; // The 'n' at the end makes it a BigInt
let anotherBigInt = BigInt("123456789012345678901234567890");
console.log(largeNumber); // 9007199254740991n
console.log(anotherBigInt); // 123456789012345678901234567890n
```

---

### 4. **Boolean**  
Represents truth or falsehood. Only two possible values.

```js
let isActive = true;
let hasPermission = false;
let isGreater = (10 > 5); // true
console.log(isActive); // true
console.log(hasPermission); // false
console.log(isGreater); // true
```

---

### 5. **Undefined**  
A variable that has been declared but hasn't been given a value yet.

```js
let x;
console.log(x); // undefined

function doNothing() {
    // This function doesn't explicitly return anything
}
let result = doNothing();
console.log(result); // undefined
```

---

### 6. **Symbol**  
A unique and immutable value, often used as a unique identifier.

```js
const id1 = Symbol('myId');
const id2 = Symbol('myId');
console.log(id1 === id2); // false (they are unique)

let obj = {
    [id1]: "This is unique data"
};
console.log(obj[id1]); // "This is unique data"
```

---

### 7. **Null**  
Represents the intentional absence of any object value. It's a primitive value.

```js
let data = null;
console.log(data); // null
console.log(typeof data); // "object" (a historical quirk, but it's primitive)

let user = { name: "John", email: null }; // Email intentionally absent
console.log(user.email); // null
```

---

## 2. Non-Primitive Type (Object)

The Object is the only non-primitive data type in JavaScript. Unlike primitive values, objects are mutable. This means their contents (properties and values) can be changed after they are created. Objects are stored differently in memory; variables don't hold the object itself, but rather a "reference" (like a pointer) to where the object is stored. This means if you have multiple variables pointing to the same object, changing the object through one variable will affect all others. Objects are typically stored in a more complex memory area called the heap.

### The Object data type includes various specialized forms:

#### **Plain Objects (Object Literals)**
A collection of key-value pairs (like a dictionary).

```js
const person = {
    name: "Alice",
    age: 30,
    city: "New York"
};
console.log(person.name); // "Alice"
person.age = 31; // Modifying a property
person.occupation = "Engineer"; // Adding a new property
console.log(person); // { name: "Alice", age: 31, city: "New York", occupation: "Engineer" }
```

---

#### **Functions**
Blocks of code designed to perform specific tasks. Functions are also objects in JavaScript.

```js
function greet(name) {
    return `Hello, ${name}!`;
}

const add = (a, b) => a + b; // Arrow function

console.log(greet("Bob")); // "Hello, Bob!"
console.log(add(5, 3)); // 8
```

---

#### **Arrays**
Ordered lists of values.

```js
const colors = ["red", "green", "blue"];
const numbers = [1, 2, 3, 4, 5];
console.log(colors[0]); // "red"
numbers.push(6); // Add an element
console.log(numbers); // [1, 2, 3, 4, 5, 6]
```

---

#### **Dates**
Objects representing specific points in time.

```js
const now = new Date();
console.log(now); // Current date and time

const christmas = new Date('2025-12-25T00:00:00Z');
console.log(christmas.getFullYear()); // 2025
```

---

#### **Maps**
Collections of key-value pairs, similar to plain objects, but with more flexible keys (any data type can be a key).

```js
const userRoles = new Map();
userRoles.set('admin', 'John Doe');
userRoles.set(101, 'Jane Smith'); // Key can be a number
console.log(userRoles.get('admin')); // "John Doe"
console.log(userRoles.has(101)); // true
```

---

#### **Sets**
Collections of unique values. Duplicate values are automatically ignored.

```js
const uniqueNumbers = new Set([1, 2, 2, 3, 4, 4]);
console.log(uniqueNumbers); // Set {1, 2, 3, 4} (duplicates removed)
uniqueNumbers.add(5);
console.log(uniqueNumbers.has(3)); // true
```

---

#### **RegExp (Regular Expression)**
Objects used for pattern matching with text.

```js
const pattern = /hello/i; // Matches "hello" case-insensitively
const text1 = "Hello World";
const text2 = "Hi there";

console.log(pattern.test(text1)); // true (pattern found)
console.log(pattern.test(text2)); // false (pattern not found)

const emailPattern = /\S+@\S+\.\S+/; // Simple email pattern
console.log(emailPattern.test("test@example.com")); // true
```

---

## Summary: Primitive vs. Non-Primitive Data Types

Here's a quick comparison of the key differences:

| Feature         | Primitive Types                       | Non-Primitive Types (Objects)                |
|-----------------|--------------------------------------|----------------------------------------------|
| Mutability      | Immutable (cannot be changed)         | Mutable (can be changed)                     |
| Storage         | Stored by value (direct copy)         | Stored by reference (pointer to memory)      |
| Memory          | Typically stored in the Call Stack    | Typically stored in the Heap                 |
| Comparison      | Compared by value                     | Compared by reference                        |
| Examples        | String, Number, BigInt, Boolean, Undefined, Symbol, Null | Plain Objects, Functions, Arrays, Dates, Maps, Sets, RegExp |
| Default Value   | `undefined` (for declared but unassigned variables) | `null` (often used to explicitly signify no object) |

---

In essence, JavaScript's data types boil down to two core ideas: primitive values (which are fixed and cannot be changed) and objects (which are flexible and can be modified). Understanding this difference is fundamental for writing effective JavaScript code.