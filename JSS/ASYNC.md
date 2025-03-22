# ASYNC js
#### Callback
- `callback` is a **function passed** as an *parameter*.
- pass the **name** don't *call it* using `()`
- they are much used in **async functions**.
- Also you can pass the *functiom itself*.
---
#### async js
- function running in `||el` with other function.
```
setTimeout(myFunction, 3000);
```
- after *3sec* it will run
- wkt, `setInterval` is to call the function every **nth** sec.

---
#### Promises
- `Producing code`- the code that takes some time to run.
-  `Consuming code`-the code which wait for result
- We shoudl create new `obj` of ***promise***
```
let myPromise=new Promise(function(myResolve,myReject){});
```
- the producing code SHOULD call on of the 2 callbacks *myResolve* ***(result)***/*myReject* ***(error obj)***.
```
myPromise.then{ function(value);function(error)}
```
- the obj cn ne in 
    - pending (working)
    - fulfilled (yields result)
    - rejected state (error obj)
> **NOTE**: Can't handle *state* and *result* thus we should `method`

---

#### ASYNC and WAIT
- `async` makes a function to *return a promise*
    - `async` before a function makes  it to return a ***promise***.
- `await` makes the function *waits for a promise*
    - pauses and waits for a resolved promise
-   `promise.resolve()`=>`resolve()` it returns a resoved promise,if it is already a promsie it simply return a promise.
---
