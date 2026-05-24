# Recap 23 May 2026 - Values and Variables in JavaScript

## Variable Declarations

```javascript
// block-scoped variable that exist/confine to specific space(s).
let 
// e.g.
let day = "saturday";

// mainly used for fixed values, e.g. gst, company name, etc. 
const
// e.g.
const serviceTax = 0.1;

// function scoped variable that exist everywhere in system.
// NOT RECOMMENDED - Result in unpredictable behaviours
var
// e.g.
var company = "google inc.";
```

## Advanced Operations

### Arithmetic Operators

```javascript
// Addition
+
// Subtraction
-
// Multiplication
*
// Divide
/

// =====================

// Power
**
// e.g 2 to the power of 2 is 4
2 ** 2 // ams: 4

// Remainder - usually used to find if the number is odd or even.
// (aka modulos)
%
// e.g. the remainder of 100 divided by 3
100 % 3 // ans: 1


// Increment (for pre and post)
++
// positions
y++ // post-increment
++y // pre-increment
// e.g. which equates to...
let x = 1;
x = x + 1; // ans: 2

// Decrement (for pre and post)
--
// positions
y++ // post-increment
++y // pre-increment
// e.g. which equates to...
let x = 1;
x = x - 1; // ans: 0
```

## Type Coercion

*aka Type Conversion*.

This happens when an operator works with values of different data types.

### Example

```javascript
let age = "2" * 5;
// converts string "2" => numeric 2
// thus answer age = 10.

// Other times maybe counterintuitive
let carPlateNumber = "901" + 9;
// converts number 9 => string "9"
// thus answer carPlateNumber = "9019".
```

### Emphasis

* *Type Coercion* in JavaScript happens quite frequently and <ins>is less strict than other programming languages</ins>.

* Developers are expected to always perform type conversions when receiving raw data (e.g. `prompt` or other sources) to ensure its predictability in their types.

### Functions

```javascript
let x = Number(x); // return a copy of x as its number equivalent
let x = parseInt(x); // return a copy of x as integer
let x = parseFloat(x); // return a copy of x as float
let x = toString(x); // return a copy of x as string
```

[Refer to this link for the functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number#static_methods)

## Variable Scopes

### Scope

A set of curly braces enclosure.

```javascript
let userInput = parseInt(prompt("Enter a number: "));
// this is a scope
if (userInput > 0) {
    console.log("You have entered: " + userInput);   
}
// this is a scope
```

### Behaviors

Example 1: 

*variables declared within a scope is not accessible outside of it.*

```javascript
...
if (isRaining) {
    let closeWindow = true;
}
console.log(closeWindow); // ERROR!
```

Example 2:

*variables that exist in the same scope is accessible within.*

```javascript
let country = "singapore";
if (country === "singapore") {
    let region = "north west";
    console.log(country + " " + region); // this works
}
```

## Variable Shadowing

*(also called, name hiding)*

*despite the same variable name, the program checks for the one within its own scope.*

```javascript
let myNumber = 2;
if (myNumber > 1) {
    let myNumber = 3;
    console.log(myNumber) // output: 3
}
```

[Refer here to know more - JavaScript Scope](http://dmitripavlutin.com/javascript-scope/)

## Comparison & Logical Operators

### Comparison

```javascript
// equivalence
== 
// same value and same type
===
// not equals to
!=
// not equal value, not equal type
!==
// greater than
>
// lesser than
<
// greater than or equal
>=
// lesser than or equal
<=
```

### Logical

```javascript
// joined clause must be true too (AND)
&& 
// joined clause could be true or false (OR)
||
// NOT operator (inverse)
!
```

### Logical Short Circuit

*when JavaScript detects that an expression is going to be true/false early, it skips the other comparison.*

Assuming...

```javascript
x = 3, y = 4
console.log(x > 0 || y > 0);
// y > 0 is skipped since true OR anything will be true.
// x > 0 has already evaluated to true.
console.log(x > 10 && y > 0);
// y > 0 is skipped since false AND anything will be false.
// x > 10 has already evaluated to false.
```

### Truthy Values

*Any value that is considered equivalent to true (or truthly) with if and while so long they are not:*

* zero (`0` or `0.0`)

* `null`

* `undefined`

* Not-a-Number `NaN` 

* Empty strings `""` or `''`

#### && and || evaluation questions

```javascript
Assume, 
x = 3, y = 4, z = 0, a = 1
password = "rotiprata", email = ""

// QUESTIONS
x && y
// ans q1: 
email || password
// ans q2:
parseInt(password) || y
// ans q3:
y - a - x && 10
// ans q4:
y && true && password == "rotiprata"
// ans q5:
z + a || x + y
// ans q6:
email && password
// ans q7:
```

### Ternary Operator

*`?` symbol repesents the operator.*

```javascript
// syntax
<expression> ? <expression if true> : <expression if false>
// operator has the same precedence as the = assignment operator
// thus can be used in the following;
const trafficLight = timesUp === 0 ? "green" : "red";
```

### Order of Precedence

*subject to changes in future by the javascript community.*.

***!!! IMPORTANT TO KNOW !!!***


1. `()` brackets

2. variable substitution

3. function calls

4. arithmetic operators 
   
   1. `**`
   
   2. `/ * %`
   
   3. `+ -`

5. comparision operators
   
   1. `> < == === >=`

6. logical Operators
   
   1. `!`
   
   2. `&&`
   
   3. `||`

7. assignment `=`, ternary `?`
