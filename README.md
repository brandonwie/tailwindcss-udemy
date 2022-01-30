# Tailwind CSS practice

Jan 31, 2022

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
