
# Web Course
This is a collection of notes from some web development courses focused on **JavaScript**, **ES6** and **React**. For each section there will be links to the appropiate tutorials and other resources.

## JavaScript

These notes introduce the most important .js concepts. JavaScript was originally designed in 10 days and it is now at the core of front-end client side web development.

### Variables
We declare variables with the let and const keywords
```js
// variables in JavaScript
let name = "Bob";
const pi = 3.14;
```
To display variables to the console we can use the `console.log` method.
```js
// log variables to the console
console.log("Hello World!");
console.log(name);
```
**String interpolation** is also useful for logging multiple variables together.

```js
// string interpolation
console.log(`My name is ${name}.`);
console.log(`The constant pi is equal to ${pi}`);
```
### Strings

Strings are declared using single or double quotes.
```js
// strings in JavaScript
let string = "JavaScript is Awsome!";
```
There are a number of useful methods for working with strings.
```js
// get the length of the string
string.length();
// get the string with capital letters
string.toUpperCase();
// get the string with lower case letters
string.toLowerCase();
// trim whitespaces from the string
string.trim();
```

#### ToDo List

- [ ] String (methods)
- [ ] Numbers
- [ ] Arrays
- [ ] Objects
- [ ] Basic logic
- [ ] Functions


## ES6

These notes introduce the most modern features of JavaScript, also known as ES6. ES6 is short for ECMAScript 6. ECMA is the organization that drives .js standards forwards.

#### Template Literals
Use backticks to interpolate strings.
```js
// template literals (string interpolation)
let country = "Netherlands";
let city    = "Eindhoven";
let address = `${country}, ${city}`;
```

#### Destructuring Objects

We can destructure objects and also rename object keys.

```js
let info = {
	name: 'Apple',
	age: '1 day',
	price: 10,
	qty: 50
};

// destructure object
let {name, price} = info;
console.log(`The item ${name} has price ${price}`);
// The item Apple has price 10

// renaming keys
let {name: item, price: p} = info;
console.log(`The item ${item} has price ${p}`);
// The item Apple has price 10
```
#### Destructuring Arrays

We can destructure arrays in a similar way as we did for objects.

```js
// destructuring arrays
let names = ['Bob', 'Tylor', 'Martin', 'Rob'];

// we can get the individual items from the array
let [name1, name2, name3, name4] = ['Bob', 'Tylor', 'Martin', 'Rob'];

console.log(name4)
// Rob
```

#### Object Literals
The following two snippets of code are the same in ES6.

```js
// old syntax
function get_address(city, state) {
	let address = {city: city, state: state};
	console.log(address);
}
// call function
get_address('Austin', 'Texas');
// This will display: {city: 'Austin', state:'Texas'}
```

```js
// new syntax (with object literals)
function get_address(city, state) {
	// no need to specify keys anymore
	let address = {city, state}; 
	console.log(address);
}
// call function
get_address('Austin', 'Texas');
// This will display: {city: 'Austin', state:'Texas'}
```

#### For of Loop

The new syntax allows to iterate over collections.

```js
let values = [1, 2, 3, 4, 5];
let sum = 0;

for (let value of values) {
	sum += value
}

console.log(sum);
// This will display: 15
```

#### Spread Operator

The spread operator unwraps the values in a given array or object (does not create a reference and this is useful when we need either new arrays or object copies)

```js
// example for arrays
let values1 = [1, 2, 3, 4, 5];
let values2 = [...values1];

console.log(values1);
console.log(values2);
// This will display the following:
// [1, 2, 3, 4, 5]
// [1, 2, 3, 4, 5]

values2.push([6, 7, 8, 9, 10]);

console.log(values1);
console.log(values2);
// This will display the following:
// [1, 2, 3, 4, 5]
// [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

For using the spread operator on objects we need to make certain configurations in Babel.

#### Rest Operator

The rest operator is very similar to the spread operator. It is useful for function parameters when we do not know the actual size of the input.

```js
function get_numbers(...numbers) {
	console.log(numbers);
}

