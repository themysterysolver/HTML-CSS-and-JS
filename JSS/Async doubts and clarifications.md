## 1. Why We Need Promises & Async in JS

JavaScript is **single-threaded** (it runs one task at a time).
If a task takes too long (like reading a file, fetching data from a server, etc.), it would **block** the rest of the code.

To solve this, JavaScript uses **asynchronous programming**:

* Long tasks run in the background.
* When finished, they tell JS: "Hey, I’m done! Now run this callback."

But callbacks (`callback hell`) get messy:

```js
// Callback style (messy)
getUser(1, function(user) {
  getPosts(user.id, function(posts) {
    getComments(posts[0].id, function(comments) {
      console.log(comments);
    });
  });
});
```

➡️ To solve this mess, **Promises** were introduced.
➡️ To make Promises even cleaner, **async/await** was introduced.

---

## 2. Promises

A **Promise** is an object that represents the eventual result of an asynchronous operation.
It has 3 states:

* **Pending** → still working
* **Fulfilled** → success, result available
* **Rejected** → error occurred

### Example: Creating and using a Promise

```js
// A promise that resolves after 2 seconds
let myPromise = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("✅ Success after 2 seconds");
    // reject("❌ Error occurred");
  }, 2000);
});

// Using .then() and .catch()
myPromise
  .then(result => console.log(result))  // runs if resolve()
  .catch(error => console.log(error));  // runs if reject()
```

---

## 3. Promise Chaining

Instead of deep callbacks, we can chain Promises:

```js
function fetchData(step) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(`Step ${step} done`);
    }, 1000);
  });
}

fetchData(1)
  .then(res => {
    console.log(res);
    return fetchData(2);
  })
  .then(res => {
    console.log(res);
    return fetchData(3);
  })
  .then(res => console.log(res));
```

Output (1 sec apart):

```
Step 1 done
Step 2 done
Step 3 done
```

---

## 4. Async & Await (Sugar for Promises 🍭)

`async` and `await` make working with Promises **look like synchronous code**.

* `async` before a function makes it return a Promise.
* `await` pauses execution until the Promise is resolved or rejected.

### Example: Rewriting the above with async/await

```js
function fetchData(step) {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve(`Step ${step} done`);
    }, 1000);
  });
}

async function runSteps() {
  try {
    let res1 = await fetchData(1);
    console.log(res1);

    let res2 = await fetchData(2);
    console.log(res2);

    let res3 = await fetchData(3);
    console.log(res3);
  } catch (err) {
    console.log("Error:", err);
  }
}

runSteps();
```

➡️ Same output, but much **cleaner** than `.then().then().then()`.

---

## 5. Real-Life Example with Fetch API

### Using Promises:

```js
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then(res => res.json())
  .then(data => console.log("Promise:", data))
  .catch(err => console.log(err));
```

### Using async/await:

```js
async function getPost() {
  try {
    let response = await fetch("https://jsonplaceholder.typicode.com/posts/1");
    let data = await response.json();
    console.log("Async/Await:", data);
  } catch (err) {
    console.log(err);
  }
}

getPost();
```
---

## 6. When to Use What?

* **Callbacks**: Old style, avoid if possible.
* **Promises**: Still useful for chaining multiple async tasks.
* **Async/Await**: Best for readability, looks like sync code, easier to debug.

---

✅ **Summary**

* JS is single-threaded, async helps avoid blocking.
* **Promise**: represents a value that will be available later.
* **.then() / .catch()**: handle async results.
* **async/await**: syntactic sugar over Promises, makes async code readable.

---


---

## 🔹 What does **blocking** mean?

* **Blocking** means the program **waits** for a task to finish **before continuing** to the next line.
* While waiting, nothing else can happen — the program is "stuck".

Example (blocking style):

```js
function wait5Seconds() {
  let start = Date.now();
  while (Date.now() - start < 5000) {
    // Just looping for 5 seconds (blocking!)
  }
  console.log("Done waiting");
}

console.log("Before");
wait5Seconds();  // blocks everything for 5 seconds
console.log("After");
```

Output:

```
Before
Done waiting   <-- takes 5 seconds
After
```

➡️ During those 5 seconds, **nothing else runs**. That’s blocking.

---

## 🔹 JavaScript’s Asynchronous Nature

Normally, JS avoids blocking by making tasks **asynchronous**.
If a task takes long (like network fetch, setTimeout, DB call), JS says:

* "Okay, go do your work in the background."
* "Meanwhile, I’ll continue running the next lines."
* "When you’re done, let me know (via callback/promise)."

