## NOTES_JSS

---

### FUNCTIONS
- `function` keyword is used
- `function <declaration> function <function name> (param1,......)` NOrmalfunction declaration doesm't need `;`
- functions are hoisted
- `()` they are excuted by ***self(self-invoking)***
- missing parameter `unefined`,we can also set *default* val like in `py`.
### FUNCTION EXPRESSIONS
- they end with a varaible `;`
- They are *anonymous*
- We call that be using the varaible on which we are storing it.
```
let x=function(a,b){return a+b};
```
### ARROW FUNCTION
- short synatx for writing function expressions.
- we don't need `function` and `return` keyword.
- They are not used for object methos,that is can't use `this`
- if u are going to use `return` then use `{}`

```
const z= (x,y) => x*y;
const z= (x,y) => { return x*y};
```

---

### EVENTS,EVENT LISTENER

- It is a *method*,which attaches event handler to specifed element.
- **SYNTAX**:`element.addEventListener(event, function, useCapture);`  
    - `event` is the event occured
    - `function` is the method we are going to call
    -  3rd param is *bool* used for ***event bubbling*** or ***event cathing***
        - `<div><p></p></div>`
        - `Event bubbling` - *innermost element's event* is handled first.`true`
        - `event capturing` - *outtermost element's event* `false`
- `addEventListener` and `removeEventListener` is used.

### getBoundingClientRect

- `element.getBoundingClientRect()`
- returns *A DOMRect object* with **eight** properties:
    - ***left, top, right, bottom, x, y, width, height.***