get_numbers(1, 2, 3, 4, 5);
// This will display: [1, 2, 3, 4, 5]
```

#### Arrow Functions

```js
function add_numbers(...numbers) {
	let total = numbers.reduce((x, y) => x + y);
	console.log(total);
}

add_numbers(1, 2, 3, 4, 5);
// This will display: 15
```

#### Default Parameters

We can now specify a default value for a parameter that will be used if this is not passed in the function call.

```js
function add_numbers(numbers = []) {
	let total = 0;
	numbers.forEach((number) => {
		total += number;
	});
	console.log(total);
}

add_numbers();
// This will display: 0
add_numbers([1, 2, 3, 4, 5]);
// This will display: 15
```

#### Export and Import

There are 4 types of exports:

- named exports (several per module)
- default exports (one per module)
- mixed named & default exports
- cyclical dependencies

##### Named Exports
```js
//---------- lib.js ----------
export const sqrt = Math.sqrt;
export function square(x) {
	return x * x;
}
export function diag(x, y) {
	return sqrt(square(x) + square(y));
}

//---------- main.js ----------
import { square, diag } from "lib";

console.log(square(11)); // 121
console.log(diag(4, 3)); // 5
```
Similarly we can import everything from another file.

```js
//---------- main.js ----------
import * as lib from "lib.js";
console.log(lib.square(11)); // 121
console.log(lib.diag(4, 3)); // 5
```

##### Default Exports (one per module)

With default exports we can have one export per module.

```js
//---------- myFunction.js ----------
export default function () {...};

//---------- main.js ----------
import myFunction from "./myFunction.js"; //.js extension is not mandatory
// calling the imported function
myFunction()

```
The snippet below is also equivalent.
```js
//---------- myFunction.js ----------
function myFunction() {...}

export default myFunction();

//---------- main.js ----------
import myFunction from "./myFunction.js";
// calling the imported function
myFunction()
```

##### Mixed Named and Default Exports
##### Cyclical Dependencies

#### ToDo List

- [ ] Async/Await
- [ ] Classes

## React

#### Setup
The following dependencies are necessary for building react applications.

- `react`
- `react-dom`

#### ReactDOM and JSX

```js
import React from "react";
import ReactDOM from "react-dom";

// ReactDOM.render(what to render, where to render)
ReactDOM.render(<h1>Hello world!</h1>, document.querySelector("#root"));
```

#### Functional Components

`React` convention is to start each **functional component** with a capital letter and use camel case style naming.

Each individual component can return **only** one JSX element (we can get around this by wrapping everyting inside a div tag).

```js
import React from "react";
import ReactDOM from "react-dom";

// functional component
function MyApp() {
	// returns JSX for the component
	return (
		<ul>
			<li>item #1</li>
			<li>item #2</li>
			<li>item #3</li>
		</ul>
	);
}

ReactDOM.render(<MyApp />, document.querySelector("#root"));
```

#### Moving Components into Separate Files
```js
//---------- MyInfo.js ----------
import React from "react";

function MyInfo(){
	return (
		
	);
}

export default MyInfo;

//---------- index.js ----------
import React from "react";
import ReactDOM from "react-dom";
import MyInfo from "./MyInfo.js";

ReactDOM.render(<MyInfo />, document.querySelector("#root"));
```

#### Styling React with CSS Classes
```js
//---------- MyInfo.js ----------
import React from "react";

function MyInfo(){
	return (
		<h1 className="navbar">This is the navbar of the app</h1>
	);
}

export default MyInfo;

//---------- style.css ----------
.navbar {
	background-color: grey;
}

//---------- index.js ----------
import React from "react";
import ReactDOM from "react-dom";
import MyInfo from "./MyInfo.js";

ReactDOM.render(<MyInfo />, document.querySelector("#root"));
```

#### Variables in JSX

```js
//---------- index.js ----------
import React from "react";
import ReactDOM from "react-dom";

name = "Bob"
lastName = "Peters"
ReactDOM.render(<p>Hello {`${name} ${lastName}`}</p>, document.querySelector("#root"));
```

#### Props
