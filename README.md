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

We want to search a value in some array and when we found it, we don't want to continue
checking the remaining ones.

The common way with the _for loop_:

```javascript
var users = [{ name: 'Jill' }, { name: 'Alex' }, { name: 'Bill' }];

var user;

for (var i = 0; i < users.length; i++) {
  if (users[i].name === 'Alex') {
    user = users[i];
    break; //Once when we find the particular user, we don't need to continue looping over the array but stop there.
  }
}

/*
Output:

>{ name: 'Alex' }
*/
```

Using _find_ method:

```javascript
users.find(user => user.name === 'Alex');

/*
Output:

>{ name: 'Alex' }
*/
```

The find method returns the value of the first element of the array that matches with the
conditional function given. With this method we walk though each element of the array,
passes the element to the iterator function and corroborates if it matches with it and
return true or false, once it returns true the find helper inmediatly exits the iteration
returning the element that it found.

Here's another example:

```javascript
var posts = [
  { id: 1, title: 'New Post' },
  { id: 2, title: 'Old Post' }
];

var comment = {postId = 1, content: 'Great Post'};

function postForComment(posts, comment) {
  return posts.find(post => post.id === comment.postId);
}

postForFirstComment = postForComment(post, comment);

/*
Output:

>{ 'id': 1, 'title': 'New Post' }
*/
```

### The 'every' helper

We want to determinate that all of the array elements satifact a condition.

The common way with the _for loop_:

```javascript
var computers = [
  { name: 'Apple', ram: 24 },
  { name: 'Compaq', ram: 4 },
  { name: 'Acer', ram: 32 }
];

var allComputersCanRunProgram = true;
var onlySomeComputerCanRunProgram = false;

for (var i = 0; i < computers.length; i++) {
  var computer = computers[i];

  if (computer.ram < 16) {
    allComputersCanRunProgram = false;
  } else {
    onlySomeComputersCanRunProgram = true;
  }
}

console.log(allComputersCanRunProgram);
console.log(onlySomeComputersCanRunProgram);

/*
Output:

>False
>True
*/
```

Using _every_ method:

```javascript
var allComputersCanRunProgram = computers.every(computer => computer.ram > 16);

console.log(allComputersCanRunProgram);
/*
Output:

>False
*/
```

The every method returns a true or false depending on _all the elements_ in the array
match the function given as parameter. Even if just only one element doesn't match it
returns false.

### The 'some' helper

The some method return true if at least one element of the array matches the condition
given by the callback function.

The common way with the _for loop_:

```javascript
var someComputersCanRunProgram = computers.some(computer => computer.ram > 16);

console.log(someComputersCanRunProgram);
/*
Output:

>True
*/
```

### The 'reduce' helper

We have every element on the array and pass it to the iterator, we also have and initial
value. The method reduce get executed and reduce the entire array into a single value.

```javascript
var numbers = [10, 20, 30];
var sum = 0;

for (var i = 0; i < numbers.length; i++) {
  sum += numbers[i];
}
```

Using _reduce_ method:

```javascript
numbers.reduce((sum, number) => {
  return sum + number;
}, 0);
```

In this case the initial value is zero. When the reduce is called it adds the first
element of the array numbers to the variable sum that its value is 0. Then asigns to sum
the value of 10, when it passes to the next element the sum variable's value is 10 and so
on.

Here's another example:

```javascript
var primaryColors = [{ color: 'red' }, { color: 'yellow' }, { color: 'blue' }];

/*We want to reduce this array of objetcs into an array of strings*/
primaryColorsString = primaryColors.reduce((accumulator, primaryColor) => {
  accumulator.push(primaryColor.color);
  return accumulator;
}, []);

console.log(primaryColorsString);

/*
Output:

>['red', 'yellow', 'blue']
*/
```

And one last example:

```javascript
function balancedParens(string) {
  return !string.split('').reduce((accumulator, char) => {
      if(accumulator < 0) {
          return accumulator;
      }
      if(char==='(') {
          return ++accumulator;
      }
      if(char ====')') {
          return --accumulator;
      }
  }, 0);
}

var unbalancedParens = balancedParens('((((');

console.log(unbalancedParens);

/*
Output:


>4
*/
```

## Const and Let variables

In modern JS we prefer using let and const for declaring variables instead of var. It
makes our code more legible and easily to read though var doesn't give us information
about the data on it.

| keyword                | const | let | var |
| ---------------------- | ----- | --- | --- |
| **global scope**       | NO    | NO  | YES |
| **function scope**     | YES   | YES | YES |
| **block scope**        | YES   | YES | NO  |
| **can be reassigned?** | NO    | YES | YES |

## Template strings

Template strings allow us to inject javascript expressions into arrays. It makes the
string much more legible.

```javascript
function getMessage() {
  const year = new Date().getFullYear();

  return `The year is ${year}`;
}

let message = getMessage();

console.log(message);

/*
Output:

>The year is 2020
*/
```

## Arrow functions
