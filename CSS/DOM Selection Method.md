## DOM Selection methods

---

# 🔹 1. `getElementById()`

* Selects **one element** by its `id`.
* Returns a single element (or `null` if not found).

```html
<p id="intro">Hello</p>
<script>
  let el = document.getElementById("intro");
  console.log(el.textContent); // "Hello"
</script>
```

✅ Fastest way to select because IDs are unique.

---

# 🔹 2. `getElementsByClassName()`

* Selects **all elements** with a given class.
* Returns an **HTMLCollection** (array-like, live list).

```html
<p class="note">One</p>
<p class="note">Two</p>
<script>
  let els = document.getElementsByClassName("note");
  console.log(els[0].textContent); // "One"
</script>
```

---

# 🔹 3. `getElementsByTagName()`

* Selects elements by tag (like `div`, `p`, `span`).
* Returns an **HTMLCollection** (live).

```html
<p>Para 1</p>
<p>Para 2</p>
<script>
  let paras = document.getElementsByTagName("p");
  console.log(paras.length); // 2
</script>
```

---

# 🔹 4. `getElementsByName()`

* Selects elements by their `name` attribute (mostly for form inputs).
* Returns a **NodeList** (not live).

```html
<input type="text" name="username">
<input type="text" name="username">
<script>
  let inputs = document.getElementsByName("username");
  console.log(inputs.length); // 2
</script>
```

---

# 🔹 5. `querySelector()`

* Selects the **first element** that matches a CSS selector.
* Very powerful, works with `#id`, `.class`, `[attr]`, `tag`, etc.

```html
<p class="note">Note 1</p>
<p class="note">Note 2</p>
<script>
  let el = document.querySelector(".note");
  console.log(el.textContent); // "Note 1"
</script>
```

---

# 🔹 6. `querySelectorAll()`

* Selects **all elements** matching a CSS selector.
* Returns a **NodeList** (static, not live).

```html
<p class="note">Note 1</p>
<p class="note">Note 2</p>
<script>
  let els = document.querySelectorAll(".note");
  els.forEach(el => console.log(el.textContent));
  // "Note 1", "Note 2"
</script>
```

---

# 🔹 7. Special DOM Shortcuts

### ✅ `document.body` → selects `<body>`

### ✅ `document.head` → selects `<head>`

### ✅ `document.documentElement` → selects `<html>`

### ✅ `document.forms` → all `<form>` elements

### ✅ `document.images` → all `<img>` elements

### ✅ `document.links` → all `<a>` with `href`

```js
console.log(document.body);          // <body>...</body>
console.log(document.forms[0]);      // first form
console.log(document.images.length); // number of images
```

---

# 🔹 8. Traversal Properties

Once you select an element, you can navigate:

* `element.children` → HTMLCollection of child elements
* `element.firstElementChild` / `lastElementChild`
* `element.parentElement`
* `element.nextElementSibling` / `previousElementSibling`

```html
<div id="box">
  <p>Para 1</p>
  <p>Para 2</p>
</div>
<script>
  let box = document.getElementById("box");
  console.log(box.children[0].textContent); // "Para 1"
</script>
```

---

# 🔹 Difference Between `HTMLCollection` & `NodeList`

* **HTMLCollection** → live, auto-updates when DOM changes.
* **NodeList** → static, does not auto-update (except for `childNodes`).
* Both are **array-like**, but not real arrays (need `Array.from()` to convert).

---

✅ **Summary of Selection Methods**

1. `getElementById()` → one element by id.
2. `getElementsByClassName()` → multiple by class.
3. `getElementsByTagName()` → multiple by tag.
4. `getElementsByName()` → by `name` attribute.
5. `querySelector()` → first match (CSS selector).
6. `querySelectorAll()` → all matches (CSS selector).
7. Special shortcuts → `body`, `head`, `forms`, `images`, etc.
8. Traversal properties → navigate relatives (`parent`, `children`, `siblings`).

---

