#### 1. **Map Object**

- **Definition**: A `Map` object is a collection of key-value pairs where both keys and values can be of any data type. Keys in a `Map` are unique, and elements are iterated in the insertion order.
  
- **Basic Operations**:
  - **Set key-value pairs**:
    ```js
    const sayings = new Map();
    sayings.set("dog", "woof");
    sayings.set("cat", "meow");
    ```
  - **Get value by key**:
    ```js
    sayings.get("dog"); // Returns 'woof'
    ```
  - **Check key existence**:
    ```js
    sayings.has("bird"); // Returns false
    ```
  - **Delete a key-value pair**:
    ```js
    sayings.delete("dog");
    sayings.has("dog"); // Returns false
    ```
  - **Get the size of the map**:
    ```js
    sayings.size; // Returns the number of elements
    ```
  - **Iterate over the map**:
    ```js
    for (const [key, value] of sayings) {
      console.log(`${key} goes ${value}`);
    }
    ```
  - **Clear the map**:
    ```js
    sayings.clear(); // Removes all elements
    ```

- **Comparison with Object**:
  - **Keys**: Map keys can be any type (objects, functions), while Object keys are usually strings or symbols.
  - **Size**: Maps have a built-in `size` property, while Objects don’t.
  - **Iteration**: Map iteration is in insertion order.
  - **Prototype**: Objects have a prototype, which could result in default keys. Maps do not have this problem.

- **When to use a Map**:
  - If keys are not known until runtime or if they are of different types.
  - If you need to store primitive values as keys (Numbers, Booleans, etc.).
  - If you need insertion order iteration.

---

#### 2. **WeakMap Object**

- **Definition**: A `WeakMap` is similar to `Map`, but its keys must be objects (or non-registered symbols). It does not prevent its keys from being garbage-collected when there are no other references to them.

- **Key Features**:
  - Keys must be objects or non-registered symbols.
  - **Garbage collection**: If the object used as a key is no longer referenced, it and its associated value will be garbage collected.
  - **Non-enumerable**: You cannot iterate over a `WeakMap` because it doesn’t allow key enumeration to avoid exposing garbage collection behavior.

- **Use Case**: `WeakMap` is useful for storing private data or implementation details inside an object. The example below demonstrates storing private data for a public object:
  ```js
  const privates = new WeakMap();

  function Public() {
    const me = {};
    privates.set(this, me);
  }

  Public.prototype.method = function () {
    const me = privates.get(this);
    // Use private data
  };
  ```

---

#### 3. **Set Object**

- **Definition**: A `Set` object stores unique values of any type. Like `Map`, the elements are iterated in insertion order.

- **Basic Operations**:
  - **Add values**:
    ```js
    const mySet = new Set();
    mySet.add(1);
    mySet.add("some text");
    ```
  - **Check value existence**:
    ```js
    mySet.has(1); // Returns true
    ```
  - **Delete values**:
    ```js
    mySet.delete("foo");
    ```
  - **Get the size of the set**:
    ```js
    mySet.size; // Returns the number of elements
    ```
  - **Iterate over a set**:
    ```js
    for (const item of mySet) {
      console.log(item);
    }
    ```

- **Array vs. Set**:
  - **Uniqueness**: A `Set` stores only unique values, so duplicates are automatically removed.
  - **Deleting elements**: In an array, you must find the element’s index and remove it with `splice()`. In a `Set`, you can directly use `delete()` by value.
  - **Performance**: Operations like checking if a value exists (`has`) or removing elements are faster in `Set` compared to array methods.

- **Converting between Array and Set**:
  - Convert a `Set` to an `Array`:
    ```js
    Array.from(mySet); 
    ```
  - Convert an `Array` to a `Set`:
    ```js
    const mySet2 = new Set([1, 2, 3, 4]);
    ```

---

#### 4. **WeakSet Object**

- **Definition**: A `WeakSet` is similar to a `Set`, but it only holds objects, and those objects can be garbage collected when no longer referenced elsewhere.

- **Key Features**:
  - Holds only **objects** or **non-registered symbols**.
  - References are **weak**, meaning objects in the set can be garbage collected if there are no other references to them.
  - **Non-enumerable**: You cannot iterate over a `WeakSet` because its contents can change due to garbage collection.

- **Use Cases**:
  - **Memory-efficient tracking**: Useful for marking or tracking DOM elements without risking memory leaks.
  - **Preventing leaks**: Objects in `WeakSet` that are no longer referenced elsewhere will be automatically removed.

---

#### 5. **Key and Value Equality in Map and Set**

- **Algorithm**: Both `Map` keys and `Set` values are compared using the `SameValueZero` algorithm, which:
  - Works like strict equality (`===`).
  - Treats `-0` and `+0` as equal.
  - Treats `NaN` as equal to itself, unlike `===` which considers `NaN !== NaN`.

--- 

These notes cover the key concepts and usage of `Map`, `WeakMap`, `Set`, and `WeakSet` in JavaScript. They can help you understand when and how to use each type of collection depending on the use case!

____

Tags : #javascript