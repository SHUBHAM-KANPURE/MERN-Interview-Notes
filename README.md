# Welcome To The MERN Interview Channel

## JavaScript (Core + Advanced)

### Q. Difference between var, let, and const

Definition:
* Var
var is a function-scoped variable. It can be re-declared and updated and is hoisted with undefined.

Example:

```js
var x = 10;
var x = 20; // allowed
x = 30;     // allowed

console.log(x); // 30
