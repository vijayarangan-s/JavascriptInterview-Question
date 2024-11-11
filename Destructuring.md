Destructuring is a feature in JavaScript that allows you to unpack values from arrays or properties from objects into distinct variables. This feature is often tested in interviews to assess a candidate’s understanding of ES6 syntax and their ability to work efficiently with data structures. Here are some common destructuring interview questions with explanations and answers.

---

### 1. **What is destructuring in JavaScript?**

**Answer:**
Destructuring is a syntax in JavaScript that allows you to unpack values from arrays or properties from objects into distinct variables in a single, concise statement. This can simplify code and make it more readable.

**Example:**

```javascript
const person = { name: "John", age: 30 };
const { name, age } = person;
console.log(name); // "John"
console.log(age);  // 30
```

---

### 2. **How can you swap two variables using array destructuring?**

**Answer:**
Array destructuring provides a concise way to swap values between two variables.

**Example:**

```javascript
let a = 1;
let b = 2;

[a, b] = [b, a];

console.log(a); // 2
console.log(b); // 1
```

---

### 3. **What will be the output of the following code?**

```javascript
const numbers = [1, 2, 3];
const [first, , third] = numbers;

console.log(first); // ?
console.log(third); // ?
```

**Answer:**
The output will be:

```
1
3
```

**Explanation:**
Array destructuring allows you to skip elements by leaving empty spaces separated by commas. Here, `first` is assigned `1`, and `third` is assigned `3`, while the second element (`2`) is ignored.

---

### 4. **How would you use object destructuring with default values?**

**Answer:**
You can set default values when destructuring to ensure a variable has a value even if the property doesn’t exist on the object.

**Example:**

```javascript
const user = { name: "Alice" };
const { name, age = 25 } = user;

console.log(name); // "Alice"
console.log(age);  // 25
```

**Explanation:**
Here, `age` is not defined in `user`, so the default value of `25` is assigned to `age`.

---

### 5. **How would you rename variables when destructuring an object?**

**Answer:**
You can rename variables while destructuring by specifying a new variable name after a colon.

**Example:**

```javascript
const person = { firstName: "Jane", lastName: "Doe" };
const { firstName: first, lastName: last } = person;

console.log(first); // "Jane"
console.log(last);  // "Doe"
```

**Explanation:**
Here, `firstName` is assigned to `first` and `lastName` to `last`, so `first` and `last` are the variable names you can use.

---

### 6. **What will be the output of the following code, and why?**

```javascript
const person = { name: "John", age: 30 };
const { name, age, job = "Developer" } = person;

console.log(name); // ?
console.log(age);  // ?
console.log(job);  // ?
```

**Answer:**
The output will be:

```
John
30
Developer
```

**Explanation:**
Since `job` does not exist in the `person` object, the default value `"Developer"` is assigned to `job`.

---

### 7. **How can you use nested destructuring to extract values from nested objects?**

**Answer:**
You can destructure nested objects by following the object structure in your destructuring pattern.

**Example:**

```javascript
const employee = {
    name: "Alice",
    position: {
        title: "Engineer",
        department: "Development"
    }
};

const {
    name,
    position: { title, department }
} = employee;

console.log(name);       // "Alice"
console.log(title);      // "Engineer"
console.log(department); // "Development"
```

**Explanation:**
Here, `title` and `department` are extracted from the nested `position` object within `employee`.

---

### 8. **What will be the output of the following code, and why?**

```javascript
const colors = ["red", ["green", "blue"]];
const [primary, [secondary, tertiary]] = colors;

console.log(primary);   // ?
console.log(secondary); // ?
console.log(tertiary);  // ?
```

**Answer:**
The output will be:

```
red
green
blue
```

**Explanation:**
This is an example of nested array destructuring. `primary` is assigned `"red"`, `secondary` is assigned `"green"`, and `tertiary` is assigned `"blue"`.

---

### 9. **Can you combine object destructuring with rest syntax?**

**Answer:**
Yes, you can use the rest syntax (`...`) in object destructuring to collect remaining properties into a new object.

**Example:**

```javascript
const person = { name: "John", age: 30, city: "New York" };
const { name, ...rest } = person;

console.log(name); // "John"
console.log(rest); // { age: 30, city: "New York" }
```

**Explanation:**
Here, `name` is extracted, and `rest` collects the remaining properties, `age` and `city`, into a new object.

---

### 10. **How can you use destructuring in function parameters?**

**Answer:**
You can destructure an object directly in the function parameter list to simplify accessing object properties within the function.

**Example:**

```javascript
function printPerson({ name, age }) {
    console.log(`Name: ${name}`);
    console.log(`Age: ${age}`);
}

const person = { name: "Jane", age: 25 };
printPerson(person);
```

**Explanation:**
Here, `name` and `age` are destructured directly from the `person` object parameter, making the function more concise.
