# The Foundations : Identifiers, Variables, Constants, and Comments

---

## Identifiers: Naming Your Code Elements

Identifiers are the labels used to name various parts of JavaScript code. Think of them as unique names for variables, functions, arrays, objects, and classes.

### Key Characteristics

- **Case-Sensitive:**  
  JavaScript treats `value` and `Value` as completely different identifiers. This is a common source of bugs for beginners, so always be mindful of your casing.

- **Meaningful & Descriptive:**  
  While not enforced, choosing names that clearly indicate their purpose (e.g., `userName` instead of `u`) makes code much easier to read and maintain.

### Rules for Valid Identifiers

Here are the strict rules for what should and should not be an identifier in JavaScript, along with examples:

- **Should Not Start with a Number:**
  - ❌ `var 1name = "John";` (Invalid: starts with a number)
  - ✅ `var name1 = "John";` (Valid: ends with a number)

- **Should Not Contain Spaces:**
  - ❌ `var full name = "John";` (Invalid: contains a space)
  - ✅ `var full_name = "John";` (Valid: uses an underscore)

- **Allowed Characters:**  
  Identifiers may only contain:
  - Letters (A-Z, a-z)
  - Digits (0-9) (but not as the first character)
  - Dollar signs ($)
  - Underscores (_)
  - ❌ `var user-name = "Manny";` (Invalid: hyphen not allowed)
  - ✅ `var user$name = "Manny";` (Valid: dollar sign allowed)
  - ✅ `var user_name = "Manny";` (Valid: underscore allowed)

- **Should Not Use JavaScript Reserved Keywords:**  
  Reserved words in JavaScript (such as `function`, `if`, `for`, `var`, `let`, `const`, etc.) should not be used as identifiers.
  - ❌ `var function = "doSomething";` (Invalid: 'function' is reserved)
  - ✅ `var myFunction = "doSomething";` (Valid)

> **Best Practice:**  
> Use descriptive and meaningful names for identifiers. Avoid single-letter names except for counters or iterators in small scopes.

### Case Sensitivity in Action

```js
var city = "Delhi";
var City = "Mumbai";
console.log(city);   // Output: Delhi
console.log(City);   // Output: Mumbai
```

### Meaningful Names (Recommendation)

- ✅ `var a = 100;` (Valid but not meaningful)
- ✅ `var studentMarks = 100;` (Valid and highly recommended for clarity)

### Naming Convention: camelCase

For variable names, the universally recommended convention in JavaScript is camelCase. This means the first letter of the first word is lowercase, and the first letter of each subsequent word is uppercase.

- ✅ `var accountBalance = 3000;` (Recommended)
- ✅ `var account_balance = 3000;` (Valid, but not standard for variables in JS)

> **Note:**  
> Use camelCase for variables and functions. Use PascalCase (e.g., `MyClass`) for class names.

---

## Variables: Containers for Your Data

Variables are essentially named storage locations that hold values. These values can change over time as your program runs.

In modern JavaScript, we declare variables using either `let` or `var`. While `var` is the older way, `let` (introduced in ES6) is generally preferred due to its improved scoping.

```js
var userName = "Manideep";
let age = 25;
```

### Declaring Variables

You have flexibility when declaring variables:

- **Declare and Assign Later:**
  ```js
  let productName;     // Declared
  productName = "Laptop"; // Assigned a value later
  ```

- **Declare and Assign Immediately:**
  ```js
  let price = 59999; // Declared and initialized
  ```

---

## var vs. let: Understanding the Differences

The choice between `var` and `let` has significant implications for how your variables behave, especially concerning scope and redeclaration.

| Feature                | var                        | let                                         |
|------------------------|----------------------------|---------------------------------------------|
| Scope                  | Function-scoped            | Block-scoped                                |
| Redeclaration Allowed  | ✅ Yes                     | ❌ No (SyntaxError if you try)              |
| Hoisting               | ✅ Yes (initialized to `undefined`) | ✅ Yes (but in a Temporal Dead Zone until declared) |
| Access Before Init     | ✅ Allowed (`undefined`)   | ❌ ReferenceError (due to Temporal Dead Zone)|
| Reassignment           | ✅ Yes                     | ✅ Yes                                      |
| Global Object Binding  | ✅ Yes (adds property to `window` object) | ❌ No (not added to `window` object)        |

---

### 🚀 Examples of var vs. let Behavior

#### Example 1: Scope Difference

