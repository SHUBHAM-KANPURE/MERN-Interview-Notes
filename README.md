# Welcome To The MERN Interview Channel

## JavaScript (Core + Advanced)

### Q.1 Difference between var, let, and const
#### 1. Var
   
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

**Definition:** `let` is block-scoped. It can be updated but not re-declared in the same scope. Hoisted but not accessible

**Example:**
```js
let y = 10;
y = 20;     // allowed
// let y = 30; ❌ not allowed in same scope

console.log(y); // 20
```
---
