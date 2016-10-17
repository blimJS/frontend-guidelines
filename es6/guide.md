#ES6 Guide


##Whitespace 
 
- Indentation: use two spaces`\s` don't use tabs `\t`. 
- A Space before leading brace

```javascript
// indentation 
function foo() {
  const name = 'foo';
}

// indentation chained functions 
response
  .then(() => {})
  .then(() => {})
  .error(() => {});
    
http.method('POST', {
  url: '//www.origin.com'
});
```

- Place a space before opening a parentheses in control statements 

```javascript
if (condition) {
     
}

while (condition) {
  
}
```

- For arguments leave space between parameters

```javascript 
  function transform(param1, param2, param3) {
    
  }
```

- Space between operators

```javascript
const x = y + 5;
```


##References
- Use `const` for all unmutable references

```javascript
const name = 'John';

```
- Use `let` for mutable references
- Don't use `var`

##Objects

- Create objects with literal syntax

```javascript 
// use literal
const object =  {};
```

- Use method shorthand 

```javascript 
const store = {
  find(id) {
    // meh.. do something
  }
};
```

- Use property shorthand 

```javascript 
function (id, remove, add) {
  const component = {
    id,
    remove,
    add
  };
}

// mixed

const component = {
  id,
  remove,
  add,
  externalId: 9003,
  zip: zipFn
};
```

- Use spread/rest operator over Object.assign

```javascript 
const original = { a: 1 , b: 2 };
const copy = { ...original, c: 3 }; // => {a: 1, b: 2 , c: 3}
// rest operator
const { a, ...notA } = copy;
notA; // => {b: 2, c: 3}
```

##Arrays
- While creating arrays use literals

```javascript
const collection = []
```
- Use push instead of manually setting index and value

```javascript
// adding
collection.push(item);

// multiple
collection.push(a, b, c);
```
- copy , space 

```javascript
// copy new items 
const selectedItems = [ ...items]; 
```
- Array-like to Array

```javascript 
const nodes = Array.from(nodeList);
```
- Array method callbacks should always return a value

```javascript
array.map((item) => {
  // always return 
  return item;
});

array.filter((item) => { 
  return false;
});
```

## Destructuring

- Object destructuring


```javascript
// space after opening curly brace and space before closing
const { name, lastname } = person;
const label = `${ name } - ${ lastname }`; // => John Lopez
```
- Destructuring in functions 

```javascript
function getFullName({ firstName, lastName }) {
  return `${ firstName } ${ lastName }`;
}
// fat arrow arguments destructuring
element.on('click', ({ altKey, bubbles }) => console.log(altKey, bubbles));
```
- Array destructuring 

```javascript
const arr = [1, 2, 3, 4];
const [first, second] = arr;
```

- Function Parameter destructuring 

```javascript 
// Lets say you get a dom event
function foo({ target }) {
  console.log('event.target', target);
}
```
- Renaming 

```javascript 
const person = {userId: 989};
const { userId: id } = person;
console.log(id);

function findUser({ userId: id }) {
  return this.lookFor('User', {id: id});
}
```

## Strings
- Use single quotes `''`


```javascript 
const name = 'Captain John';
```

- Use template literals only for interpolation or new lines

```javascript 
const text = `This is a super long error that was thrown because of 
Batman. When you stop to think about how ${name} had anything`;
```


## Functions 
- Use function declarations 

```javascript 
function foo() {

}
// or , traceable 
const foo = function foo() {

};
```

- IIFE should be like this 

```javascript 
// Immediately Invoked Function Expression
(function () {
  console.log('Welcome to the internet');
}());
```

- Use rest shorthand instead of arguments array

```javascript 
function concatenate(...args) {
  return args.join('');
}
```

- Always put default parameters last

```javascript 
function handleStuff(name, opts = {}) {
  // ...
}
```

- Long Functions , leave a linebreak between declaration, body and return.

```javascript 
function foo(id) {
  const limit = 102;
  
  if ( id < limit) {
    // do something
  } else {
    // otherwise do this 
  }
  
  return something;
}
```
### Arrow Functions 
- Use arrow function notation for short functions, callbacks (as when passing an anonymous function )  

▣ Whitespace rule: One space before and after `∙=>∙`

```javascript 
[1, 2, 3].map((x) => {
  var y = x + 1;
  return x * y;
});
```
- If function body is one single expression omit the braces and use the implicit return 

```javascript
// one liner function omit parentheses , curly braces
[1, 2, 3].map(number => `string contains ${number}`);


[1, 2, 3].map((number, index) => ({
  index: number
}));
```
- If the function only requires one argument and doesn't use braces omit parentheses

```javascript
// good
[1, 2, 3].map(x => x * x);
```
## Classes & Constructors

- Always use class . Avoid manipulating prototype directly

```javascript
class Component {
  constructor() {
    this.enable = false;
  }
  show() {
    this.enable = true;
  }
}
```

- `extends` for inheritance 


```javascript
class Cellphone extends Device {
  voiceCall() {
    return 'calling';
  }
}
```

