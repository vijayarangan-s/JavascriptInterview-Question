Hoisting is a common topic in JavaScript interviews, especially when discussing variable declarations, function declarations, and scope. Here are some potential interview questions on hoisting along with answers and explanations.

---

### 1. **What is hoisting in JavaScript?**

**Answer:**
Hoisting is JavaScript's default behavior of moving declarations (variable and function declarations) to the top of their containing scope (function or global scope) before the code executes. This means that you can use variables and functions before they are declared.

**Explanation:**
During the compilation phase, JavaScript "hoists" declarations to the top of their scope. However, only the declarations are hoisted, not the initializations.

---

### 2. **What will be the output of the following code, and why?**

```javascript
console.log(x);
var x = 5;
```

**Answer:**
The output will be `undefined`.

**Explanation:**
Due to hoisting, the declaration `var x` is moved to the top, but not the initialization. So the code effectively becomes:

```javascript
var x;
console.log(x);  // undefined
x = 5;
```

---

### 3. **How does hoisting work with `let` and `const`?**

**Answer:**
Variables declared with `let` and `const` are also hoisted, but they are not initialized. They remain in a "temporal dead zone" (TDZ) from the start of the block until the declaration is encountered. Accessing them before declaration results in a `ReferenceError`.

**Example:**

```javascript
console.log(a);  // ReferenceError: Cannot access 'a' before initialization
let a = 10;
```

---

### 4. **What will be the output of the following code?**

```javascript
var y = 10;

function test() {
  console.log(y);
  var y = 5;
}

test();
```

**Answer:**
The output will be `undefined`.

**Explanation:**
Inside the function, `var y` is hoisted to the top of the `test` function's scope, so it shadows the global variable `y`. The function becomes:

```javascript
function test() {
  var y;  // y is hoisted and declared at the top, but not initialized
  console.log(y);  // undefined
  y = 5;
}
```

---

### 5. **Explain hoisting behavior with function declarations and function expressions.**

**Answer:**
- **Function Declarations**: These are fully hoisted, meaning both the declaration and the function definition are moved to the top of the scope. This allows you to call the function even before its declaration in the code.

    ```javascript
    greet();  // Output: Hello!
    function greet() {
      console.log("Hello!");
    }
    ```

- **Function Expressions**: Only the variable declaration is hoisted, not the function itself. If you try to call a function expression before it is defined, you will get `undefined` or an error (depending on whether `var`, `let`, or `const` is used).

    ```javascript
    console.log(greet);  // Output: undefined
    var greet = function() {
      console.log("Hello!");
    };
    ```

---

### 6. **What will be the output of the following code, and why?**

```javascript
console.log(foo);  // ?
foo();

var foo = function() {
  console.log("Hello");
};
```

**Answer:**
The output will be:

```
undefined
TypeError: foo is not a function
```

**Explanation:**
1. `var foo` is hoisted, so `console.log(foo);` prints `undefined`.
2. `foo()` throws an error because `foo` is still `undefined` at the time of the function call.

