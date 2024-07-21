# TypeScript Basics
TypeScript is a strongly-typed superset of JavaScript that compiles to plain JavaScript.

## 🚀 Data Types in TypeScript
1. **Primitive Types**: Represent single values and include:
   - `number`: Represents numeric values.
   - `string`: Represents text.
   - `boolean`: Represents true or false values.
   - `null` and `undefined`: Represent absence of value.
   - `symbol`: Represents unique identifiers.
   - `bigint`: Used for very large integers,

```ts
let num: number = 10;
let str: string = "Hello, TypeScript!";
let bool: boolean = true;
let nul: null = null;
let undef: undefined = undefined;
let sym: symbol = Symbol("key");
```
2. **Object Types**: Includes objects, arrays, functions, classes, interfaces, and enums.
3. **Other Types**: `Type Aliases`, `Union Types`, `Interfaces`, `Record`, `Union`; 
```ts 
//Interface Extending an interface

interface Animal {
  name: string;
}

interface Bear extends Animal {
  honey: boolean;
}

const bear = getBear();
bear.name;
bear.honey;
```       
```ts
//Extending a type via intersections

type Animal = {
  name: string;
}

type Bear = Animal & { 
  honey: boolean;
}

const bear = getBear();
bear.name;
bear.honey;      
```
## 🚀 TypeScript Collections and Classes Initialization

- Array

```ts
    let arrayExample: number[] = [1, 2, 3, 4, 5];
    push(): Adds elements to the end.
    pop(): Removes and returns the last element.
    shift(): Removes and returns the first element.
    unshift(): Adds elements to the beginning.
    splice(): Adds or removes elements at specific indexes.
    slice(): Returns a shallow copy of a portion of an array.
```
- Object

```ts
let objExample: { [key: string]: number } = { "apple": 1, "banana": 2 };
```
- Map

```ts
let mapExample: Map<string, number> = new Map();
mapExample.set("apple", 1);

    set(key, value): Sets the value for a key.
    get(key): Returns the value associated with a key.
    delete(key): Removes a key and its associated value.
```
- Set

```ts
    let setExample: Set<number> = new Set();
    setExample.add(1);

    add(value): Adds a new element to the set.
    delete(value): Removes a value from the set.
    has(value): Checks if a value exists in the set.
```
## 🚀 Access Modifiers in TypeScript

Access modifiers control the visibility and accessibility of class members.

```ts

class AccessModifiersExample {
    public publicMethod(): void {
        console.log("This is a public method.");
    }

    protected protectedMethod(): void {
        console.log("This is a protected method.");
    }

    private privateMethod(): void {
        console.log("This is a private method.");
    }
}
```
- Public: Accessible from anywhere.
- Protected: Accessible within the same class and by subclasses.
- Private: Accessible only within the same class.

The default access modifier in TypeScript is public.

## 🚀 Some important Core concepts on typescript/javascript

- 🚀 Higher Order function
In TypeScript, higher-order functions are functions that either take other functions as arguments, return a function, or both. Higher-order functions are powerful tools that enable functional programming paradigms, such as map, filter, and reduce operations on arrays.
1. takes function as argument
```ts
const numbers: number[] = [1, 2, 3, 4, 5];
const doubledNumbers = numbers.map((num: number): number => {
    return num * 2;
});
console.log(doubledNumbers); // Output: [2, 4, 6, 8, 10]
```
2. Return function
```ts
function createMultiplier(factor: number): (x: number) => number {
    return (x: number): number => {
        return x * factor;
    };
}
const double = createMultiplier(2);
console.log(double(5)); // Output: 10
const triple = createMultiplier(3);
console.log(triple(5)); // Output: 15
```
3. Compose 
```ts
function compose<T>(...fns: ((arg: T) => T)[]): (arg: T) => T {
    return (arg: T): T => {
        return fns.reduceRight((acc, fn) => fn(acc), arg);
    };
}

const addOne = (x: number): number => x + 1;
const square = (x: number): number => x * x;

const addOneThenSquare = compose(square, addOne);

console.log(addOneThenSquare(2)); // Output: 9
```
Benefits of Higher-Order Functions
- Reusability:
- Abstraction
- Functional Programming (e.b composition and currying)

### 🚀 Function Composition
Function composition is the process of combining two or more functions to produce a new function.
```ts
//custom compose
const addOne = (x: number): number => x + 1;
const square = (x: number): number => x * x;

// Compose these functions
const addOneThenSquare = (x: number): number => square(addOne(x));

console.log(addOneThenSquare(2)); // Output: 9
```
```ts
//built-in compose
function compose<T>(...fns: ((arg: T) => T)[]): (arg: T) => T {
    return (arg: T): T => {
        return fns.reduceRight((acc, fn) => fn(acc), arg);
    };
}

const addOneThenSquare = compose(square, addOne);

console.log(addOneThenSquare(2)); // Output: 9
```

