# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)
# Functions

---

## Objectives
* Define a function
* Define a function with a parameter
* Define a function that operates on two parameters
* Create functions with and without return values

---

## Context

A function is a module that can store and invoke code. When writing repetitive
code, we can isolate code into **functions** in order to reduce repetition. For
example, if we needed to say "Hello World" to the screen multiple times, we can
create a function like so.

Function is synomymous with method.

This is also our first opportunity to create an *interface* for to a specific set of code.

Functions are not just about avoiding repetition, but also about creating a series of black boxes that we can hide functionality in.

We know that if a process is complex, breaking it down and also hiding or not worrying about certain actions or processes is prefered.

When we create our PB&J sandwiches, we don't worry about how the bread is baked, because we know it's taken care of and is a discreet and contained part of the process of creating the sandwich.

## Define a Function

We've been using functions already without knowing it:
```js
alert('hello');
```

Those are predefined.
But we can define our own:

```js
var greeting = function() {
  console.log("Hello World");
}

greeting();
```

---

We can **call** the function by taking the variable name and appending parentheses to the end of the function variable.

**Parts of a function**

```
function FUNCTIONNAME() {
	//CODE
}
```

---

We can also create functions that accept **parameters**, and use those parameters as variables in the function.

## Defining a function with a parameter
```js
var greeting = function(taco) {
	// anything inside of here will execute when called
	console.log("Good morning", taco);
}

var name = "Josh"
var name2 = "Brian"
greeting(name);
greeting(name2);
```

---

## Defining a function with two parameters

Functions can have multiple parameters, separated by commas.

```js
var greeting = function(person, stuff) {
	// anything inside of here will execute when called
	console.log("Good morning", person, stuff);
	console.log("person:", person);
	console.log("stuff:", stuff);
}

var name = "Josh";
var thing = "Spoon";
greeting(name, thing); // "Good morning Josh Spoon"
greeting(thing, name); // "Good morning Spoon Josh"
```

---

## Return Values

Note that functions can have **input** via parameters. They can also have **output** as return values. Returning values from a function is denoted by the keyword `return`. **Something** is always returned by the function. If you don't specify anything, it returns `undefined`.




```js

var add = function(a,b){
  return a + b;
};

add(2,3);

var number = add(2,4);

console.log( number + 3 );

// what happens when we call this?

var add = function(a,b){
  a + b;
};

```

---

With console.log

```js
// With a return value
var returnHello = function(name) {
	return("Hello, " + name);
}

console.log("with a return value:");
console.log(returnHello("jane") );

// Without a return value
var returnHello2 = function(name) {
	console.log("inside returnHello2: Hello, " + name);
}
returnHello2("nachos");
console.log("without a return value:");
console.log( returnHello2("taco") ); //will show as undefined
```


---





Note that printing something to the screen using `console.log` is not the same as returning values.

```js
var multiply = function(num1, num2) {
	console.log("inside the function");
	// return result = num1 * num2;
	return num1 * num2;
}

var firstNum = 2;
var secNum = 3;
var taco = multiply(firstNum,secNum);

console.log(firstNum + " multiplied by " + secNum + " is " + taco );
```

## Functional Patterns
Generally we will prefer that our functions operate as discreet parts.

If we want to add two numbers we can write:
```js
var result = 0;

var add = function(num1, num2){
  result = num1 + num2;
};
```

This function acts on some value defined outside of itself.

In javascript it allows you to do this and might seem tempting, but for a variety of reasons it is much better to explicitly define the inputs and outputs of a set of code. (this applies to things beyond functions as well)

The prefered way would be:
```js
var add = function(num1, num2){
  return num1 + num2;
};

var result = add(1,2);
```

This is only possible with the return keyword.

### Functions as sub-routines
Given this code that adds 2 numbers then multiplies it, then adds a string to it:
```js
// inputs
var num1 = 2;
var num2 = 4;

var result = num1 + num2;

var multiplied = num1 * num2;

var resultString = "The Result is: "+multiplied;

// output
console.log(resultString);
```

We can define each of the steps as subroutines of the main code.

Functional patterns allow us to extract that code into functions, where we define the inputs and return a value. The point of the function becomes a thing that transforms values from one state into another.

---

## Declaring functions

There are two different ways to declare a function
```js
function multiply(a, b) {
	return a * b;
}

var multiply = function(a, b) {
	return a * b;
}
```

The difference between these two is that the first one is defined at run-time, meaning that if we try to call the function before it's declared, an error will be thrown:
```js
multiply(2, 2); // ERROR

var multiply = function(a, b) {
    return a * b;
}
```

The second declaration is defined at parse-time, so we can call the function wherever we'd like.
```js
multiply(2, 2); // success

function multiply(a, b) {
	return a * b;
}
```

Despite being more flexible, the former declaration that assigns the function to a variable is more common when developing Node applications.


---

## Functions as values
Since we can assign a function to a variable, we can also assign a function anywhere else any other value would go.
```js
var multiply = function(a, b) {
    return a * b;
};
```


### Exercises

Try these examples. Paste them into your code one at a time.

Do these two examples do different things?

```js
var add = function(a,b){
  console.log( a + b );
};

var sum = add(2,2);

console.log("here is the answer: "+sum);
```

```js
var addition = function(a,b){
  return a + b;
};

var anotherSum = addition(2,2);

console.log("Answer: "+anotherSum);
```


- Change this function to add the `return` keyword.

```js
var lightsabers = function(num) {
	console.log('I have ' + num + ' lightsabers.');
}

lightsabers(2);
```

- Modify the above to pass in an object of lightsabers, and return a different value.

```js
var myLightsaberCollection = {
	blue: 1,
	green: 3
}

var lightsabers = function(lightsaberCollection) {
	//code here
}

lightsabers(myLightsaberCollection);

// Output
// I have 1 blue lightsaber and I have 3 green lightsabers
```

- execute this function

```js
var doMaths = function(a,b){
  var result = 0

  result = a + b;
  result = result + b + b + 3;

  return result;
}

var total = doMaths( 2, 3 );
console.log( total );
```


Question:
Using the chrome debugger, what is the value of the result inside the function when `i` is equal to 3?


#### Further Exercises
  - create a function named hello that prints out 'Hello World'
  - call that function

```js
var example = function() {
  \\ your code goes here
};

example();
```

1.1.2
  - create a function that takes in a string as a parameter and prints it

1.1.3
  - create a function that takes in 2 numbers as parameters and returns the product of the 2 numbers
  - add a conditional statement such that multiply will only happen if at least one of the numbers is greater than 0
  - add a conditional statement such that if the multiply does not happen, print 'Criteria not met'


1.1.5
  - create a function that converts a string into an array
  - sort the letters in alphabetical order
  - convert the array back into a string
  

<details>
<summary>Hints</summary>
  There is a string method called `.split('')`
  read more about it here
</details>


