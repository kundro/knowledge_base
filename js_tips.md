# JavaScript Quick Reference

1. **Array Methods**

🔹 `.map()` – Transforms each element and returns a new array.

```
const nums = [1, 2, 3];
const doubled = nums.map(num => num * 2);  // [2, 4, 6]
```

🔹 `.filter()` – Returns a new array with elements that meet a condition.

```
const nums = [1, 2, 3, 4];
const evens = nums.filter(num => num % 2 === 0);  // [2, 4]
```

🔹 `.reduce()` – Reduces an array to a single value (sum, product, etc.).

```
const nums = [1, 2, 3, 4];
const sum = nums.reduce((acc, num) => acc + num, 0);  // 10
```

🔹 `.find()` – Returns the first element that matches a condition.

```
const users = [{name: "Ali", age: 25}, {name: "Bob", age: 30}];
const user = users.find(user => user.age === 30);  // {name: "Bob", age: 30}
```

🔹 `.some()` – Checks if at least one element matches a condition.

```
const nums = [1, 2, 3];
const hasEven = nums.some(num => num % 2 === 0);  // true
```

🔹 `.every()` – Checks if all elements match a condition.

```
const nums = [2, 4, 6];
const allEven = nums.every(num => num % 2 === 0);  // true
```

🔹 `.sort()` – Sorts an array (modifies original array!).

```
const nums = [3, 1, 4, 2];
nums.sort((a, b) => a - b);  // [1, 2, 3, 4]
```
🔹 `.reverse()` – Reverses an array (modifies original array!).

```
const nums = [1, 2, 3];
nums.reverse();  // [3, 2, 1]
```

🔹 `.slice()` – Returns a portion of an array (does not modify original).

```
const nums = [1, 2, 3, 4];
const part = nums.slice(1, 3);  // [2, 3]
```

🔹 `.splice()` – Removes/adds elements (modifies original array!).

```
const nums = [1, 2, 3, 4];
nums.splice(1, 2, 99);  // Removes 2 and 3, inserts 99 → [1, 99, 4]
```

---

2. **String Methods**

🔹 `.split()` – Splits a string into an array.

```
const str = "hello world";
const words = str.split(" ");  // ["hello", "world"]
```

🔹 `.join()` – Joins an array into a string.

```
const words = ["hello", "world"];
const str = words.join("-");  // "hello-world"
```

🔹 `.includes()` – Checks if a string contains another string.

```
const str = "hello world";
const hasHello = str.includes("hello");  // true
```

🔹 `.replace()` – Replaces part of a string.

```
const str = "hello world";
const newStr = str.replace("world", "JS");  // "hello JS"
```

🔹 `.trim()` – Removes whitespace from the start and end.

```
const str = "  hello  ";
const trimmed = str.trim();  // "hello"
```

---

3. **Object Methods**

🔹 `Object.keys()` – Gets an array of object keys.

```
const obj = {a: 1, b: 2, c: 3};
Object.keys(obj);  // ["a", "b", "c"]
```

🔹 `Object.values()` – Gets an array of object values.

```
Object.values(obj);  // [1, 2, 3]
```

🔹 `Object.entries()` – Gets an array of key-value pairs.

```
Object.entries(obj);  // [["a", 1], ["b", 2], ["c", 3]]
```

🔹 `Object.assign()` – Copies properties to another object.

```
const obj1 = {a: 1};
const obj2 = {b: 2};
const merged = Object.assign({}, obj1, obj2);  // {a: 1, b: 2}
```

🔹 `JSON.stringify()` & `JSON.parse()` – Convert objects to/from JSON.

```
const obj = {name: "Ali", age: 25};
const str = JSON.stringify(obj);  // '{"name":"Ali","age":25}'
const parsed = JSON.parse(str);   // {name: "Ali", age: 25}
```

4. **Functional & Miscellaneous Tips**

🔹 *Arrow Functions* – Shorter function syntax.

```
const sum = (a, b) => a + b;
```

🔹 *Destructuring* – Extract values from objects/arrays.

```
const [a, b] = [1, 2];  // a = 1, b = 2
const {name, age} = {name: "Ali", age: 25};  // name = "Ali", age = 25
```

🔹 *Spread Operator `(...)`* – Copies arrays/objects easily.

```
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4];  // [1, 2, 3, 4]
```

🔹 *Rest Operator `(...)`* – Gathers multiple arguments into an array.

```
const sumAll = (...nums) => nums.reduce((acc, num) => acc + num, 0);
sumAll(1, 2, 3, 4);  // 10
```

🔹 *Ternary Operator* *(`condition ? true : false`)* – Shortens if-else.

```
const age = 18;
const canVote = age >= 18 ? "Yes" : "No";  // "Yes"
```