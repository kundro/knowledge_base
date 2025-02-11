**JavaScript / TypeScript / Node.js**

### **Node.js Overview**
💡 **Node.js** is a runtime that allows JavaScript to run outside the browser. It is mainly used for backend (server-side) applications.
- **Asynchronous** – Handles multiple requests at the same time.
- **Event-driven** – Performs actions based on events like user requests.
- **Uses V8 engine** – The same JavaScript engine as Chrome.
- **Non-blocking I/O** – Ideal for operations like database calls.
- **Single-threaded** – Efficient for real-time applications.
- **NPM (Node Package Manager)** – Manages dependencies and libraries.

### **Event Loop in Node.js**
💡 The **Event Loop** is what makes Node.js **non-blocking**.
**How it works:**
1. **Receives** a request.
2. **Sends** it to the correct handler (file system, database, etc.).
3. **Moves** to the next request (doesn’t wait).
4. **When the operation finishes**, it sends the response.

📌 This method allows multiple requests to be processed **without waiting**.

### **Event Loop in JavaScript**
JavaScript is **single-threaded** but can handle multiple tasks using the **event loop**.
```js
console.log("Start");
setTimeout(() => {
   console.log("Delayed Message");
}, 1000);
console.log("End");
```
📌 JavaScript uses an event loop to handle **asynchronous** tasks like `setTimeout` and **Promises**.

### **Callbacks**
💡 A **callback** is a function passed as an argument to another function.
```js
const fs = require('fs');
fs.readFile('file.txt', 'utf8', (err, data) => {
   if (err) throw err;
   console.log(data);
});
```
📌 Instead of waiting, the program moves to the next task and runs the **callback** when the file is **ready**.

### **Promises**
💡 **Promises** provide a better way to handle **asynchronous** code.
**Promise states:**
- **Pending** – Waiting for the result.
- **Resolved (Fulfilled)** – Success.
- **Rejected** – Error happened.
```js
const fs = require('fs').promises;
fs.readFile('file.txt', 'utf8')
   .then(data => console.log(data))
   .catch(err => console.error(err));
```
📌 **Promises avoid callback hell** and make asynchronous code easier to read.

### **async/await**
💡 **async/await** is a cleaner way to write **Promises**.
```js
async function readFile() {
   try {
      const data = await fs.readFile('file.txt', 'utf8');
      console.log(data);
   } catch (err) {
      console.error(err);
   }
}
readFile();
```
📌 **Makes async code look like synchronous code.**

### **process in Node.js**
💡 `process` is a **global object** that gives information about the Node.js **environment**.
```js
console.log(process.env.NODE_ENV); // Shows environment variable
console.log(process.argv); // Shows command-line arguments
```
📌 Useful for handling **environment settings** and **configurations**.

### **Error Handling**
💡 Use `try-catch` for **synchronous** code and `.catch()` for **Promises**.
```js
try {
   throw new Error("Something went wrong");
} catch (error) {
   console.error(error.message);
}
```
📌 **Handling errors properly prevents app crashes.**

### **Loops in JavaScript**
💡 Loops are used to **repeat a block** of code multiple times.
- `for` – Runs a fixed number of times.
- `while` – Runs as long as a condition is true.
- `do...while` – Runs at least once, then checks the condition.
- `forEach` – Used for arrays.
```js
for (let i = 0; i < 5; i++) {
   console.log(i); // Prints 0, 1, 2, 3, 4
}
```

### **setTimeout & setInterval (Async Basics)**
💡 Both are used to **run code later** after some time.
```js
setTimeout(() => console.log("Hello after 2 seconds"), 2000);
setInterval(() => console.log("Repeating every 3 seconds"), 3000);
```

### **Difference between var, let, and const**
💡 `var` has **function scope**, while `let` and `const` have **block scope**.
📌 `const` **cannot be reassigned** after declaration.

### **Difference between == and ===**
💡 `==` **checks only value**, while `===` **checks both value and type**.

### **JavaScript vs TypeScript**
| Feature | JavaScript | TypeScript |
|---------|------------|------------|
| **Type System** | Dynamic (no type checking) | Static (types checked at compile time) |
| **OOP Features** | ES6+ based | Supports interfaces, abstract classes, access modifiers (public, private, protected) |

📌 **JavaScript is dynamic**, while **TypeScript** provides **better structure** and **type safety**.

---
🚀 **JavaScript is the foundation of web development. Node.js enables backend capabilities, and TypeScript improves code quality.**

