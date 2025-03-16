### **1. Mouse Events**

| Event         | Description |
|--------------|------------|
| `click`      | Triggered when the button is clicked. |
| `dblclick`   | Triggered when the button is double-clicked. |
| `mousedown`  | Triggered when the mouse button is pressed down on the button. |
| `mouseup`    | Triggered when the mouse button is released after pressing it. |
| `mousemove`  | Triggered when the mouse moves over the button. |
| `mouseenter` | Triggered when the mouse enters the button area. |
| `mouseleave` | Triggered when the mouse leaves the button area. |
| `mouseover`  | Similar to `mouseenter`, but also fires if a child element is hovered. |
| `mouseout`   | Similar to `mouseleave`, but also fires if a child element is left. |
| `contextmenu` | Triggered when the right mouse button is clicked (opens the context menu). |

---

### **2. Keyboard Events** (If the button is focused)

| Event      | Description |
|-----------|------------|
| `keydown`  | Triggered when a key is pressed down. |
| `keyup`    | Triggered when a key is released. |
| `keypress` | (Deprecated) Used to detect when a key is pressed. |

---

### **3. Touch Events** (For mobile devices)

| Event        | Description |
|-------------|------------|
| `touchstart`  | Triggered when a finger touches the button. |
| `touchmove`   | Triggered when a finger moves over the button. |
| `touchend`    | Triggered when the finger is lifted from the button. |
| `touchcancel` | Triggered when the touch is interrupted (e.g., switching apps). |

---

### **4. Focus & Form Events**

| Event   | Description |
|---------|------------|
| `focus`  | Triggered when the button gains focus (e.g., tab key). |
| `blur`   | Triggered when the button loses focus. |
| `submit` | (For forms) Triggered when a form containing the button is submitted. |

---

### **5. Drag & Drop Events** (If draggable)

| Event       | Description |
|------------|------------|
| `dragstart` | Triggered when dragging starts. |
| `drag`      | Triggered while dragging. |
| `dragend`   | Triggered when dragging ends. |
| `dragover`  | Triggered when a draggable element is dragged over another. |
| `drop`      | Triggered when a draggable element is dropped. |
