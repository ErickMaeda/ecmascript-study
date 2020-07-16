# ES10 / ES2019

## Array.prototype.{flat,flatMap}
> The flat() method enables you to easily concatenate all sub-array elements of an array. Consider the following example:

```js
let arr = ['a', 'b', ['c', 'd']];
let flattened = arr.flat();

console.log(flattened);    // => ["a", "b", "c", "d"]

arr = ['a', , , 'b', ['c', 'd']];
flattened = arr.flat();

console.log(flattened);    // => ["a", "b", "c", "d"]

arr = [10, [20, [30]]];

console.log(arr.flat());     // => [10, 20, [30]]
console.log(arr.flat(1));    // => [10, 20, [30]]
console.log(arr.flat(2));    // => [10, 20, 30]
```

> The flatMap() method combines map() and flat() into one method. It first creates a new array with the return value of a provided function and then concatenates all sub-array elements of the array. An example should make this clearer:

```js
const arr = [4.25, 19.99, 25.5];

console.log(arr.map(value => [Math.round(value)]));    
// => [[4], [20], [26]]

console.log(arr.flatMap(value => [Math.round(value)]));    
// => [4, 20, 26]
```

# Object.fromEntries
> This static method allows you to easily transform a list of key-value pairs into an object:

```js
const myArray = [['one', 1], ['two', 2], ['three', 3]];
const obj = Object.fromEntries(myArray);

console.log(obj);    // => {one: 1, two: 2, three: 3}
```

## String.prototype.{trimStart,trimEnd}
> The trimStart() and trimEnd() methods are technically the same as trimLeft() and trimRight(). These methods are currently stage 4 proposals and will be added to the specification for consistency with padStart() and padEnd(). Let’s look at some examples:

```js
const str = "   string   ";

// es2019
console.log(str.trimStart());    // => "string   "
console.log(str.trimEnd());      // => "   string"

// the same as
console.log(str.trimLeft());     // => "string   "
console.log(str.trimRight());    // => "   string"
```
> For web compatibility, trimLeft() and trimRight() will remain as aliases for trimStart() and trimEnd().

## Symbol.prototype.description
> When creating a Symbol, you can add a description to it for debugging purposes. Sometimes, it’s useful to be able to directly access the description in your code.

> This ES2019 proposal adds a read-only description property to the Symbol object, which returns a string containing the description of the Symbol. Here are some examples:

```js
let sym = Symbol('foo');
console.log(sym.description);    // => foo

sym = Symbol();
console.log(sym.description);    // => undefined

// create a global symbol
sym = Symbol.for('bar');
console.log(sym.description);    // => bar
```

## Optional catch binding
> This makes a small change to the ECMAScript specification that allows you to omit the catch binding and its surrounding parentheses:

```js
try {
  // use a feature that the browser might not have implemented
} catch {
  // do something that doesn’t care about the value thrown
}
```


----

# ES11 / ES2020
