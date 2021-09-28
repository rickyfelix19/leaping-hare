# Table of Content

1. [Introduction]()
2. [Create and Modify Properties]()
3. [Invoking Object Methods]()
4. [Beware of Globals]()
5. [Extracting Properties and Values]()
6. [Summary]()

## 1. Introduction

### Course Structure

Welcome! This course covers object-oriented programming with JavaScript. Here's a quick breakdown of what each of the lessons in the course looks like:

- Lesson 1 details how to create, access, and modify objects.
- Lesson 2 examines how JavaScript functions are first-class functions.
- Lesson 3 illustrates JavaScript's abstractions over traditional classes and inheritance.

Refresher: [Intro to JavaScript (free)](https://www.udacity.com/course/intro-to-javascript--ud803)

### Array

The array is one of the most useful data structures in JavaScript. At its core, an array is just an ordered collection of elements, enclosed by square brackets (i.e., [ and ]). Here's a variable called myArray, which is assigned to an empty array:

```js
const myArray = [];
```

Each element in an array is referenced by a numeric key called an index, which starts from zero and increments by one for each additional element in the array. Check out the following example:

```js
const fruits = ['apple', 'banana', 'orange', 'grape', 'lychee'];

console.log(fruits);
// ['apple', 'banana', 'orange', 'grape', `lychee`]

// If we want to retrieve element in fruits, we can access that element by its index:
fruits[0]; // apple
fruits[4]; // lychee
```

### Objects

The object is one of the most important data structures in JavaScript. After all, you're currently taking an entire course on object-oriented programming!

Fundamentally, an object is a collection of associated key/value pairs. We create an object with curly brackets (i.e., { and }). Here's a variable called myObject, which is assigned to an empty object:

```js
const myObject = {};

// While elements in arrays are referenced by a numeric index, keys in an object must be named explicitly, like color or year
const car = {
  color: 'red',
  year: 1992,
  isPreOwned: true
};
```

Let's break this down and see what's going on:

- The variable that is assigned to the object is named car.
- Curly brackets are used to define the car object.
- Individual keys (e,g, color) are associated with a single value ('red' in this case). These key/value pairs are connected by a colon (:).
- Each distinct key/value pair, known as a property of that object, is separated from other properties by a comma (,). The car object therefore contains three properties.

Unlike arrays, objects are unordered collections. For example, the car object above could be written with the key/value pairs in a different order, and it wouldn't change how you'd access car's items:

```js
const car = {
  isPreOwned: true,
  color: 'red',
  year: 1992
};
```

### Object Property Syntax

Another thing to note is that keys (i.e., the names of the object's properties) are strings, but quotation marks surrounding these strings are optional as long as the string is also a valid Javascript identifier (i.e., you could use it as a variable name or function name). As a result, the following three objects are equivalent:

```js
const course = { courseId: 711 }; // ← no quotes around the courseId key
const course = { courseId: 711 }; // ← single quotes around the courseId key
const course = { courseId: 711 }; // ← double quotes around the courseId key
```

You'll commonly find quotation marks omitted from property names. Certain situations require them to be included, especially if the property name:

- Is a reserved word (e.g., for, if, let, true, etc.).
- Contains spaces or special characters that cannot appear in a variable name (i.e., punctuation other than `$`, and `_` -- most accented characters).

### JavaScript Object Might Look Familiar

If you've had past experience with Python or Ruby, objects are quite similar to **dictionaries** and **hashes** (respectively). Though they may look the same, there are key differences to be mindful of.

First, Ruby hashes and JavaScript objects have similar functionality

> they are both collections of values accessible by keys.
> However, values are accessed in Ruby hashes a bit differently. Consider the following Ruby hash:

```Ruby
book = {
  title: 'To Kill a Mockingbird',
  author: 'Harper Lee',
  published: 1960
}

book{:title} # 'To Kill a Mockingbird'

# Any attempts to using JavaScript's dot notation or square bracket notation lead to undesirable results
```

The following is a valid object in JavaScript:

```js
const javascriptObject = { name: 'George Orwell', year: 1984 };

// However, it would be invalid as a Python dictionary
// Python: my_dictionary = {'name': 'George Orwell', 'year': 1984}
```

Above all else, you can also leverage objects in JavaScript not just to hold data, but for many powerful functionalities such as **constructors**.

```js
menu = {
  name: 'Salted Caramel Ice Cream',
  price: 2.95,
  ingredients: ['butter', 'ice cream', 'salt', 'sugar']
};
```

### Accessing Object Properties

How do we access their values? There are two ways: dot notation and square bracket notation.
Consider this bicycle object:

```js
const bicycle = {
  color: 'blue',
  type: 'mountain bike',
  wheels: {
    diameter: 18,
    width: 8
  }
};

bicycle.color; //blue
bicycle['color']; // blue

// Both expressions are equivalent, and will each return 'blue'.

bicycle.wheels.width; // 8
bicycle['wheels']['width']; // 8

// To retrieve the value of the width property of the object contained within bicycle's wheels property,
// in which case will return 8
```

### Summary

In JavaScript, an object is an unordered collection of properties. Each property consists of a key/value pair, and can reference either a primitive (e.g., strings, numbers, booleans, etc.) or another object. Unlike elements in an array, which are accessed by a numeric index, properties in objects are accessed by their key name using either square bracket notation or dot notation. For a closer look at object fundamentals, check out Intro to JavaScript linked below.

#### Further Reading

- [Intro to JavaScript](https://www.udacity.com/course/intro-to-javascript--ud803)
- [Unquoted property names / object keys in JavaScript](https://mathiasbynens.be/notes/javascript-properties)
- [Valid JavaScript variable names in ECMAScript 5](https://mathiasbynens.be/notes/javascript-identifiers)
- [Valid JavaScript variable names in ECMAScript 6](https://mathiasbynens.be/notes/javascript-identifiers-es6)

---

## 2. Create and Modify Properties

To create a new, blank (i.e., “empty”) object, you can use object literal notation, or the Object() constructor function. For now, just know that the following two expressions are equivalent:

```js
// Using literal notation:

const myObject = {};

// Using the Object() constructor function:

const myObject = new Object();
```

While both methods ultimately return an object without properties of its own, the Object() constructor function is a bit slower and more verbose. As such, the recommended way to create new objects in JavaScript is to use literal notation.

### Modifying Properties

Keep in mind that data within objects are mutable, meaning that data can be changed. There are a few exceptions to this, but for now, let's see how we can modify/reassign existing properties in an object.

```js

// old
const cat = {
  age: 2,
  name: 'Bailey',
  meow: function () {
    console.log('Meow!');
  },
  greet: function (name) {
    console.log(`Hello ${name}`);
  }
};

// change
cat.age += 1;
cat.age; // 3

cat.name = 'Bambi';
cat.name; // 'Bambi'

// new
{
  age: 3,
  name: 'Bambi',
  meow: function () {
    console.log('Meow!');
  },
  greet: function (name) {
    console.log(`Hello ${name}`);
  }
};
```

### Adding Properties

Properties can be added to objects simply by specifying the property name, then giving it a value. Let's start off with a blank object, then add two properties:

```js
const printer = {};

printer.on = true;

// dot notation square bracket notation works just as well:
printer.mode = 'black and white';
printer['remainingSheets'] = 168;

// likewise, we can add a method to the `printer` object in a similar manner.
printer.print = function () {
  console.log('The printer is printing!');
};

// now the printer object look as follow:
{
  on: true,
  mode: 'black and white',
  remainingSheets: 168,
  print: function () {
    console.log('The printer is printing!');
  }
}
```

### Removing Properties

Recall that since objects are mutable, not only can we modify existing properties (or even add new ones) -- we can also delete properties from objects.
Say that the printer object above actually doesn't have any modes (i.e., 'black and white', 'color', etc.).
We can go ahead and remove that property from printer using the delete operator.

```js
delete printer.mode; // true
printer.mode; // undefined, because it already has been deleted (in the previous line)
```

### Passing Arguments

#### Passing a Primitive

In JavaScript, a primitive (e.g., a string, number, boolean, etc.) is immutable.
In other words, any changes made to an argument inside a function effectively creates a copy local to that function, and does not affect the primitive outside of that function.

```js
function changeToEight(n) {
  n = 8; // whatever n was, it is now 8... but only in this function!
}

let n = 7;

changeToEight(n);
console.log(n); // 7
```

#### Passing an Object

On the other hand, objects in JavaScript are mutable. If you pass an object into a function, Javascript passes a reference to that object. Let's see what happens if we pass an object into a function and then modify a property:

```js
let originalObject = {
  favoriteColor: 'red'
};

function setToBlue(object) {
  object.favoriteColor = 'blue';
}

setToBlue(originalObject);
originalObject.favoriteColor; // 'blue'
```

> Objects in JavaScript are passed by reference, if we make changes to that reference, we're actually directly modifying the original object itself!
> What's more: the same rule applies when re-assigning an object to a new variable, and then changing that copy. Again, since objects are passed by reference, the original object is changed as well.

```js
const iceCreamOriginal = {
  Andrew: 3,
  Richard: 15
};

const iceCreamCopy = iceCreamOriginal;
iceCreamCopy.Richard; // 15
// As expected, the expression iceCreamCopy.Richard; returns 15

iceCreamCopy.Richard = 99;
iceCreamCopy.Richard; // 99
iceCreamOriginal.Richard; // 99

// Since objects are passed by reference, making changes to the copy (iceCreamCopy) has a direct effect on the original object (iceCreamOriginal) as well.
// In both objects, the value of the Richard property is now 99.
```

### Comparing an Object with Another Object

On the topic of references, let's see what happens when we compare one object with another object. The following objects, parrot and pigeon, have the same methods and properties:

```js
const parrot = {
  group: 'bird',
  feathers: true,
  chirp: function () {
    console.log('Chirp chirp!');
  }
};

const pigeon = {
  group: 'bird',
  feathers: true,
  chirp: function () {
    console.log('Chirp chirp!');
  }
};

parrot === pigeon; // false
// he expression will only return `true` when comparing two references to exactly the same object

const myBird = parrot;
myBird === parrot; // true
myBird === pigeon; // false
```

### Summary

Objects are commonly created with literal notation, and can include properties that point to functions called methods. Methods are accessed the same way as other properties of objects, and can be invoked the same way as regular functions, except they automatically have access to the other properties of their parent object.

By default, objects are mutable (with a few exceptions), so data within them can be altered. New properties can be added, and existing properties can be modified by simply specifying the property name and assigning (or re-assigning) a value. Additionally, properties and methods of an object can be deleted as well with the delete operator, which directly mutates the object.

We've modified objects quite a bit in this section, and even added new methods into them. In the very next section, we'll take a closer look at invoking these methods, as well as how these methods can directly access and modify an object itself!

### Further Reading

- [The 'delete' operator on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/delete)

---

## 3. Invoking Object Methods

### Functions vs Methods