- Chaining 

```javascript
class Cellphone {
  requestCall() {
    // request call
    return this;
  }
  onStartCall() {
    // start call
    return this;
  }
  onEndCall() {
    // end call
    return this;
  }
}

const smartphone = new Cellphone();
smartphone
  .requestCall()
  .onStartCall(() => { .. })
  .onEndCall(() => { .. });

```

- Unnecessary 

```javascript
class Cellphone extends Device {
  constructor(..args) {
    super(..args);
  }
}
```

## Modules 
- Use import / export

```javascript
const Machine from './Machine';
const { engine } from './Machine';
export default engine;

// avoid wildcard
import * as Machine from './Machine';
```
- For consistence don't export directly from an import

▣ Whitespace rule: Spaces `{∙moduleName∙}` `{∙moduleName1,∙moduleName2∙}` 

```javascript
export { engine as default } from './Machine';
```
- Only import from one path once

```javascript
import foo, { name1, name2 } from './foo';

// if there are to much modules
import {
  mango,
  apple,
  pear, 
  banana,
  watermelon
} from './Fruits';
```
- Export only ummutable bindings

```javascript
const foo = 3;
// no semicolon in export
export { foo }
```

## Iterators 
- Use `map()`, `every()`, `filter()`, `find()`, `findIndex()`, `reduce()`, `some()` for array iteration, and `Object.keys()`, `Object.values()`, `Object.entries()` to produce arrays so you can interate over objects.

```javascript
numbers.forEach(num => sum += num);
```

- Don't use generators for now

## Properties
- Use dot notation when accesing properties

```javascript 
const name = person.name;
```

- Bracket notation for accessing properties

```javascript 
function getValue(key) {
  return object[key]; // return value
}
```
## Variables
- Always use one `const` for each variable

```javascript
const variableA = 1;
const variableB = 2;
const variableC = 3;

//avoid 
const variableA = 1,
  variableB = 2, 
  variableC = 3;

```

- Group `const`s and `let`'s

```javascript
const variableA = 1;
const variableB = 2;
let variableC = 3;
let variableD = 4;
```
## Comparison Operators & Equality

- Use `===` and `!==`
- For if statements use expression coercion for the following types 

Falsy Values  
**Undefined** evaluates to `false`  
**Null** evaluates to `false`   

Truthy values  
**Objects** evaluate to `true`  
**Arrays** evaluate to `true`  

Primitives  
**Numbers** evaluate to `false` if +0, -0 or **NaN** otherwise `true`  
**Strigns** evaluate to `false` if an empty string, otherwise `true` 

- For Objects and Arrays

```javascript 
const data = {
  person: {
    name: 'John',
    age: 10,
    children: [person1, person2]
  }
};

// good
if (data.person) {
  // true
}

// good
if (data.person.children) {
  // true
}
```

- For **Numbers** and **Strings** always compare against the values you are looking since they don't full evaluate to true or false. 

```javascript 
// name could be an empty string '' , so you can check like this

if (typeof data.person.name === 'string') {

}

// if it needs to be different from empty
if (data.person.name.length > 0) {
  // stuff 
}

```

## General AntiPatterns

#### Operators
```javascript 
// avoid this , very tricky 
foo() && bar(); 

// instead
if (foo()) {
  bar();
}
```

#### Functions 
 - Don't use Functions in a non-function block 

```javascript 
// Antipattern
if ( condition ) {
  function foo() {
    // foo function   
  }
}

// Good
function doo() {
  
  function error() {
  }
  
  function success() {
  }
}

// good
function doer() {

  if ( condition ) {
    foo();
  } else {
    bar();
  }
  
  // Try to keep your sub-functions in the bottom
  function foo () {

  }
  function bar() {
  
  }
}

```
- Never use arguments as a parameter name, it overrides arguments

```javascript 
// Wrong
function person(name, arguments) {
  // do stuff
}
```
- Don't use function constructor to create functions 

```javascript
// bad
var add = new Function('a', 'b', 'return a + b');
```
- Never reassign parameters

```javascript 
// wrong 
function fn(a) {
  a = 1;
}

// Instead 
function fn(a) {
  const newA = a || 1;
}
```

####Abuse of Ternary Operator 
The ternary operator should be used only for assignation, it should only be used for one liners as long it doens't affect the  readability and clearness. 

```javascript 
// Only for use for assignation
const size = name.length > 10 ? 'large' : 'small';

// Never do this
foo() ? bar() : doo(); 

// avoid this , it's confusing not readable 
const url = age > 18 ? (
  alert("OK, you can go."), 
  "continue.html"
) : (
  alert("You are much too young!"),
  alert("Sorry"),
  "stop.html"
);


```
####Simpler conditions

```javascript 
//avoid this, it's hard to read
if (_.find(list, function (item) {
  return compare(item.something, external);
})) {
    // Do stuff
}

// Do this 
var found = _.find(list, function (item) {
  return compare(item.something, external);
});

// Simple conditions
if (found) {
  // do stuff
} 
