# Module-Scope

![image](https://github.com/user-attachments/assets/e33b8351-49d2-4aca-a73d-c67a638c6608)


Module scope means that variables declared inside a module (a file) are only accessible within that file. Each JavaScript file is treated as its own **module** and has its own separate scope.


### What are Export and Import?

- Export: Allows you to share variables, functions, or classes from one module (file) so they can be used in another module.
- Import: Allows you to use what has been exported from another module.


### Types of Export

#### 1. **Default Export**:
- Use this when you want to export a single main thing from a file.
- A file can have **only one** default export.

**Example:**
```javascript
// `math.js`
export default function add(a, b) {
  return a + b;
}
```

**How to Import:**
```javascript
// `main.js`
import add from './math.js'; // No curly braces needed
console.log(add(3, 5)); // Output: 8
```


#### 2. **Named Export**:
- Use this when you want to export **multiple things** from a file.
- A file can have multiple named exports.

**Example:**
```javascript
// `math.js`
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

**How to Import:**
```javascript
// `main.js`
import { add, subtract } from './math.js'; // Use curly braces for named exports
console.log(add(3, 5));      // Output: 8
console.log(subtract(10, 4)); // Output: 6
```


#### 4. Mixing Exports (Default + Named):
You can mix **default export** and **named exports** in the same module.

**Example:**
```javascript
// `math.js`
export default function multiply(a, b) {
  return a * b;
}
export const add = (a, b) => a + b;
export const subtract = (a, b) => a - b;
```

**How to Import:**
```javascript
// `main.js`
import multiply, { add, subtract } from './math.js';
console.log(multiply(3, 5)); // Output: 15
console.log(add(3, 5));      // Output: 8
console.log(subtract(10, 4)); // Output: 6
```


#### 5. Export with Destructuring:

#### `api.js`:
```javascript
// Exporting properties from an object using destructuring
const apiRequests = {
  fetchUsers: () => ['User1', 'User2'],
  removeUser: (id) => `User with ID ${id} removed`,
};

export const { fetchUsers, removeUser } = apiRequests;
```


### Import with the same names:

#### `main.js`:
```javascript
// Importing the destructured exports
import { fetchUsers, removeUser } from './api.js';

console.log(fetchUsers());         // Output: ['User1', 'User2']
console.log(removeUser(1));        // Output: User with ID 1 removed
```


### Import with different names:

#### `main.js`:
```javascript
// Renaming during import
import { fetchUsers as getUsers, removeUser as deleteUser } from './api.js';

console.log(getUsers());          // Output: ['User1', 'User2']
console.log(deleteUser(1));       // Output: User with ID 1 removed
```



### Key points:
- **Default Export**: Only one per file, no curly braces when importing.-
-  **Named Export**: Multiple exports allowed, must use curly braces to import.
-  You can rename imports for convenience using `as`:
   ```javascript
   import { add as sum } from './math.js';
   console.log(sum(3, 5)); // Output: 8
   ```

---

