## Code naming convention

This is the set of rules for naming code constructs such as constants, variables, 
functions, function arguments, object methods and properties

## Constants

Use capitalized named constants. Remember, in js const and constant are not the same!
A constant is a primitive value that is inheriently fixed and won't be changed in feature

```ts
const CURRENT_DATE = moment().format("YYYY/MM/DD"); // bad - not a constant
const CARS_COUNT = 10; // bad - not a constant (cars count is specific to a context)
const millisecondsInDay = 86400000; // bad - constant

const MILLISECONDS_IN_DAY = 86400000; // good - constant (day has defined number of miliseconds)
const currentDate = moment().format("YYYY/MM/DD"); // good - not a constant

```

## Variables

Use meaningful and pronounceable variable names. Avoid using shortcuts

```ts
const yyyymmdstr = moment().format("YYYY/MM/DD"); // bad - hard to read
const currentDate = moment().format("YYYY/MM/DD"); // good

const c = 10 // bad
const count = 10 // good
const carsCount = 10 // great
```
Use explanatory variables, avoid using direct array indexes

```ts
const address = "One Infinite Loop, Cupertino 95014";
const addresSplitterRegex = /^[^,\\]+[,\\\s]+(.+?)\s*(\d{5})?$/;

saveCityZipCode(
  address.match(addresSplitterRegex)[1], // bad - hides method argument name
  address.match(addresSplitterRegex)[2] // bad - hides method argument name
);

const [, city, zipCode] = address.match(addresSplitterRegex) || []; // destruct city and zip code from splitted address 
saveCityZipCode(city, zipCode); // good - preserves argument names
```

Avoid Mental Mapping. Explicit is always better then implicit. Use singular version of iteratable variable in iterator function

```ts
const locations = ["Austin", "New York", "San Francisco"];
locations.forEach(l => { // bad - mental map
  doStuff();
  doSomeOtherStuff();
  // ...
  // ...
  // ...
  // Wait, what is `l` for again?
  dispatch(l);
});

locations.forEach(location => { // good - using singular version of locations
  doStuff();
  doSomeOtherStuff();
  // ...
  // ...
  // ...
  dispatch(location);
});
```

Use searchable names. Do not use magic strings, magic numbers
We will read more code than we will ever write. 
It's important that the code we do write is readable and searchable. 
By not naming variables that end up being meaningful for understanding our program, we hurt our readers.
Make your names searchable

```ts
setTimeout(blastOff, 86400000); // bad - What the heck is 86400000 for?

const milisecondsTillBlastOff = 86400000;

setTimeout(blastOff, milisecondsTillBlastOff); // good now we have more context
```
## Arrays

Arrays are an iterable list of items, usually of the same type. 
Since they will hold multiple values, pluralizing the variable name makes sense:

```ts
let fruit: Array<string> = ['apple', 'banana', 'cherry'] // bad
let fruits: Array<string> = ['apple', 'banana', 'cherry'] // good
let fruitNames: Array<string> = ['apple', 'banana', 'cherry'] // great - gives more context about what is stored in an array
```

## Booleans

Booleans can hold only 2 values, true or false. 
Given this, using prefixes like “is”, “has”, and “can” will help the reader infer the type of the variable.

```ts
const open: boolean = true; // bad
const write: boolean = true; // bad
const isNotOpened: boolean = true; // bad - false positives
const canNotWrite: boolean = true; // bad - false positives
const hasNoFruit: boolean = true; // bad - false positives

const isOpened: boolean = true; // good
const canWrite: boolean = true; // good
const hasFruit: boolean = true; // good
const popupIsOpened: boolean = true; // good, but can be only used if popup is not the main context
```

## Boolean functions

Since boolean functions checking the condition, it makes sence to place `check` prefix before function

```
const openedPopups = {
  'dummyPopup': true
}

const isOpened = (popupId: string): boolean => openedPopups[popupId] // bad - isOpen is reserved for boolean variables 
const checkIsOpened = (popupId: string): boolean => openedPopups[popupId] // good
```

## Numbers

For numbers, think about words that describe numbers. Use words like maximum, minimum, total.

```ts
const cars = 3; // bad - does not describe the number, but the object

const carsCount = 3; // good
const minCars = 1; // good
const maxCars = 5; // good
const totalCars = 3; // good
```

## Objects

If your class/object name tells you something, don't repeat that in your variable name.

```ts
const car = {
  carMake: 'Honda', // bad - car is already present in object name
  carModel: 'Accord', // bad
  carColor: 'Blue', // bad
  paintCar(color: string): void { // bad - car is already present in object name
    this.carColor = color;
  }
};

car.paintCar('Red')

const car = {
  make: "Honda", // good
  model: "Accord", // good
  color: "Blue", // good
  paint(color: string): void { // good
    this.color = color
  }
};

car.paint('Blue')
```

## Functions

Functions should be named using a verb, and a noun. 
When functions perform some type of action on a resource, its name should reflect that. 
A good format to follow is actionResource. For example, getUser

```ts
userData(userId) // bad - resource is defined twice (user and data)
userDataFunc(userId) // bad
totalOfItems(items) // bad - resource is defined twice (total and items)

getUser(userId); // good
calculateTotal(items); // good
```

When writing transformer functions, only use the resource to be transformed to in function names since
resources which would be transformed from will be passed to function as it's arguments

```ts
fromEurosToDollars(20) // bad

const priceInEuros = 20
toDollars(priceInEuros); // good
toUppercase('a string'); // good
```

## Function arguments
Limiting the amount of function parameters is incredibly important because it makes testing and modifying of your function easier. 
Having more than three arguments leads to a combinatorial explosion where you have to test tons of different cases with each separate argument.
I'ts also hard to deal with optional arguments

```ts
function createMenu(title, body, buttonText, isCancellable) { // bad - imagine you'd like to make buttonText argument as optional
  // ...
}


function createMenu({ title, body, buttonText, isCancellable }) { // good - now we can make button text optional and even reorder arguments!
  // ...
}

createMenu({
  body: "Bar",
  title: "Foo",
  isCancelable: true
});
```

References:

https://github.com/ryanmcdermott/clean-code-javascript - ['Clean Code' by Robert C. Martin](https://www.amazon.com/gp/product/0132350882/ref=as_li_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=0132350882&linkCode=as2&tag=brandonwoz-20&linkId=8af093cb2b8d9a87993f285341ff015a), 
rewritten for javascript  
https://hackernoon.com/the-art-of-naming-variables-52f44de00aad  
https://www.freecodecamp.org/news/javascript-naming-conventions-dos-and-don-ts-99c0e2fdd78a  