- `var` is function-scoped, meaning it's accessible anywhere within the function it's declared in, even outside of if blocks or loops.
- `let` is block-scoped, meaning it's only accessible within the specific block (`{ }`) where it's defined.

```js
function testVar() {
  if (true) {
    var a = 10; // 'a' is function-scoped
  }
  console.log(a); // Output: 10 (Accessible because 'a' is scoped to `testVar` function)
}
testVar();

function testLet() {
  if (true) {
    let b = 20; // 'b' is block-scoped
  }
  // console.log(b); // ❌ ReferenceError: b is not defined (Not accessible outside the 'if' block)
}
testLet(); // This will throw an error if the console.log(b) line is uncommented
```

#### Example 2: Redeclaration

- `var` lets you declare the same variable multiple times in the same scope without error, overwriting the previous value.
- `let` prevents this, which helps catch accidental redeclarations.

```js
// var allows redeclaration - NO ERROR
var course = "Math";
var course = "Science"; // ✅ This is perfectly fine with 'var'
console.log(course);    // Output: Science

// let does not allow redeclaration - SYNTAXERROR
let subject = "Physics";
// let subject = "Chemistry"; // ❌ SyntaxError: Identifier 'subject' has already been declared
console.log(subject);     // Output: Physics (if the error line is commented out)
```

#### Example 3: Hoisting Behavior

Both `var` and `let` declarations are hoisted (their declaration is moved to the top of their scope). However, `var` variables are also initialized to `undefined` during hoisting, while `let` variables remain in a "temporal dead zone" until their actual declaration line is executed.

```js
console.log(x); // Output: undefined (declaration of 'x' is hoisted, but not its assignment)
var x = 5;
console.log(x); // Output: 5

// console.log(y); // ❌ ReferenceError: Cannot access 'y' before initialization
let y = 10;
console.log(y); // Output: 10 (if the error line is commented out)
```

#### Example 4: Global Object Property

When `var` variables are declared in the global scope, they become properties of the global `window` object (in browsers). `let` variables declared globally do not.

```js
var globalVar = 'hello';
let globalLet = 'hi';

console.log(window.globalVar); // Output: 'hello'
console.log(window.globalLet); // Output: undefined
```

#### Example 5: Reassignment

Both `var` and `let` variables can be reassigned to new values after their initial declaration. This is a common and intended behavior for variables.

```js
// Reassignment with 'var'
var counter = 1;
console.log(counter); // Output: 1
counter = 2;          // ✅ Value changed
console.log(counter); // Output: 2

// Reassignment with 'let'
let userName = "Alice";
console.log(userName); // Output: Alice
userName = "Bob";      // ✅ Value changed
console.log(userName); // Output: Bob
```

---

## Constants: Values That Don't Change

Constants are declared using the `const` keyword. Like `let`, they are block-scoped, but their defining characteristic is that they cannot be reassigned after their initial value is set. This makes them ideal for values that should remain fixed throughout your program.

```js
const PI = 3.14;
// PI = 3.1415; // ❌ TypeError: Assignment to constant variable (you cannot reassign a const)
console.log(PI); // Output: 3.14
```

You can use constants directly in expressions:

```js
const DISCOUNT = 0.2;
const price = 100;
console.log(price * (1 - DISCOUNT)); // Output: 80 (100 * (1 - 0.2) = 100 * 0.8)
```

> **Important Note:**  
> You must assign a value when you declare a `const` variable. It cannot be declared without an initializer.
>
> ```js
> // const total; // ❌ SyntaxError: Missing initializer in const declaration
> ```

---

## Comments: Explaining Your Code

Comments are ignored by the JavaScript engine but are invaluable for developers. They help you and others understand what your code does, why it does it, and how it works.

### Single-line Comments

Use `//` for comments that span a single line.

```js
// This is a single-line comment
let name = "Mani"; // You can also put them at the end of a line of code
```

**Editor Shortcut (VS Code):**  
- Ctrl + / (Windows/Linux)  
- Cmd + / (Mac)

### Multi-line or Block Comments

Use `/* ... */` for comments that extend across multiple lines.

```js
/*
  This is a multi-line comment.
  It's great for explaining complex logic,
  or for temporarily disabling a block of code.
*/
let age = 25;
```

**Editor Shortcut (VS Code):**  
- Shift + Alt + A (Windows/Linux)  
- Option + Shift + A (Mac)

---
