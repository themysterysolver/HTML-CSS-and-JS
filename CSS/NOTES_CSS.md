
## CSS NOTES
---
### DISPLAY
- `block`: 
    - takes up a new line
    - occupy full width
-  `inline`:
    - takes as much spce it wants
    - no new line

- `grid` block level grid container
- `none` removed
- `inherit` inherit from parents

- `flex` block lvl flex conatainer
    - `flex-direction`: *row,column,row-reverse,column-reverse*
    - `flex-wrap`:*wrap,wrap-reverse,nowrap*
#### FLEX CONTAINER:
#### justify-content
- used along with flex
- `justify-content`:to align flex itmes when they do not use all available space on ***(mian axis)horizontal axis***
- **Property**:*ceneter,flex-start,flex-end,space-around,space-end,space-evenly*
    - `space-around` space around flex element
    - `space-between` space between flex items
    - `space-evenly` equal spaces

#### align-items
- `align-items`: align the flex items when they do not use all available space on the *cross-axis (vertically)*.
- `property`:*center,flex-start,flex-end,stretch*
- `stretch` stretches as much as possible *vertically*
- `height` is decide for ht of the container. 
  
#### align-content

- it aligns ***flex lines***
- similar to *align items*
- Here instead of aligning flex items we align flex lines.
- `Property`: *center,stretch,flex-start,flex-end,space-around,space-evenly,space-between*
- ***how each line in the flex box is alligned***

#### Perfect centering

- set both `justify-content` and `align-items` to *`center`*

#### Flex items
- Items or elements inside flex are called flex items.
- *styling* here is doen for individual items.
- property `order` tells abt the order in which they shoudl appear.
- `grow` tells about how one flex item will **grow** wrt other items.
- `flex-shrink` property specifies how much a flex item will shrink relative to the rest of the flex items.
-
---

### Z-INDEX

- how it is stacked
- can be *+ve* or *-ve*

---

### BOX-SHADOWING

- ***SYNTAX***:`box-shadow: none|h-offset v-offset blur spread color |inset|initial|inherit;`
- gives a shadow to the element
- `h-offset`
    - `+ve` right side
    - `-ve` left side
- `v-offset`
    - `+ve` below 
    - `-ve` above
- `inset` shadow inside than outside
- `blur` greater blur value greater blurrer the shadow will be .
- use `,` to have multiple shadows.
---

