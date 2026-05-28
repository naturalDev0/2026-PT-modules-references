# Recap 25 May 2026 - JavaScript Object Oriented Programming (OOP)

## Objects

```javascript
// Create an object
// where they represent property name and value e.g. a:"blueberry"
let berries = {
  a: "blueberry",
  b: "raspberry",
  c: "strawberry",
  d: function() { return "kiwi"}
}

// Access the value of a property
// e.g. retrieve blueberry
berries["a"]
// OR
berries.a

// NOTE: when property name is shown invalid, the dot syntax
// won't work thus require ["prop name"] to access its value.
let sample = {
  "review rating": 3
}
sample["review rating"];

// Assign new properties to existing object
sample.movieName = "kung fu panda";
sample.getMovieNameInUpperCase = function() {
  return this.movieName.toUpperCase();
}

// NOTE: Objects are considered as references.

// Traversing Objects
// Get property name
for (let prop in sample) {
  console.log(prop); // "review rating", movieName, getMovieNameInUpperCase 
}
// Get property value
for (let prop in sample) {
  // 3, "kung fu panda", function() {
  //  return this.movieName.toUpperCase();
  // }
  console.log(sample[prop]); 
}

// Nested Objects
let emp = {
  firstName:"poh",
  address: {
    buildingName: "blk 100",
    streetName: "victoria street 1",
    unitNumber: "#01-01"
  }
}
```

### Object Methods

```javascript
// retrieve all values of object
sourceObject.values()

// retrieve both property name and value of object
Object.entries(object)

// return true/false if property name exist in object
sourceObject.hasOwnProperty()

// merge two objects together
// if both objects contain same property name, the later object
// overwrites the former.
.assign(formerObj, laterObj)
```

### Object Destructuring

```javascript
let berries = {
  a: "blueberry",
  b: "raspberry",
  c: "strawberry"
}

let { a, b } = berries;
console.log(a, b); // "blueberry", "raspberry"

// Rename destructured varibles
let {a:blue, b:straw} = berries;
console.log(blue, straw);

// OR destructure as function arguments
function showBerries({a, b}) {
  return a + " " + b;  
}

console.log(showBerries(berries));
```

## Class

### Definition

* A blueprint (it defines the shape of objects),

* A factory (it creates instances),

* A namespace (it groups related behavior together)

### Defining a Class

```javascript
class Car {
  constructor() {
    this.model = "n/a";
    this.horsepower = 0;
    this.mileage = 0;
    this.chassis_color = "n/a";
    this.no_of_doors = 4;
  }
}

// this.model - A piece of data inside the class, aka Instance variable
// "n/a" - default value to this.model instance variable
// `this` refers t the new object that is being created
```

### Assign to Instance variables

```javascript
let emp = new Employee();
emp.first_name = "Ah Mao";
emp.last_name = "Lim";
```

### Methods

```javascript
class Employee {
  function getSchedule() {
    return this.schedule;
  }
}

let emp = new Employee();
emp.schedule = {monday: 8, tuesday: 8};
console.log(emp.getSchedule());
```

### Inheritance

A technique to extend resources the main/parent class has, the new sub/child class created can continue from it.

```javascript
class Employee {
  constructor(personName, certs) {
    this.personName = personName;
    this.certs = certs;
  }
}
class SoftwareDeveloper extends Employee {
  constructor(personName, certs, progLangs, projects) {
    // `super` keyword is required to call parent constructor.
    super(personName, certs);
    this.progLangs = progLangs;
    this.projects = projects;
  }
}
```

## Additional References

* [JavaScript Classes - w3schools](https://www.w3schools.com/js/js_classes.asp)