# Recap 23 May 2026 - Functions as Values

In JavaScript, functions are treated as first-class citizens, where it's able to become the following:

* Assigned to be a variable
  `let subtract = (x,y) => x - y;`

* Passed to a function
  `array.sort(someFunction)`

* Returned from a function (following example)

```javascript
function counter() {
  let counter = 0; 
  return function() {
    counter++;
    return counter;
  }
}
```

***Why is it important?***

* Without them, callbacks, HOFs, closures, and composition would all require verbose workarounds.

## Functions as Values

#### Callback functions

*Use to modify how an algorithm works.*

Example

```javascript
let num = [-3, 10, 11, 9, 8, 5, 54, 2, 21, 33, 3];
num.sort(); // DOES NOT WORK! Because sort() is sorting by string instead of numbers.

// hence a modified function need to be introduced.
function comparator(num1, num2) {
// Returns -1, when num1 < num2
// Returns 0, when num1 = num2
// Returns 1, when num1 > num2
  return num1 - num2;
}

num.sort(comparator);
console.log(num); //  [-3,  2,  3,  5,  8, 9, 10, 11, 21, 33, 54]
```

### Anonymous functions

*Function without a name. Also, a reference value.*

Criterias:

1. Store a function as a value in a variable.

2. Pass a function as an argument by reference.

#### Arrow functions

```javascript
let sumTwoNumbers = (n1, n2) => n1 + n2;
// OR
// write this when you have more than 1 line...
let sumTwoNumbers = (n1, n2) => {
  let n1 = n1 + 10;
  return n1 + n2;
}    
// the above declaration is equivalent to... 
function sumTwoNumbers(n1, n2) {
  return n1 + n2;
}
```

## Functions as Arguments

```javascript
function makeDrinkWithRecipe(drink, recipeProcess) {
  drink = recipeProcess(drink);
  return drink;
}

let miloSuperSweet = makeDrinkWithRecipe("milo", (beverage) => {
  const sugarAmount = 2;
  for (let times = 0; times < sugarAmount; times++) {
    beverage += " sugar";
  }
  return beverage;
});

`
where,
--> drink is "milo" AND
--> the function `recipeProcess` is...
(beverage) => {
  const sugarAmount = 2;
  for (let times = 0; times < sugarAmount; times++) {
    beverage += " sugar";
  }
  return beverage;
}
thus,
drink = recipeProcess("milo"); // result in milo sugar sugar
`

console.log(miloSuperSweet); // milo sugar sugar
```

## Closure

*A closure is created when a function remembers the variables from its outer scope, even after the outer function has finished executing.*

Example ([from w3schools](https://www.w3schools.com/js/tryit.asp?filename=tryjs_function_closures5))

```javascript
function myCounter() {
  let counter = 0;
  return function() {
    counter++;
    return counter;
  };
}
const add = myCounter();
add();
add();
add();

// the counter is now 3
```

*Closures has historically been used to:*

- *Create private variables*
- *Preserve state between function calls*
- *Simulate block-scoping before let and const existed*
- *Implement certain design patterns like currying and memoization*

## Functional Programming

What is Functional Programming?

* Express processes as functions, making them reusable and generic.
- Avoid state changes and side effects

- Replaces explicit loops

Example

```javascript
// Functional Programming
let words = ['quick', 'brown', 'fox', 'jumps'];
transformedWords = words.map(w => w.toUpperCase());
console.log(transformedWords);

// Iterative Programming
let words = ['quick', 'brown', 'fox', 'jumps'];
let transformedWords = [];

for (let w of words) {
   transformedWords.push(w.toUpperCase());
}

console.log(transformedWords);
```

### Common Methods

#### Map

Transform element(s) from the array.

```javascript
let words = ['quick', 'brown', 'fox', 'jumps'];
transformedWords = words.map( w => w.toUpperCase());
console.log(transformedWords);
```

#### Reduce

Simplifying a list of elements into one element.

```javascript
let numbers = [7, 12, 50, -5, 12];
let total = numbers.reduce( (bucket, addNumber) => addNumber + bucket, 0);
// where 0 is the current starting number inside bucket,
// addNumber is the incoming numeric to add into bucket.

console.log(total); // 76
```

#### Filter

Create a new list of elements that fits the desired condition.

```javascript
let words = ['quick', 'brown', 'fox', 'jumps', 'over', 'the'];
let longWords = words.filter( word => word.length > 3)

console.log(longWords); // ['quick', 'brown', 'jumps', 'over'];
```

## Additional References

* [JavaScript Function Closures - w3schools](https://www.w3schools.com/js/js_function_closures.asp)
* [Array.prototype.reduce() - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)
* [First-class function - Wikipedia](https://en.wikipedia.org/wiki/First-class_function)
* [Higher-order function - Wikipedia](https://en.wikipedia.org/wiki/Higher-order_function)
* 