# ECMAScript6 course notes

## Helper Methods

### The 'forEach' helper

When we want **iteration** over an array...

The common way with the ver classic _for loop_:

```javascript
var colors = ['red', 'blue', 'green'];

for (var i = 0; i < color.length; i++) {
  console.log(colors[i]);
}

/*
Output:

> "red"
> "blue"
> "green"
*/
```

Using _forEach_ method:

```javascript
colors.forEach(function (color) {
  console.log(color);
});

/*
Output:

> "red"
> "blue"
> "green"
*/
```

When we use forEach we pass to it a function named _callback_ as a parameter indicating
what we want to do in this iteration with the array's _current value_. In this case we
only want to see every element of the array in the console. **This function is called one
time for every element in the array.**

Other way to write this is:

```javascript
colors.forEach(color => {
  console.log(color);
});

/*
Output:

> "red"
> "blue"
> "green"
*/
```

The forEach behaves the same way for loop does but it's convenient to use it because it
uses less code.

Here's another simple example:

```javascript
/*Create an array of numbers*/
var numbers = [1, 2, 3, 4, 5];

/*Create a variable to hold the sum*/
var sum = 0;

/*Create a function to accumulate the sum of every element in the numbers array into sum*/
function adder(number) {
  sum += number;
}

/*Loop over the array calling the adder function that increments the sum variable*/
numbers.forEach(adder);

/*Print the sum variable*/
console.log(sum);

/*
Output:

> 15
*/
```

_One thing to take into account is that all of the following helpers can be refactored
into a forEach method._

### The 'map' helper

### The 'filter' helper

### The 'find' helper

### The 'every'

### The 'some' helper

### The 'reduce' helper

## Const and Let variables

## Template strings

## Arrow functions
