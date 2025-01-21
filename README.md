# Module-Scope

![image](https://github.com/user-attachments/assets/476fde6b-715b-4543-b2d5-7f87269e5673)


Module scope means that variables declared inside a module (a file) are only accessible within that file. Each JavaScript file is treated as its own **module** and has its own separate scope.

If we want to share variables, functions, or other things between modules, you need to use **export** and **import**.

### Example:

Let's say we have two files:

#### `math.js` (Module 1):
```javascript
// This is a separate module
const add = (a, b) => a + b;
const subtract = (a, b) => a - b;

// Export the functions so they can be used in another module
export { add, subtract };
```

#### `main.js` (Module 2):
```javascript
// Import the functions from math.js
import { add, subtract } from './math.js';

console.log(add(5, 3)); // Output: 8
console.log(subtract(5, 3)); // Output: 2
```

Here’s what’s happening:

1. The `math.js` file defines two functions: `add` and `subtract`. 
2. These functions are **not automatically accessible** outside `math.js`. 
3. To share them, we use `export`.
4. In `main.js`, we use `import` to bring the `add` and `subtract` functions into the file.

### Importance
- It keeps variables and functions private to their files unless explicitly shared.
- This prevents accidental interference between different parts of your code.

