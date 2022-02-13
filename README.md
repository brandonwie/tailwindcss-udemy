# Tailwind CSS practice

## Notes

### Feb 13

#### Layer & Apply Directives

- overwrite utilities

  ```css
  @layer utilities {
    .text-green-500 {
      color: blue;
    }
  }
  ```

  you can use as `@apply text-blue-900`

  ```html
  <h1 class="text-green-500">Heading</h1>
  ```

  and the `text-green-500` will now show blue color

- overwrite components

  ```css
  @tailwind base;
  @tailwind components;
  @tailwind utilities;

  @layer components {
    .menu-button {
      @apply text-white bg-indigo-500 p-3;
    }
  }
  ```

  and use as,

  ```html
  <body>
    <button class="menu-button">Click</button>
    <button class="menu-button">Exit</button>
  </body>
  ```

- Layers

  - The base layer is for things like reset rules or default styles applied to plain HTML elements.
  - The components layer is for class-based styles that you want to be able to override with utilities.
  - The utilities layer is for small, single-purpose classes that should always take precedence over any other styles.

- overwrite settings

  ```css
  @tailwind base;
  @tailwind components;
  @tailwind utilities;

  @layer base {
    a {
      @apply text-green-500 underline;
    }
  }
  ```

---

### Feb 8

#### Pseudo Selectors

- `group`

  ```html
  <div class="group bg-red-500">
    <p class="group-hover:text-white">Para 1</p>
    <p>Para 2</p>
    <!-- hover on Para 2 will trigger hover style -->
  </div>
  ```