Example (non-blocking style):

```js
console.log("Before");

setTimeout(() => {
  console.log("Done waiting (after 5 sec)");
}, 5000);

console.log("After");
```

Output:

```
Before
After
Done waiting (after 5 sec)
```

➡️ Notice how `"After"` prints immediately without waiting for 5 seconds.
That’s **non-blocking asynchronous execution**.

---

## 🔹 Back to Your Question

> *"isn't it asynchronous in nature, it will just go to the next statement if the response was long right?"*

✅ Exactly!
That’s the whole point — **JS won’t wait** for slow tasks like fetching from the internet.
Instead:

* It starts the fetch.
* Immediately goes to the next line.
* When the fetch finishes, the `.then()` or `await` callback runs.

---

Perfect! 🚀 Let’s go over the **handy asynchronous functions** in JavaScript (the ones built into the browser/Node.js that work with the **event loop**).

---

# 🔹 1. `setTimeout()`

Runs a function **once** after a specified delay (in milliseconds).

```js
console.log("Start");

setTimeout(() => {
  console.log("Runs after 2 seconds");
}, 2000);

console.log("End");
```

👉 Output:

```
Start
End
Runs after 2 seconds
```

* JS doesn’t pause — it schedules the task and continues.
* `setTimeout(fn, 0)` is also useful → it pushes the task to the **end of the event loop queue**, so it runs *after* current code finishes.

---

# 🔹 2. `setInterval()`

Runs a function **repeatedly** at fixed intervals until you stop it.

```js
let count = 0;
let intervalId = setInterval(() => {
  count++;
  console.log("Interval:", count);
  if (count === 5) {
    clearInterval(intervalId); // stop after 5 times
  }
}, 1000);
```

👉 Prints numbers 1 → 5 every second.

---

# 🔹 3. `clearTimeout()` & `clearInterval()`

Cancel a scheduled timeout/interval.

```js
let timeoutId = setTimeout(() => {
  console.log("This will never run!");
}, 3000);

clearTimeout(timeoutId); // cancels the timeout
```

---

# 🔹 4. `Promise.resolve()` & `Promise.reject()`

Quickly create resolved/rejected promises.

```js
Promise.resolve("Instant value")
  .then(console.log); // "Instant value"

Promise.reject("Error!")
  .catch(console.log); // "Error!"
```

---

# 🔹 5. `Promise.all()`

Run multiple promises in parallel, wait until **all** finish.

```js
let p1 = new Promise(res => setTimeout(() => res("A"), 1000));
let p2 = new Promise(res => setTimeout(() => res("B"), 2000));

Promise.all([p1, p2]).then(values => console.log(values));
```

👉 Output after 2s:

```
["A", "B"]
```

---

# 🔹 6. `Promise.race()`

Returns the result of the **first** promise to finish (resolve or reject).

```js
let p1 = new Promise(res => setTimeout(() => res("Fast"), 1000));
let p2 = new Promise(res => setTimeout(() => res("Slow"), 2000));

Promise.race([p1, p2]).then(console.log);
```

👉 Output after 1s:

```
Fast
```

---

# 🔹 7. `Promise.allSettled()`

Waits for **all promises** to finish, no matter success or failure.

```js
let p1 = Promise.resolve("OK");
let p2 = Promise.reject("Fail");

Promise.allSettled([p1, p2]).then(results => console.log(results));
```

👉 Output:

```js
[
  { status: "fulfilled", value: "OK" },
  { status: "rejected", reason: "Fail" }
]
```

---

# 🔹 8. `setImmediate()` (Node.js only)

Runs a callback **immediately after the current event loop phase**.
(Similar to `setTimeout(fn, 0)` but optimized in Node.js)

---

# 🔹 9. `process.nextTick()` (Node.js only)

Runs a callback **before the event loop continues** (highest priority).

```js
console.log("Start");

process.nextTick(() => console.log("Next tick"));

console.log("End");
```

👉 Output:

```
Start
End
Next tick
```

---

✅ **Summary of Handy Async Functions**

* `setTimeout(fn, ms)` → run once after delay
* `setInterval(fn, ms)` → run repeatedly
* `clearTimeout(id)` / `clearInterval(id)` → cancel
* `Promise.resolve() / reject()` → instantly create promises
* `Promise.all()` → wait for all
* `Promise.race()` → wait for first
* `Promise.allSettled()` → wait for all (ignore errors)
* `setImmediate()` / `process.nextTick()` → Node.js event loop helpers

---


