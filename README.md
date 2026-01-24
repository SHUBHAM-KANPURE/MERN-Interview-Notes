# Welcome To The MERN Interview Channel

## -> JavaScript (Core + Advanced)

### Q.1 Difference between var, let, and const
#### 1. var
   
**Definition:** `var` is a function-scoped variable. It can be re-declared and updated and is hoisted with undefined.

**Example:**
```js
var x = 10;
var x = 20; // allowed
x = 30;     // allowed

console.log(x); // 30
```
---

#### 2. let

**Definition:** `let` is block-scoped. It can be updated but not re-declared in the same scope. Hoisted but not accessible before declaration.

**Example:**
```js
let y = 10;
y = 20;     // allowed
// let y = 30; not allowed in same scope

console.log(y); // 20
```
---

#### 3. const

**Definition:** `const` is block-scoped and cannot be re-declared or updated. Value must be assigned at declaration.

**Example:**
```js
const z = 10;
// z = 20; not allowed

const obj = { name: "Shubham" };
obj.name = "Shivam"; // allowed (object mutation)

```
---

### Q.2 Explain hoisting with example

**Definition:** `Hoisting` is JavaScript’s behavior where variable and function declarations are moved to the top of their scope during compilation, before code execution.

**Example:**
```js
console.log(a); // undefined
var a = 10;
```
---
---

## -> Node.js

### Q.1 What is Node.js and why is it fast?
**Definition:** `Node.js` is a JavaScript runtime environment built on Chrome’s V8 engine that allows JavaScript to run outside the browser, mainly on the server side.