- `:focus`: Triggered when the user clicks or taps on an element or selects it with the keyboard’s `Tab` key
- `:focus-within `: Triggered when the user clicks or taps on any of its child element or itself
- `:focus-visible`: Triggered by User-Agent on elements having :focus selector based on some heuristics that determine which one of the active elements should receive focus. (apply in Button and you'll see the real different wen )

#### Using Breakpoints

> Use unprefixed utilities to target mobile, and override them at larger breakpoints

```html
<!-- This will center text on mobile, and left align it on screens 640px and wider -->
<div class="text-center sm:text-left"></div>
```

### Feb 6, 2022

> Writing contents on README takes too much time while learning especially because I am not an expert but just to learn things quickly so I decided to minimize the amount of writing things here.

- Box Shadow: `shadow` or `shadow-{sm|md|lg|xl|2xl|inner|none}`
  - it's not that visible but give you some sort of 3D visual effect
- Border Radius: `rounded` or `rounded-{sm|md|lg|full}`
- Margin top + bottom | left + right: `mx-10`, `my-10`: x - left & right, y - top & bottom

- Text Effects: `capitalize`, `normal-case`, `font-bold`, `text-center`, `text-green-500/80`-80 is opacity
  - you may reason other effects based on what's written
- opacity can be explicitly set or set with text-color

### Feb 4, 2022

#### Padding and Margin

you won't see blue background in this case unless you set padding to the parent div because inner div occupy full space of the parent

```html
<div class="bg-blue-500">
  <div class="bg-red-500">This is inner div</div>
</div>
```

you will see the background color of the parent div here

```html
<div class="bg-blue-500 p-10">
  <div class="bg-red-500">This is inner div</div>
</div>
```

- Margins: `m-10`, `mt-10`, `mr-10`,`mb-10`,`ml-10` (all, top, right, bottom, left as ordered)
- Padding: works in the same fashion as margins but with letter `p` instead of `m`

#### Adding Gap Between & Justifying items

I think in case of `stretch` option in `justify-item`, you can set it to stretch and use width to particular items that need to be smaller. Then all other times will fit in the divs

(parent div class)

- Gap between columns: `gap-x-{value}`
- Gap between rows: `gap-y-{value}`

(parent div class)

- Align Items: `justify-items-{left | right | center}`
  you will see very thin divs from the code below if the child divs don't have width set
- Stretch Items: `justify-items-stretch`

  - it works as expected if no width is declared

  ```html
    <div
      class="bg-yellow-500 w-auto grid grid-cols-5 grid-flow-row gap-x-2 gap-y-4 justify-items-center"
    >
      <div class="h-20 w-20 bg-red-500">1</div>
      <div class="h-20 w-20 bg-red-500">2</div>
      <div class="h-20 w-20 bg-red-500">3</div>

      <div class="h-20 w-20 bg-red-500">4</div>
      <div class="h-20 w-20 bg-red-500">5</div>
      <div class="h-20 w-20 bg-red-500">6</div>

      <div class="h-20 w-20 bg-red-500">7</div>
      <div class="h-20 w-20 bg-red-500">8</div>
      <div class="h-20 w-20 bg-red-500">9</div>
    </div>
  </body>
  ```

(child div class)

- Align one item: `justify-self-{left | right | center | stretch}`

  - the `stretch` option works as expected if the item has no width set

  ```html
  <div
    class="bg-yellow-500 w-auto grid grid-cols-5 grid-flow-row gap-x-2 gap-y-4"
  >
    <div class="h-20 w-20 bg-red-500 justify-self-end">1</div>
    <div class="h-20 w-20 bg-red-500">2</div>
    <div class="h-20 w-20 bg-red-500">3</div>
    ...
    <div class="h-20 bg-red-500 justify-self-stretch">7</div>
    <div class="h-20 w-20 bg-red-500">8</div>
    <div class="h-20 w-20 bg-red-500">9</div>
  </div>
  ```

#### Flow in Grid Layout

- `grid-flow-row`: fill row first - works as expected when using with `grid-cols-{numCols}`
- `grid-flow-col`: fill column first - works as expected when using with `grid-rows-{numRows}`

---

### Feb 2, 2022

#### Flex

- `flex`, `flex-row|col-?reverse` (parent)
  - `flex-row-reverse`: send elements far right
  - `flex` must come first and separate to apply additional changes
- `flex-wrap`, `flex-wrap-reverse`: (parent) stack when there's no space for child element

- `flex-1`: (child) grow & shrink while ignoring initial size
- `flex-initial`: (child) can shrink but doesn't grow more than initial size
- `flex-auto`: (child) grow & shrink while considering initial size
- `flex-none`: (child) won't grow or shrink, scroll bar will appear when there's no space
- `flex-shrink` or `flex-shrink-0`: only shrink or don't shrink

#### Order

```html
<div class="flex bg-yellow-500 w-auto">
  <div class="order-2 h-10 w-80 bg-red-500">1</div>
  <div class="order-1 h-10 w-80 bg-blue-500">2</div>
  <div class="order-3 h-10 w-80 bg-green-500">3</div>
</div>
```

#### Grid layout

```html
<div class="bg-yellow-500 w-auto grid grid-cols-3 gap-4">
  <div class="col-span-2 h-20 bg-red-500">1</div>
  <div class="h-20 bg-red-500">2</div>
  <div class="h-20 bg-red-500">3</div>

  <div class="h-20 bg-red-500">4</div>
  <div class="h-20 bg-red-500">5</div>
  <div class="h-20 bg-red-500">6</div>

  <div class="h-20 bg-red-500">7</div>
  <div class="h-20 bg-red-500">8</div>
  <div class="h-20 bg-red-500">9</div>
</div>
```

- `grid-cols-{numCols}`: generate columns
- `gap-{gutterSize}`: gap between items
- `col-span-{numCols}`: expend column

#### Creating Row Layout

```html
<div class="bg-yellow-500 w-auto grid grid-rows-3 grid-flow-col gap-8">
  <div class="h-20 bg-red-500">1</div>
  <div class="h-20 bg-red-500">2</div>
  <div class="h-20 bg-red-500">3</div>

  <div class="h-20 bg-red-500">4</div>
  <div class="h-20 bg-red-500">5</div>
  <div class="h-20 bg-red-500">6</div>

  <div class="h-20 bg-red-500">7</div>
  <div class="h-20 bg-red-500">8</div>
  <div class="h-20 bg-red-500">9</div>
</div>
```

- make grid in a row fashion (numbering continues downwards, not to the right)

---

### Jan 31, 2022

- What does `-i` flag does in build command?

  ```json
    "scripts": {
      "build": "tailwind build -i ./src/styles.css -o ./public/styles.css"
    },
  ```

  - because it threw a deprecation error

- **container**: 100% width of the breakpoints

- horizontal center align: `mx-auto` (margin x-axis)

  - \*`container` class work with fixed screen sizes and not when you want a fluid and responsive layout

- `w-4`: width 1rem (1 = 0.25rem)
- `w-1/2`: width 50%
