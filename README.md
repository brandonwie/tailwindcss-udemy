# Tailwind CSS practice

## Notes

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
