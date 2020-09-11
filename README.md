# ECMAScript6 course notes

## Helper Methods

### The 'forEach' helper

When we want **iteration** over an array...

The common way with the classic _for loop_:

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

We want to double the value of every array's element.

The common way with the _for loop_:

```javascript
var numbers = [1, 2, 3];
var doubledNumbers = [];

for (var i = 0; numbers.length; i++) {
  doubledNumbers.push(numers[i] * 2);
}

console.log(doubledNumbers);

/*
Output:

> [2, 4, 6]
*/
```

Using _map_ method:

```javascript
var doubledNumbers = numbers.map(function (number) {
  return number * 2;
});
```

Other way to write this is:

```javascript
var doubledNumbers = numbers.map(number => number * 2);

/*
Output:

> [2, 4, 6]
*/
```

The "map" method creates a _new array_ with the results of the called function applied to
each one of its elements. It goes through each element of the array and apply to it the
iterator function, then returns a new value of the element that will be pushed into a
brand new array. With map we dont make changes in the existing array.

Let's look at another example:

```javascript
var cars = [
  { model: 'Buick', price: 'CHEAP' },
  { model: 'Camaro', price: 'expensive' }
];

var prices = cars.map(car => car.price);

/*
Output:

> ['CHEAP', 'expensive']
*/
```

### The 'filter' helper

We have an array of products but we want to obtain a new one with specific elements.

The common way with the _for loop_:

```javascript
var products = [
  { name: 'cucumber', type: 'vegetable' },
  { name: 'banana', type: 'fruit' },
  { name: 'celery', type: 'vegetable' },
  { name: 'orange', type: 'fruit' }
];

var filteredProducts = [];

for (var i = 0; i < products.length; i++) {
  if (products[i].type === 'fruit') {
    filteredProducts.push(products[i]);
  }
}

console.log(filteredProducts);

/*
Output:

> [{'name': 'banana', 'type': 'fruit'},
{'name': 'orange', 'type': 'fruit'}]
*/
```

Using _filter_ method:

```javascript
var filteredProducts = products.filter(product => product.type === 'fruit');

console.log(filteredProducts);

/*
Output:

> [{'name': 'banana', 'type': 'fruit'},
{'name': 'orange', 'type': 'fruit'}]
*/
```

The filter method creates a new array with every element that matches the condition
implemented by the function given. It takes each element of the array, then passes to the
iterator function and return true or false if it returns true it will be included into the
new array.

Here's a bit more complicated example:

```javascript
var products = [
  { name: 'cucumber', type: 'vegetable', quantity: 0, price: 1 },
  { name: 'banana', type: 'fruit', quantity: 10, price: 15 },
  { name: 'celery', type: 'vegetable', quantity: 30, price: 9 },
  { name: 'orange', type: 'fruit', quantity: 3, price: 5 }
];

/*Lets filter vegetables which quantity is greater that 0 and price is less than 10.*/

var cheapVegetables = products.filter(
  product => product.type === 'vegetable' && product.quantity > 0 && product.price < 10
);

console.log(cheapVegetables);

/*
Output:

> [{ name: 'celery', type: 'vegetable', quantity: 30, price: 9 }]
*/
```

Another example:

```javascript
var post = { id: 4, title: 'New Post' };
var comments = [
  { postId: 4, content: 'awesome post' },
  { postId: 3, content: 'it was ok' },
  { postId: 4, content: 'neat' }
];

function commentsForPost(post, comments) {
  return comments.filter(comment => comment.postId === post.id);
}

var commentsForFourthPost = commentsForPost(post, comments);

console.log(commentsForFourthPost);

/*
Output:

> [{ postId: 4, content: 'awesome post'}, { postId: 4, content: 'neat'}]
*/
```

### The 'find' helper

### The 'every' helper

### The 'some' helper

### The 'reduce' helper

## Const and Let variables

## Template strings

## Arrow functions
