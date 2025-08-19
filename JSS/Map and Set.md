### Map and Set

# 🔹 1. `Map`

* Stores **key–value pairs** (like objects).
* But unlike objects:

  * Keys can be **any type** (objects, functions, NaN, etc).
  * Maintains **insertion order**.
  * Has useful methods.

```js
let map = new Map();

// Add
map.set("name", "Prabha");
map.set(1, "One");
map.set({id: 101}, "Object Key");

// Get
console.log(map.get("name")); // "Prabha"

// Check
console.log(map.has(1)); // true

// Delete
map.delete(1);

// Size
console.log(map.size); // 2

// Iterate
for (let [k, v] of map) console.log(k, v);
```

---

# 🔹 2. `Set`

* Stores **unique values** only (no duplicates).
* Order is maintained.

```js
let set = new Set();

// Add
set.add(1);
set.add(2);
set.add(2); // ignored (duplicate)

// Check
console.log(set.has(1)); // true

// Delete
set.delete(1);

// Size
console.log(set.size); // 1

// Iterate
for (let val of set) console.log(val); // 2
```

👉 Great for removing duplicates:

```js
let arr = [1, 2, 2, 3, 4, 4];
let unique = [...new Set(arr)]; 
console.log(unique); // [1,2,3,4]
```

---

# 🔹 3. `WeakMap`

* Similar to `Map`, but **keys must be objects**.
* Keys are **weakly referenced** → if object is garbage-collected, entry disappears automatically.
* **Not iterable** (for security/memory reasons).

```js
let weakMap = new WeakMap();
let obj = {id: 1};

weakMap.set(obj, "Secret");
console.log(weakMap.get(obj)); // "Secret"

obj = null; // now garbage collected, entry removed
```

👉 Useful for storing **private data** tied to objects.

---

# 🔹 4. `WeakSet`

* Similar to `Set`, but only stores **objects**.
* Weakly held (garbage-collectable).
* **Not iterable**.

```js
let weakSet = new WeakSet();
let obj1 = {name: "Prabha"};
let obj2 = {name: "John"};

weakSet.add(obj1);
weakSet.add(obj2);

console.log(weakSet.has(obj1)); // true

obj1 = null; // removed from memory automatically
```

---

# 🔹 5. Typed Arrays (Special for Binary Data)

* Collections for working with **raw binary data** (e.g., `Int8Array`, `Uint8Array`, `Float32Array`).
* Mostly used in games, WebGL, image processing, etc.

```js
let buffer = new ArrayBuffer(8);  // 8 bytes
let int32 = new Int32Array(buffer);
int32[0] = 12345;
console.log(int32[0]); // 12345
```

---

# 🔹 Quick Comparison Table

| Collection       | Keys            | Values  | Unique? | Order | Iterable?    | Use Case                 |
| ---------------- | --------------- | ------- | ------- | ----- | ------------ | ------------------------ |
| **Object**       | Strings/Symbols | Any     | No      | No    | Yes (for-in) | General key-value        |
| **Array**        | Index (0..n)    | Any     | No      | Yes   | Yes          | Ordered list             |
| **Map**          | Any (obj, fn…)  | Any     | No      | Yes   | Yes          | Key-value, flexible keys |
| **Set**          | N/A             | Any     | ✅ Yes   | Yes   | Yes          | Unique values            |
| **WeakMap**      | Objects only    | Any     | No      | N/A   | ❌ No         | Private object data      |
| **WeakSet**      | Objects only    | N/A     | ✅ Yes   | N/A   | ❌ No         | Track object existence   |
| **Typed Arrays** | Index           | Numbers | N/A     | Yes   | Yes          | Binary/raw data          |

---

✅ **Summary**

* Use **Map** when you need key-value with any type of key.
* Use **Set** when you need unique values.
* Use **WeakMap/WeakSet** for memory-efficient object tracking.
* Use **Typed Arrays** for binary/numeric heavy tasks.

---


# 🔹 `Map` Basics (Key → Value)

👉 **Check if a key exists**

```js
let map = new Map();
map.set("name", "Prabha");
map.set("age", 21);

console.log(map.has("name")); // ✅ true
console.log(map.has("gender")); // ❌ false
```

👉 **Get only keys**

```js
for (let key of map.keys()) {
  console.log(key);
}
// Output:
// name
// age
```

👉 **Get only values**

```js
for (let value of map.values()) {
  console.log(value);
}
// Output:
// Prabha
// 21
```

👉 **Get both keys and values**

```js
for (let [k, v] of map.entries()) {
  console.log(k, v);
}
// Output:
// name Prabha
// age 21
```

👉 **Convert to arrays**

```js
console.log([...map.keys()]);   // ["name", "age"]
console.log([...map.values()]); // ["Prabha", 21]
```

---

# 🔹 `Set` Basics (Unique Values Only)

👉 **Check if an element exists**

```js
let set = new Set([1, 2, 3]);

console.log(set.has(2)); // ✅ true
console.log(set.has(4)); // ❌ false
```

👉 **Get all elements (like keys)**

```js
for (let val of set) {
  console.log(val);
}
// Output: 1 2 3
```

👉 **Convert to array**

```js
let arr = [...set];
console.log(arr); // [1,2,3]
```

👉 **Delete and clear**

```js
set.delete(2);
console.log(set); // Set(2) {1, 3}

set.clear();
console.log(set); // Set(0) {}
```

---

# ✅ Quick Cheatsheet

### For **Map**

* `map.set(key, value)` → add/update
* `map.get(key)` → get value
* `map.has(key)` → check existence
* `map.delete(key)` → remove key
* `map.clear()` → remove everything
* `map.keys()` → iterable of keys
* `map.values()` → iterable of values
* `map.entries()` → iterable of `[key, value]`

### For **Set**

* `set.add(value)` → add
* `set.has(value)` → check existence
* `set.delete(value)` → remove
* `set.clear()` → remove all
* `set.size` → count of elements

---
