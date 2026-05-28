# Recap 23 May 2026 - Arrays and Strings

## Strings

### Declaration of a String

`""` double quotes OR `''` single quotes

```javascript
let paragraph1 = "The quick brown fox jumps over the lazy dog";
let paragraph2 = 'Jack and Jill went up the hill';
```

### Escape Sequence

`\n` - Newline
`\t` - Tabs
`\v` - Vertical Tabs
`\'` - Single quote
`\"` - Double quote
`\\` - Backslash

**Example**

```javascript
// Sample - Newline
// ================
console.log("Wishing you a merry christmas\nAnd a happy new year\nfor 2020!");

// Output
// ================
I wish you a merry christmas
And a happy new year
for 2020!

// ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

// Sample - Tabs
// =============
console.log("To see a world in a grain of sand,\tand a heaven in a wild flower. — William Blake");

// Output
// =============
To see a world in a grain of sand,      and a heaven in a wild flower. — William Blake

// ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

// Sample - Vertical Tabs
// ======================
console.log("hello\vworld");

// Output
// ======================
Hello
     World!

// ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

// Sample - Single quote
// =====================
console.log('it\'s morning!');

// Output
// =====================
it's morning!

// ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

// Sample - Double quote
// =====================

// Output
// =====================

// ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

// Sample - Backslash
// ==================

// Output
// ==================
```

### Template literals (Full Text)

```javascript
let poem = `
The waves crashed violently against the jagged shore, a tireless rhythm of salt and thunder that echoed the storm brewing in my own restless heart. Above, the bruised sky bled into shades of deep violet and charcoal, swallowing the last fragile rays of a dying sun. Every gust of wind carried the bitter scent of ozone and forgotten promises, pulling at my clothes like a desperate plea to turn back. Yet, I stood frozen at the edge of the world, watching the tide erase my footprints and realizing that some paths are meant to be washed away forever.

Best,
Teachy
`;
```

### String indexing

```javascript
let message = "hello world";
```

Output `message` variable - table reference

| 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| h   | e   | l   | l   | o   |     | w   | o   | r   | l   | d   |

```javascript
// accessing one specific letter value within the array we can...
console.log(message[6]); // output gets 'w'
```

### String - length

```javascript
console.log(message.length); // output gets 11
```

### String - slicing

```javascript
let target = "good day to you";

// SLICE METHOD - PATTERN REFERENCES
// =================================
// allows us to retrieve certain string value pattern from the variable
// =================================
// Methods
// target.slice()
// target.slice(start-index)
// target.slice(start-index, end-index)
// target.slice(end-index) but using negative value
// =================================

target.slice(0, 4) // outputs "good"

target.slice(5); // outputs "day to you"

target.slice(-3); // output "you"
```

### String methods

*NOTE !!! Strings are immutable/(cannot be changed) by design.*

*All string methods always return a copy of the modified string where the original string is never changed*

*Example*

```javascript
let leaveType = "annual_leave";
// the value retrieved from .toUpperCase() method
// differs from `leaveType`
let systemFriendlyName = leaveType.toUpperCase(); // "ANNUAL_LEAVE";
```

Commonly used methods

```javascript
let website = "www.google.com"
website.toUpperCase(); // "WWW.GOOGLE.COM"
website.toLowerCase(); // "www.google.com"

let userId = " iLove2Swim1940     ";
userId.trim(); // iLove2Swim1940 - clears off whitespaces from both left and right ends

website.split("."); // ["www", "google", "com];
website.includes("g"); // true
website.indexOf("c"); // 11
```

### String concatenation

```javascript
let sent1 = "how are";
let sent2 = " you?";
console.log(sent1 + sent2); // "how are you?"
```

## Arrays

*similar to Strings. Able to use similar syntaxes to access the values stored.*

```javascript
// storing same data type values.
let listOfNumbers = [1,3,5,7,9,11];
// OR different data type values.
let listOfRandoms = [10, "go", true, 9.81];
```

#### Array Terminology

| index   | 0   | 1   | 2   | 3   | 4   | 5   |
| ------- | --- | --- | --- | --- | --- | --- |
| element | 1   | 3   | 5   | 7   | 9   | 11  |

```javascript
let listOfNumbers = [1,3,5,7,9,11];
```

#### Array Slicing

| index   | 0   | 1   | 2   | 3   | 4   | 5   |
| ------- | --- | --- | --- | --- | --- | --- |
| element | 1   | 3   | 5   | 7   | 9   | 11  |

*Example: Retrieving 1 to 5 only*

```javascript
let subArray = listOfNumbers.slice(0, 3);
```

### Array Operations

```javascript
.push(element); // insert new element from the right.
listOfNumbers(13); // [1,3,5,7,9,11,13];

.pop(); // remove element from the right and return the removed element.
let justPop = listOfNumbers.pop(); // 13
// while listOfNumbers is [1,3,5,7,9,11]

.reverse(); // reverse the elements initial order.
listOfNumbers.reverse(); // [11,9,7,5,3,1]

.indexOf(element); // return the index position of the query element.
listOfNumbers.indexOf(11); // 1

.includes(element); // return true/false (boolean) whether element exist in array.
listOfNumbers.includes(7); // true
```

#### Accessing array through iteration/loop

```javascript
// using a for loop
for (let x of [1,3,5,7,9]) {
    console.log(x);
}
// output
1
3
5
7
9
```

### Array Destructuring

Use for removing one element at a time.

```javascript
let x = [1,2,3];
let [a,b,c] = x;
console.log(a, b, c); // 1 2 3
```

### Array variable

*aka Reference variable.*

They store **REFERENCES** only to the actual data, not the data itself.

#### Implications

1. When TWO variables reference the same array, changing the array through either variable will affect the same array.

```javascript
let orderList = ["coffee", "tea", "milo", "horlick"];
let orderListA = orderList;
let orderListB = orderList;

// add new element into orderListA
orderListA.push("coke");

// orderList data is affected.
// turning to ["coffee", "tea", "milo", "horlick", "coke"];
console.log(orderListA); // shows the exact copy as orderList
```

2. When you pass a variable that holds a reference to an array to a function as an argument, you can edit the same array via that argument.

```javascript
let pricingList = [9.99, 100.99, 49.9, 30];

function modifyPricing(pricingList, newPricing) {
    pricingList.push(newPricing);
}

modifyPricing(pricingList, 1000);
console.log(pricingList); // [9.99, 100.99, 49.9, 30, 1000]
```

## Additional References

* [String, Instance Methods - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String#instance_methods)

* [Character escape: \n, etc. - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Regular_expressions/Character_escape)

* [Array, Instance Methods - JavaScript | MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#instance_methods)

* [Console - Web APIs | MDN](https://developer.mozilla.org/en-US/docs/Web/API/console)