### 🚀 Function Currying
Currying is the process of transforming a function that takes multiple arguments into a sequence of functions, each taking a single argument. This technique allows you to break down functions into smaller, reusable functions with partial application.

```ts
const add = (x: number, y: number): number => x + y;

//curried version:
const curriedAdd = (x: number) => (y: number): number => x + y;
const addFive = curriedAdd(5);
console.log(addFive(3)); // Output: 8
console.log(curriedAdd(5)(3)); // Output: 8

//Currying a Function with Multiple Parameters
const multiply = (x: number, y: number, z: number): number => x * y * z;
const curriedMultiply = (x: number) => (y: number) => (z: number): number => x * y * z;
const multiplyBy2 = curriedMultiply(2);
const multiplyBy2And3 = multiplyBy2(3);

console.log(multiplyBy2And3(4)); // Output: 24
console.log(curriedMultiply(2)(3)(4)); // Output: 24

```
### 🚀 Implementing custom map, filter, reduce
- Note:  `map`, `reduce`, and `filter` methods in JavaScript do not modify the original array.

```js
Array.prototype.myMap = function(callback) {
    const result = [];
    for (let i = 0; i < this.length; i++) {
        result.push(callback(this[i], i, this));
    }
    return result;
};

Array.prototype.myReduce = function(callback, initialValue) {
    let accumulator = initialValue;
    for (let i = 0; i < this.length; i++) {
        accumulator = callback(accumulator, this[i], i, this);
    }
    return accumulator;
};

Array.prototype.myFilter = function(callback) {
    const result = [];
    for (let i = 0; i < this.length; i++) {
        if (callback(this[i], i, this)) {
            result.push(this[i]);
        }
    }
    return result;
};

```
Note: `callback(this[i], i, this)` passing the `this` so callback will always have access to whole array.

### 🚀 Other core concepts of javascript
- `Promise`, `async/await`, `Promise chain/hell`
- `Hoisting`
    var, let get hoisted to gobal scope before it's declaration
    accesing var result undefined
    accessing const, let result reference error
```js
function demo() {
  let x = (y = 0);
  x++;
  y++;
  return x;
}
console.log(demo(), typeof x, typeof y);
//correct output: 1, undefined, number
// explaination: since y is not delcared with var, let or const.. so after calling demo(); y will get hoisted to global scope so type will be number.
//x will not be available so typeof x would be undefined
```
- `Closure` refers to a function that `retains access to its lexical scope, even after the function has finished executing`. This allows the function to "close over" the variables defined in its scope.
```ts
function createCounter() {
    let count = 0;  // `count` is a variable in the lexical scope of `createCounter`
    return function() {
        count += 1;  // The returned function has access to `count`
        return count;
    };
}
const counter = createCounter();  // `counter` is a closure
console.log(counter());  // Outputs: 1
console.log(counter());  // Outputs: 2
console.log(counter());  // Outputs: 3

```
- Single threaded `blocking/non-blocking` I/O operations, `Event loop` concepts
```js
const myFun = (count) => {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      console.log(++count);
      resolve(count);
    }, 2000);
    console.log("hello");
  });
};

(async () => {
  console.log(1);
  console.log(2);
  const a = await myFun(1);
  console.log(a);
  console.log(3);
})();

//correct output: 1, 2, hello, 2, 2, 3
```
### 🚀 Event loop
The event loop is a fundamental concept in JavaScript and TypeScript, as both languages share the same runtime environment (typically `Node.js` or `browsers`).

- The event loop is a mechanism that allows JavaScript to perform non-blocking operations despite being single-threaded. It handles the execution of code, collects and processes events, and executes queued sub-tasks.

#### Working of event loop
- `Execution Stack`: Contains the currently executing code. When a function is called, it’s pushed onto the stack; when it returns, it’s popped off.

- `Callback Queue`: Holds callbacks (like event handlers or resolved promises) that are waiting to be executed.

- `Event Loop`: Continuously checks the stack and the callback queue. If the stack is empty, it pushes the oldest callback from the queue onto the stack for execution.

Code Example
```ts
console.log('Start'); // (1) Synchronous operation
setTimeout(() => {
    console.log('Inside timeout'); // (3) Asynchronous operation
}, 0);
console.log('End'); // (2) Synchronous operation
//output: Start, End, Inside timeout
```
```lua
+-----------------+
|     Stack       |
|-----------------|
| console.log('Start')  (1)
| console.log('End')    (2)
+-----------------+
          |
          v
+-----------------+       +-----------------+
| Callback Queue  | <---> |   Event Loop    |
|-----------------|       +-----------------+
| setTimeout callback (3)|
+-----------------+

```
## 🚀 Summary
TypeScript provides static typing and additional features over JavaScript, making it suitable for large-scale application development.