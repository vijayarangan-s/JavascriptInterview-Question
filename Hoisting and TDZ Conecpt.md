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

---

The Temporal Dead Zone (TDZ) is a crucial concept related to variable declarations with `let` and `const` in JavaScript, often tested in interviews to check the candidate's understanding of ES6 scope and hoisting behavior. Here are some common TDZ-related interview questions, along with answers and explanations.

---

### 1. **What is the Temporal Dead Zone (TDZ) in JavaScript?**

**Answer:**
The Temporal Dead Zone (TDZ) is the time between entering a block scope and the actual declaration of variables with `let` or `const`. During this period, accessing the variable before its declaration results in a `ReferenceError`.

**Explanation:**
When JavaScript encounters a `let` or `const` declaration, the variable is hoisted to the top of its scope but is uninitialized until the declaration line. Accessing it before this point triggers the TDZ, where the variable is considered to exist but is unusable.

---

### 2. **What will be the output of the following code, and why?**

```javascript
console.log(a);  // ?
let a = 5;
```

**Answer:**
The output will be a `ReferenceError: Cannot access 'a' before initialization`.

**Explanation:**
Here, `a` is in the TDZ from the start of the block until the line `let a = 5;`. Attempting to access `a` before it is declared results in a `ReferenceError`.

---

### 3. **How does the TDZ affect variable declarations with `var`, `let`, and `const`?**

**Answer:**
- **`var`**: Variables declared with `var` are hoisted and initialized with `undefined`, so there is no TDZ. Accessing a `var` variable before its declaration results in `undefined`, not an error.
- **`let` and `const`**: Both are hoisted but uninitialized until the declaration is encountered. Accessing them before declaration results in a `ReferenceError` due to the TDZ.

---

### 4. **What will be the output of the following code?**

```javascript
{
  console.log(b);  // ?
  let b = 10;
}
```

**Answer:**
The output will be a `ReferenceError: Cannot access 'b' before initialization`.

**Explanation:**
Since `b` is declared with `let`, it is hoisted but not initialized until the declaration is reached. Accessing `b` before its declaration in the block scope results in a TDZ error.

---

### 5. **Explain the difference in behavior between `var`, `let`, and `const` within a block scope in terms of TDZ.**

**Answer:**
- `var` declarations are hoisted to the top of the function or global scope and initialized to `undefined`, so there is no TDZ.
- `let` and `const` declarations are hoisted but uninitialized, creating a TDZ from the beginning of the block until the line where they are declared.
- Accessing `let` or `const` variables within their TDZ results in a `ReferenceError`.

---

### 6. **How can you avoid TDZ-related errors in your code?**

**Answer:**
To avoid TDZ errors:
1. Always declare `let` and `const` variables at the beginning of their scope.
2. Avoid accessing `let` or `const` variables before their declaration line.
3. If a variable might need to be accessed before initialization, consider using `var`, or review the code flow to ensure TDZ errors won’t occur.

---

### 7. **What will be the output of this code?**

```javascript
let x = 5;
{
  console.log(x);  // ?
  let x = 10;
}
```

**Answer:**
The output will be a `ReferenceError: Cannot access 'x' before initialization`.

**Explanation:**
The block-scoped `let x = 10;` creates a new `x` within the block. Due to the TDZ, `x` is not accessible before its declaration within the block, resulting in a `ReferenceError` on `console.log(x)`.

