# TypeScript Basics
TypeScript is a strongly-typed superset of JavaScript that compiles to plain JavaScript.

### Data Types in TypeScript
1. **Primitive Types**: Represent single values and include:
   - `number`: Represents numeric values.
   - `string`: Represents text.
   - `boolean`: Represents true or false values.
   - `null` and `undefined`: Represent absence of value.
   - `symbol`: Represents unique identifiers.

2. **Object Types**: Includes objects, arrays, functions, classes, interfaces, and enums.

```typescript
let num: number = 10;
let str: string = "Hello, TypeScript!";
let bool: boolean = true;
let nul: null = null;
let undef: undefined = undefined;
let sym: symbol = Symbol("key");
```

### TypeScript Collections and Classes Initialization

- Array

```typescript
    let arrayExample: number[] = [1, 2, 3, 4, 5];
    push(): Adds elements to the end.
    pop(): Removes and returns the last element.
    shift(): Removes and returns the first element.
    unshift(): Adds elements to the beginning.
    splice(): Adds or removes elements at specific indexes.
    slice(): Returns a shallow copy of a portion of an array.
```
- Object

```typescript
let objExample: { [key: string]: number } = { "apple": 1, "banana": 2 };
```
- Map

```typescript
let mapExample: Map<string, number> = new Map();
mapExample.set("apple", 1);

    set(key, value): Sets the value for a key.
    get(key): Returns the value associated with a key.
    delete(key): Removes a key and its associated value.
```
- Set

```typescript
    let setExample: Set<number> = new Set();
    setExample.add(1);

    add(value): Adds a new element to the set.
    delete(value): Removes a value from the set.
    has(value): Checks if a value exists in the set.
```
### Access Modifiers in TypeScript

Access modifiers control the visibility and accessibility of class members.

```typescript

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

### Summary
TypeScript provides static typing and additional features over JavaScript, making it suitable for large-scale application development.