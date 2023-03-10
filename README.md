<p align="center" >
  <img width="200" height="200" src="https://user-images.githubusercontent.com/115108831/213843365-56fa4f2d-b9d5-4997-88bf-7eb59bb405bb.png">
</p>

# 40 JavaScript Essential Concepts (Updating the repo everyday)


For anyone starting with Web Development, It is important to know the basics of JavaScript, but it can be confusing to figure out just where to start. That’s where this repository comes in. This repo will explain 40 of the most essential concepts that every developer should know to become a successful Javascript programmer. From data types and variables to functions and classes, this repository will cover the key concepts that one needs to know in order to master Javascript. 

Every concept covered in this repo has an Instagram Reel, please click on 🎬 in every heading.

## Table of Contents

* [Data types in JS](#types)
* [Call Stacks in JS](#stacks)
* [Primitive vs Reference types in JS](#ref-types)
* [== & === in JS](#equality)
* [Coercion in JS](#coercion)
* [Function and block scopes in JS](#scopes)
* [Nested Objects in JS](#nested)
* [function declaration vs function expression in JS](#function)
* [this, call, apply, bind in JS](#this)
* [JavaScript Engines](#engines)
* [Object.create( ) & Object.assign( ) in JS](#object-assign)
* [Object Deconstruction in JS](#deconstruction)
* [Default vs Named exports](#exports)
* [.map( ), reduce( ), filter( )](#maps)
* [the new operator](#new)
* [typeof, instanceof operator](#typeof)
* [Pure functions](#pure)
* [Higher-Order functions](#higher)
* [Side-Effects](#effects)
* [Spread Operator](#spread)






<br/>
<br/>


## <a name='types'>Data types in JavaScript</a> <a href='https://www.instagram.com/reel/Cmf0v2FoCGU/?igshid=MDM4ZDc5MmU='>🎬</a>
#### Primitive Data Types

##### Number 
Used to hold decimal value.
```js
  x = 2
```
##### String
Used to hold sequence of characters.
```js
  name = "Toronto Dev"
```
##### Undefined
Means value is not assigned.
```js
  console.log(x) // Output to web console: undefined.
```
##### Boolean
A data type accepts true, false
```js
  let isOn = true;
```
##### Null
A data type can only hold **null** value.
```js
  let x = null;
  console.log("Value of x" + x)
```
##### BigInt
Represents whole numbers larger than 2<sup>53</sup>-1.
```js
  let number = BigInt(565656565656565656656565656565656565634) 
```
##### Symbol
A built-in object whose constructor return a unique symbol.
```js
  let symbol1 = Symbol()
  let symbol1 = Symbol('baz')
  let symbol1 = Symbol('baz')
```

Primitives types are **immutable** which means they cannot be modified after creation.
- These are stored by value
```js
  let string = "who invented World Wide Web"
  string = 'Sir Tim Berners-Lee'     // We replaced the value of string variable

  // However, We cannot ALTER only REPLACE, like the example below.
  let string = 'Sir Tim Berners-Lee'
  string[0] = 's'  // Outpust -> 'Sir Tim Berners-Lee'
```


#### Non-Primitive Data types
These are the Data Types Derived from primitive Data.
##### Objects
A Javascript entity having properties and methods.
          Everything in JS is an object.
          
```js
   // Creating object with the name person
   let person = {
        firstName: "Toronto",
        lastName: "Dev",
   };

   console.log(`${person.firstName} ${person.lastName}`)
```
##### Array
Collection of items stored at contiguous memory locations.
```js
  // Empty array
  var x = new array()
  
  // Array with single numeric argument
  var y = new array(10)
  
  // Explicit values
  var z = new Array(1, 3, "Toronto")
```
Non-primitive are **mutable**, these can be modified after creation.
- These are stored by the reference
```js
  let arr = ['Toronto', 'Melbourne', 'New Delhi']
  arr[1] = 'Sydney'                // We are mutating the state of variable arr using index
```

#### The typeof operator
This operator returns a string that tells the type of js variable.
```js
  typeof "G`day" // string
  typeof 0      // number
  typeof null // object
  typeof 1n    // BigInt
  typeof true  // boolean
  typeof undefined // undfined
  typeof Symbol("id")  symbol
  typeof {}   // object
```

<br/>
<br/>

## <a name='stacks'>Call Stacks in JavaScript</a> <a href='https://www.instagram.com/reel/CmiKqgZI1br/?igshid=MDM4ZDc5MmU='>🎬</a>

A call stack is a mechanism for an interpreter (like the JS interpreter in a web browser) to keep **track** of its place in a script that calls *multiple functions* — what function is being currently run and what other functions are called within that function.

Every time you invoke a function, it gets added or *pushed* to the top of call stack. When the function returns, its removed or  *popped* out of call stack. It is like a real stack in data structure where data is pushed and popped and follows the Last In First Out (LIFO) principle.

LIFO — When we say that the call stack follows the data structure principle of Last In, First Out (LIFO), it means that the last function that gets pushed into the stack is the first to be pop out, when the function returns.

#### Call Stacks example
```js
function greetings() {
 sayHello();
}

function sayHello() {
  return "Hello!";
}

// Call the function greetings()
greetings();
```

#### Step 1

![STEP1](https://user-images.githubusercontent.com/115108831/213942291-c819376d-713b-41d5-a097-9d7dd6a9f238.png)



###### Step 2

![2](https://user-images.githubusercontent.com/115108831/213942455-d708106b-71b6-42ed-988f-1bcb93cf75b4.png)


###### Step 3

![3](https://user-images.githubusercontent.com/115108831/213942468-f16fa931-b2e5-455d-ba8a-4aa95d7e0bc9.png)

 
 ###### Step 4

![4](https://user-images.githubusercontent.com/115108831/213942469-bf049a3f-2b70-485e-a171-3bebdb08ce35.png)


<br/>
<br/>

##  <a name='ref-types'>Primitive vs Reference types in JavaScript</a>  <a href='https://www.instagram.com/reel/CmlKFQ7q_Vd/?igshid=MDM4ZDc5MmU='>🎬</a>
#### Primitive types
- strings, numbers, booleans, undefined, BigInt, symbol and null.
- Stored by the value and hence also called Value Types
- Stored (in fixed amount of memory available) on a stack.
- With each primitive data type you create, data is added to the stack.

```js
let x = 5      // Assign `5` to `x`
let y = x      // Copy the value of `x` to `y`
y = 55         // Assign `55`
console.log(x, y) // Value of => 5 and Value of y = 55
```
- When you set let y = x, it means new variable y with the value same value as x is created.
- updating one of them would not affect the other.

#### Reference Types
- arrays, functions, collections and other objects are dynamic in nature. It means they do not have a fixed size.
- Stored by the reference. 
- When you create a variable and assign it a value that is a reference data type, the computer does not directly store that data type in that variable. Instead, a pointer is assigned that points to the location of that Data type in memory.
```js
// Assign the reference of a new object to `carOne`
let carOne = {
name: 'Tesla Model 3',
year: 2021,
color: 'White'
}
/* Copy the reference of the object 
inside `carOne` to new variable `carTwo`*/
let carTwo = carOne

// Modify the contents of the object `carTwo`
CarTwo.name = 'Tesla Model S' 

cosole.log(carOne) // This carOne.name ALSO changed.
// => {name: 'Tesla Model S',year: 2021, color: 'White'}
```
- In the Snipped above, we created another object carTwo and assigned it to carOne. Since the object already exists on the heap, carOne and carTwo will both point to the same object. And the moment, we modified carTwo.name, carOne.name had the same value since It is the same object.

<br/>
<br/>


##  <a name='equality'>== & === in JavaScript</a> <a href='https://www.instagram.com/reel/CmnZoMvIrps/?igshid=MDM4ZDc5MmU='>🎬</a>
#### == double equals
- Double Equals (==) checks for value equality only.
- Before checking the values, it converts the types of the variables to match each other.
<br/>
<br/>

#### === triple-equals operator 
- Also called "Strict equals" or identically equal.
- Verify whether the variables being compared have both the same value AND the same type.
<br/>
<br/>

```js
const foo = 'Polestar'
const baz = 'Polestar'
cosole.log(foo == baz) // => true
cosole.log(foo === baz) // => true
```
The value and the type of variable are both same. Hence, the result is `true` for both.


```js
const number = 1962
const stringNumber = '1962'
console.log(number == stringnumber) // => true
console.log(number === stringnumber) // => false
```
Even though values are same, the type is not the same. Hence, **==** return `true`, however **===** checked value and type both, returned `false`.


### When should you use == and when should you use === ?
- Always use 3 equals unless you have a good reason to use 2. This helps to maintain data type integrity throughout your code and save you multiple bugs in your code.
<br/>
<br/>


- Scenarios when an API accepts both "true" and true from the client, use ==. Otherwise === is the best approach.

<br/>
<br/>

## <a name='coercion'>Coercion in JS</a> <a href='https://www.instagram.com/reel/CmsrGwyoBoR/?igshid=MDM4ZDc5MmU='>🎬</a>
- Type coercion, type conversion, typecasting, and type juggling: all different names that refer to the process of converting one data type into another.


- Type coercion in JavaScript, coerces to the string, number, and Boolean primitive types.

- You can pass `number` where a `string` is expected and a `string` where a `boolean` is expected. JS will try to convert it to right type.

- It is best to **avoid** this JS feature 


### JavaScript has two types of **coercions**
  - Implicit Coercion
  - Explicit Coercion

#### Implicit Coercion happens:

- When Javascript coerces the value type to expected behind the scenes, without developer noticing about it.

- When JavaScript operates in a wrong data type, it will try to convert the value to the right data type.

- Whenever we pass a different data type as an operand in a numeric expression using operators such as **`-, *, /, %`,** the conversion process is similar to calling the in-built Number function on the operand. If the conversion to number isn’t possible, NaN is returned.


- **Note**: The + operator works differently than the other numerical operators. It can work as both concatenation and numerical operator depending on the type of operand passed.


##### Example of Implicit Typecasting
```js

let x = 44
console.log(x + "") 
//Output=> "44" as number 44 is converted into String

console.log("14" * 3)
//Output=> 42 , 14 string is converted into number.

cosole.log(99 + undefuined)
//Outout=> NaN, undefined could not be converted to num


console.log('16' + 5)
//Output=> 165, 

console.log(null * 3)
//Output=>0, null is converted into 0.

console.log(5 * [6])
//Output=> [6] is converted into number 
```


#### Explicit Coercion happens
When type conversion is explicitly done in the code by the developer using inbuilt methods for type conversion.
- String( ) method is used to convert any other data type value to string values.
```js
  String(45) // => string "45"
  String(true) // => string "true"
```
- Boolean( ) method used to convert any data type into Boolean
```js
  Boolean(55) // => true
  Boolean("") // => false
  Boolean(" ")// => true
```
- Number ( ) method used to convert any data type to numeric value.
```js
 Number("")// => 0, "" is converted into 0.
 Number("122")//=> 122, string is converted into number
```

<br/>
<br/>

## <a name="scopes">Function and block scopes in JavaScript</a> <a href='https://www.instagram.com/reel/CmvXZ9jIg6K/?igshid=MDM4ZDc5MmU='>🎬</a>

There are 3 ways to declare variable in JS (ES6).
```js
var height = 10
let width = 300 
const key = 'abc123
```

#### var -- function scope
Variable declared using `var` will ONLY exist within the scope of function it is declared in. **However**, var created outside a function is globally scoped.
```js
function ancientKing(){
  var name = 'Porus'
  console.log(name);
}

ancientKing() // Output=> Porus

// If we try console.log outide the function
console.log(name); //Output=> name is not defined
```


##### Please note:
Statements like if-statements, loops etc — will not be considered as a scope.
```js
if(true){
  var name = 'Logan'
}

console.log(name)//Outout=> Logan
```


#### let and const -- block scope
Scope restricts the variable that is declared inside a specific block, from access by the outside of the block. 
```js
{
let name = 'Logan'
const a = 59
}

console.log(name) //Uncaught ReferenceError: name is not defined
console.log(a) //Uncaught ReferenceError: a is not defined


if(true){
    let color = 'blue'
}

console.log(color) //Uncaught ReferenceError: color is not defined
```
Above, we have used the let & const keyword to illustrate the block-level scope, in order to access the variable from outside of the block.




#### Using var can cause confusion
```js
var city = 'Toronto';

if (true) {  
  var city = 'Calgary';
  console.log(city); // 'Calgary'
}

console.log(city); // 'Calgary' 
```
In this scenario ‘Calgary’ will be printed in both places. This is because both variables are in the same scope, resulting in ‘Calgary’ overriding the first variable declaration.
##### Magic of let
```js
var city = 'Toronto';

if (true) {  
  let city = 'Calgary';
  console.log(city); // 'Calgary'
}

console.log(city); // 'Toronto' 
```


<br/>
<br/>

## <a name='nested'>Nested Objects</a> <a href='https://www.instagram.com/reel/CmxqJpjo_L5/?igshid=MDM4ZDc5MmU='>🎬</a>
- In application code, objects are often nested— an object might have another object as a property which in turn could have a property that’s an array of even more objects.
 


- These objects can be accessed through dot, bracket notations and object deconstruction.



- These nested objects are useful for storing the different properties and specifying the value based on user needs.



- If you are working with APIs, you would have to deal with nested objects. Hence, a developer must have a good understanding about the topic.

#### Example of a nested object
```js
const employeeInfo = {
    employeeName: "Alan Turing",
    employeeId: 45585,
    salary: {
        2021: "130000"
    },
    address: {
        streetName: {
            address1: "101 Queens Street
        },
        city: "Brisbane",
        state: "Queensland",
        country: "Australia"
    }
}
```

##### We can access the data above using the following:
- Dot Notation
- Bracket Notation
- Object Destructuring 


- Dot Notation: A property in an object is accessed by giving the object’s name, followed by a period, followed by the property name **(Example: employeeInfo.address)**
```js
  console.log(employeeInfo.address.city)
  // Output=> Brisbane 

  console.log(employeeInfo.employeeId)
  // Output=> 45585
```

<br/>

##### Bracket Notation

The object name is followed by a set of square brackets, with the property name specified inside the brackets via either a string **(Example: employeeInfo['address']) or a variable (Example: employeeInfo['address'])**
```js
  console.log(employeeInfo['employeeId'])
  // Output=> 45585

  console.log(employeeInfo['address']['state])
  // Output=> Queensland
```
##### Destructuring the object
The destructuring assignment syntax allows you to unpack array values or object properties into different variables.
```js
  const employeeInfo = {
    employeeName: "Alan Turing",
    employeeId: 45585,
    salary: {
        2021: "130000"
    },
    address: {
        streetName: {
            address1: "101 Queens Street"
        },
        city: "Brisbane",
        state: "Queensland",
        country: "Australia"
      }
   }

   const {salary} = employeeInfo
   console.log(salary) //Output=> {2021:'130000'}

   const  {address: {streetName} = {}} = employeeInfo
   console.log(streetName) // { address1: "101 Queens Street"}
```
<br/>
<br/>

## <a name='function'>function declaration vs function expression in JS</a> <a href='https://www.instagram.com/reel/Cm-t3hSoKNt/?igshid=MDM4ZDc5MmU='>🎬</a>
#### function declaration
- Also known function statement, declares a function.
- A declared function is “saved for later use”, and will be executed later, when it is invoked (called).
- We can declare a function in JS using keyword **function**, followed by a name, followed by parentheses ().
```js
// Declaring a function, we can invoke anytime and anywhere in our program.
function sum(a, b) { // NOT INVOKED, just declared
  return a + b
}

```

#### function expression 
- A function expression is similar to a function declaration, however function expression can be stored in a variable.

```js
const sum = function (){
             return a + b
             }
```
- Functions stored in variables do not need function names(anonymous function). They are always invoked (called) using the variable name like **`const sum`** above.

- As soon as the function is defined with an expression, it is invoked.
- After a function expression has been stored in a variable, the variable can be used as a function in our code.


#### Difference Between function expressions & function declarations
- Function declarations are hoisted, while function expressions are not, which means you can call a **function** **declaration** before it is defined, but you cannot do this with a **function expression**.
- With **function expressions,** you can use a function immediately after it is defined. With **function declarations**, you have to wait until the entire script has been parsed.
- Function expressions can be used as an **argument** to another function, but function declarations cannot.
- Function expressions can be **anonymous**, while function declarations cannot.

## <a name='this'>this, call, apply, bind in JS</a> <a href='https://www.instagram.com/reel/CnGuCQmqpxX/?igshid=MDM4ZDc5MmU='>🎬</a>
#### this ( )
- In JavaScript, **this** always refers to an object.

- **this** refers to an object which calls the function it contains.


- In the global context **this** refers to either window object or is undefined if the ‘strict mode’ is used.
```js
var car = {
  plateNumber: 'CEF158',
  maker: 'Holden', 
  
  carDetails: function(){
    console.log(this.plateNumber, this.maker)
  }
}

car.carDetails() //Output `CEF158 Holden`

var vehicleOne = car.carDetails()
vehicleOne(); // THIS WONT WORK, and BIND () CAN MAKE IT WORK

```

#### Bind( )
- With the bind() method, an object can borrow a method from another object.
```js
var car = {
  plateNumber: 'CEF158',
  maker: 'Holden', 
  
  carDetails: function(){
    console.log(this.plateNumber, this.maker)
  }
}

car.carDetails() //Output `CEF158 Holden`
var vehicleOne = car.carDetails.bind(car)//Output `CEF158 Holden
```
##### Passing parameter in bind()
```js
var car = {
  plateNumber: 'CEF158',
  maker: 'Holden', 
  carDetails: function(color){
    console.log(this.plateNumber, this.maker, color)
  }
}
var vehicleOne = car.carDetails.bind(car, "Red")
vehicleOne() // `CEF158 Holden Red`
```

#### Call ( )
- With call(), an object can use a method belonging to another object.
```js
const vehicle = {
  details: function () {
      return this.make + " " +  this.model
  }
}

const car1 = {
  make: 'Tesla',
  model: 'Model X'
}

vehicle.details.call(car1)//Output => Tesla Model X
```
**Call ( ) can accept arguments as well**
```js
const vehicle = {
  details: function (year) {
      return this.make + " " +  this.model + " " + year
  }
}

const car1 = {
  make: 'Polestar',
  model: 'Polestar 2'
}
vehicle.details.call(car1, 2022) //Output => Polestar Polestar 2 2022
```
#### Apply( )
- With the apply( ) method, you can write a method that can be used on different objects. ( *Similar to the call( )* ) 

- The only **difference** between **call ( )** and **apply ( )**
  - The call( ) method takes arguments separately.
  - The** apply( )** method takes arguments as an array.

```js
const person = {
  fullName: function(city, country) {
    return this.firstName + " " + this.lastName + "," + city + "," + country;
  }
}

const person1 = {
  firstName:"John",
  lastName: "Doe"
}

person.fullName.apply(person1, ["Oslo", "Norway"]);
//Output => John Doe, Osla, Norway
```
<br/>
<br/>

## <a name='engines'>JavaScript Engines</a> <a href='https://www.instagram.com/reel/CnYKcQVqedI/?igshid=MDM4ZDc5MmU='>🎬</a>

- A JavaScript engine is a program that interprets JavaScript code and translates it into a format that a computer can understand.
 
 - The execution of JS code is done one line-by-line and objects and variables are created as needed.

 - The main purpose of a JavaScript engine is to run the JavaScript code written by the developer, and to make sure the code is executed correctly.

- Some of the most common examples of JavaScript engines are:
   - Google V8
   - Microsoft Chakra
   - Mozilla SpiderMonkey
   - Apple JavaScriptCore.


#### Google V8
- Google's V8 JavaScript engine is a high performance, open source JavaScript engine developed by Google for use in its Chrome web browser. 


- V8 compiles JavaScript code into native machine code instead of using an interpreter, resulting in improved performance. It can also be used to execute code outside of a browser through Node.js.


- It compiles JavaScript code into native machine code units, including functions and data. This compilation process is called **‘lazy compilation’**, because it only compiles code when it is needed. This improves performance, since it doesn't need to compile code that isn't used or needed.


- It also includes many performance optimizations to improve the speed of execution and reduce the amount of memory needed to run code. This includes advanced memory management, intelligent garbage collection and compiler optimizations that reduce the size of generated code.



#### Microsoft Chakra 
- Microsoft Chakra is an open-source scripting engine designed for scripting in the Microsoft Windows environment. It is the common execution engine for JavaScript code in Microsoft Edge.


- It is designed for high-throughput, real-time performance and scalability to provide a responsive experience for users of Microsoft services such as Office, Windows, Bing, and Xbox.


-  Chakra is also optimized to ensure efficient memory usage and fast startup up times. It has a number of advanced features such as Just-In-Time compilation, a powerful debugging infrastructure, a unique memory management technology, and advanced types of JIT optimizations. 


-  Microsoft Chakra is a great tool for creating performant, modern web applications and is a great choice for developers looking to develop powerful applications with better user experiences.


#### Mozilla SpiderMonkey
- SpiderMonkey is Mozilla’s open source JavaScript engine for web browsers. 


- It is the foundation for Firefox, Mozilla’s popular web browser, and it is also used as a standalone JavaScript interpreter. 


- SpiderMonkey has many features that make it attractive to developers. The language is designed to be extensible and can be used to create web applications with high performance. 

- It has an efficient type system and provides APIs that can be used to modify JavaScript objects.


#### Apple JavaScriptCore
- Apple JavaScriptCore is a framework that is built into Apple's products, such as Safari and OS X. 


- It is a JavaScript engine that is embedded in applications, meaning that it can interpret and execute JavaScript code. 


- The JavaScriptCore framework works by taking JavaScript code and running it as a virtual machine. JavaScriptCore provides an intermediate representation of the code, which enables fast and efficient execution of the code. 


- The use of the virtual machine helps improve performance, as the JavaScript code can be interpreted and optimized once it is in the virtual machine.
<br/>
<br/>

## <a name='object-assign'>Object.create( ) & Object.assign( ) in JS </a> <a href='https://www.instagram.com/reel/Cndqon-o9LK/?igshid=MDM4ZDc5MmU='>🎬</a>

#### Object.create( )
It is a method used to create an object from an existing object. It creates a new object and sets the newly created object’s prototype to the original object.
```js
/* Let's create a car object and use it as 
prototype for our new object.*/

// create the original object
const Car = {
  type: 'Sedan',
  wheels: 4,
  color: 'black',
  engine: '2.4L'
};

// create a new object which uses Car as its prototype
const myCar = Object.create(Car);

// now myCar and Car share the same properties
console.log(myCar.type); // 'Sedan'
```

You can also use the Object.create( ) to assign the initial values of the new object.

```js
// create the original object
const Car = {
  type: 'Sedan',
  wheels: 4,
  color: 'black',
  engine: '2.4L'
};

// create a new object which uses Car as its prototype and sets the initial values
const myCar = Object.create(Car, {
  mileage: {
    value: 100
  }
});

// now myCar has the same properties as Car plus the initial mileage value
console.log(myCar.mileage); // 100
```


#### Object.assign( )
Object.assign( ) is a method that is used to copy the values of all enumerable own properties from one or more source objects to a target object. It returns the target object.

```js
// Example 1
let object1 = {
  a: 1,
  b: 2
}
let object2 = {
  c: 3,
  d: 4
}
let object3 = Object.assign({}, object1, object2);
console.log(object3); 
// Output: { a: 1, b: 2, c: 3, d: 4 }
```

```js
// Example 2
let object1 = {
  a: 1,
  b: 2,
  c: {
    d: 3
  }
}
let object2 = Object.assign({}, object1);
console.log(object2); 
// Output: { a: 1, b: 2, c: { d: 3 } }
```

<br/>
<br/>


## <a name="deconstruction">Object Deconstruction</a> <a href='https://www.instagram.com/reel/Cnn0oK0qqgp/?igshid=MDM4ZDc5MmU='>🎬</a>
- Destructuring is a JavaScript expression that allows us to extract data from arrays, objects, and maps and set them into new, distinct variables.

#### Syntax
```js
let{var1, var2} = {var1: val1,var2:val2}
  variables            Object
```
#### Examples
```js
const person = {
    firstname: 'Bruce',
    lastname: 'Wayne',
    city: 'Gotham'
};
const { firstname, lastname, place } = person;
console.log( firstname, lastname, place);
// Output Bruce Wayne Gotham
```



#### Assign new variable names
Code below destructures the object into variables with a different name than the object property:

```js
const person = {    
    firstname: 'Bruce',
    lastname: 'Wayne',
    city: 'Gotham'
};

const { firstname: fName, 
     lastname: lName, city: loc } = person;

console.log( fName, lName, loc);
// Output Bruce Wayne Gotham
```


#### Assign to a variable with default values
We can also assign default values to variables whose keys may not exist in the object we want to destructure. This will prevent our variable from having an undefined value assigned to it.
```js
const person = {  
    firstname: 'Bruce',
    lastname: 'Wayne',

};


const { firstname = 'Bruce', 
      lastname = 'Wayne', 
      city = 'Toronto' } = person;

console.log( firstname, lastname, city);
// Bruce Wayne Toronto
```
## <a name="exports">Default vs Named exports</a> <a href='https://www.instagram.com/reel/Cn6D3F9qZNn/?igshid=MDM4ZDc5MmU='>🎬</a>
####  Default vs Named exports in JS
-  The **export** declaration is used to export values from a JavaScript module.


 - Exported values can then be imported into other programs with the import declaration or dynamic import. this is done by adding **type="module"**


 -  A file can have not more than one default export, but it can have as many named exports as you like.



- There are two primary ways to export values in JS
  - Default Export 
  - Named Export

#### Default Export

- Only one default export is allowed per file. When importing, a specific name must be provided and the import must be written in the following format:

```js

// my-module.js
function sayHello() {
  console.log('Hello!');
}

export default sayHello;

// main.js
import sayHello from './my-module.js';

sayHello(); // 'Hello!'

```




#### Named Export
- Named exports allow for multiple exports from a single file.Specific exports can be imported by enclosing their names in curly braces. 


- It is important to note that the name of the imported module has to match the name of the module being exported.

```js
import { myExport } from "/modules/my-module.js";

// You can import multiple names from the same module.
import { foo, bar } from "/modules/my-module.js";

// You can rename an export when importing it. 
import { longModuleExportName as shortName } 
from "/modules/my-module.js";

```
## <a name="maps">.map( ), .reduce( ), .filter( )</a> <a href='https://www.instagram.com/reel/CoG15Q9oVan/?igshid=MDM4ZDc5MmU='>🎬</a>
#### 


#### .map ( )
- The map( ) method creates a new array populated with the results of calling a provided function on every element in the calling array.

<br/>

- Map can be used when you want to perform an action on each element in a collection, and gather the results into a new array. 

##### Examples
```js
//  Use .map() to find the square of all elements in an array:
const numbers = [1, 2, 3, 4, 5];
const squares = numbers.map(num => num * num);

// Create a new array of objects using .map() and an array of data:
const data = [
  {name: 'Alex', job: 'Engineer'},
  {name: 'Bob', job: 'Doctor'}
];
const people = data.map((person, index) => {
  const newPerson = {
    id: index + 1,
    name: person.name,
    job: person.job
  };
  return newPerson;
});
```

#### .reduce( )
- reduce takes( ) an array and reduces it into a single value. For instance, with an array of numbers you can easily find the average of all values or calculate sum of array.


##### Examples

```js

//Example 1 - Sum All Items in an Array
const numbers = [2, 3, 5, 10];
const sum = numbers.reduce((total, amount)=> total + amount);

console.log(sum);  // Output: 20

// Example 2 - Flatten an Array of Arrays
const flattened = [[0, 1], [2, 3], [4, 5]].reduce(
  (accumulator, array) => accumulator.concat(array),
  []
);

console.log(flattened);  // Output: [ 0, 1, 2, 3, 4, 5 ]
```
#### .filter ( )
- The filter( ) method creates a shallow copy of a portion of a given array, filtered down to just the elements from the given array that pass the test implemented by the provided function.


##### Examples
```js
// Filtering an array of numbers:
let numbers = [2, 4, 6, 8, 10];
let evenNumbers = numbers.filter(number => number % 2 === 0);
// evenNumbers will be [2, 4, 6, 8, 10]

// Filtering an array of objects:
let users = [
  {name: 'John', age: 30},
  {name: 'Jane', age: 25},
  {name: 'Bob', age: 32},
  {name: 'Sara', age: 20}
];

let adults = users.filter(user => user.age >= 18);
/* adults will be [{name: 'John', age: 30},
{name: 'Jane', age: 25},{name: 'Bob', age: 32}]*/
```

## <a name="new">The new operator</a> <a href='https://www.instagram.com/reel/CoTclNGoaBi/?igshid=MDM4ZDc5MmU='>🎬</a>
The new operator does 4 things:
- It creates a new, empty object.
- It adds a property onto our newly created object called “__proto__” which points to the constructor function’s prototype object.
- It binds this to our newly created object.
- It adds a return this to the end of the function, so that the object that is created is returned from the function.


#### Example
```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

//Invoke the Person constructor using new
var candidate = new Person('Logan', 28)
```
###### Behind the scenes after we run the above
- A new object is created — the candidate object.
- this is bound to our candidate object. So any references to this will point to candidate.
- Our __proto__ is added. candidate.__proto__ will now point to Person.prototype.
- After everything is done, our brand new candidate object is returned to our new candidate variable.



#### What is \__proto__
- It is an actual object that provides a way to inherit properties from JavaScript with the help of an object which is created with new. Every object with behavior associated has internal property [[prototype]].

Lets head to chrome dev tools and follow the steps below 
```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

var candidate = new Person('Logan', 28)

// open console type
candidate
```
 
In ScreenShot below, Object have proto property

<img width="253" src="https://user-images.githubusercontent.com/115108831/216867503-84dd7ccd-7a78-4435-abeb-58f9f682d9fe.png">

## <a name="typeof">typeof, instanceof Operators </a> <a href='https://www.instagram.com/reel/CogO3JjqjDq/?igshid=MDM4ZDc5MmU='>🎬</a>

#### typeof

The typeof operator returns a string indicating the type of the operand's value. Mainly primitive values such as numbers, strings, symbols, booleans, bigint and undefined values.
```js
console.log(typeof 42);// Output: "number"

console.log(typeof 'blubber');// Output: "string"

console.log(typeof true);// Output: "boolean"

console.log(typeof undeclaredVariable);// "undefined"
```
Please note that it can’t be used to check for the **null type**. 
```js
console.log(typeof null);// Output: Object
```


###### Why typeof(null) returns `Object`?
In the first implementation of JavaScript, JavaScript values were represented as a type tag and a value. The type tag for objects was 0. null was represented as the NULL pointer (0x00 in most platforms). Consequently, null had 0 as type tag, hence the **typeof** return value "object". 


#### instanceof
- instanceof checks the current object and returns true if the object is of the specified object type.
```js
// Syntax
object instanceof constructor
```
**Examples**
```js
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}
const auto = new Car('Tesla', 'Model 3', 2023);

console.log(auto instanceof Car);
// Expected output: true

console.log(auto instanceof Object);
// Expected output: true
```


- Anything Created with **new** can also Be Checked with the instanceof Operator
```js
let foo = new String('foo');
console.log(typeof foo);
console.log(foo instanceof String);
```

## <a name="pure">Pure functions </a> <a href='https://www.instagram.com/reel/Covh14kIhVb/?igshid=MDM4ZDc5MmU='>🎬</a>
- A Pure Function is a function that always returns the **same result** if the same arguments are **passed**.
- It does not depend on any **state** or data change during a program’s execution.
- It only depends on its input arguments.
- A pure function does not produce any observable side effects such as network requests or data mutation, etc.

#### Example 
```js
function calculateFederalTax( itemPrice ) {
    return itemPrice * 0.03;
    }

console.log(calculateFederalTax(34))
```
- The above function is an example of **pure function**, It will always return the same value if we pass the same argument and Its output does not depend on anything else.


#### Please note the below function is not a pure function
```js
var specialTax = 0.10
function calculateFederalTax( itemPrice ){
    return (itemPrice * 0.03) + specialTax;
    }

console.log(calculateFederalTax(34))
```

- It is not a pure function as the output is dependent on an external variable “specialTax”.
- If specialTax updated, the output is going to be different even if the itemPrice is same. 

## <a name="higher">Higher-Order functions </a> <a href='https://www.instagram.com/reel/CpDIAk6IyXB/?igshid=MDM4ZDc5MmU='>🎬</a>
- Higher order functions are functions that take other functions as arguments and/or return functions as output.
- These functions can be used to apply sequence of operations as well as for composition of expressions for evaluation.
- This ability to handle higher-order functions, among other characteristics, makes JavaScript one of the programming languages well-suited for functional programming.

#### Examples 
##### map( )
- The map( ) method is a higher-order function in JavaScript that can be used to apply a function to every element in an array:

```js
const numbers = [2, 4, 6, 8];

const evenNumbers = numbers.map(number => 
                                number * 2);
console.log(evenNumbers);//Output: [4, 8, 12, 16]
```

#### filter(  )
- The filter( ) method is another higher-order function in JavaScript that can be used to filter an array based on a condition.
```js
const numbers = [2, 4, 6, 8, 10];

const evenNumbers = numbers.filter(number
                           => number % 2 == 0);

console.log(evenNumbers);//Output: [2, 4, 6, 8, 10]
```


## <a name='effects'>Side Effects in JavaScript</a> <a href='https://www.instagram.com/reel/CpT3BU2DZLi/?igshid=MDM4ZDc5MmU='>🎬</a>
- A side effect occurs in a program whenever you use an external code in your function—which, as a result, impacts the function's ability to perform its task.

#### Code in the snippet below has 3 side-effects.

```js
let x = 5;

function sum(y) {
  return x += y;
}

```
##### Side-effect 1 - Dependency on x
- sum( ) depends on the value of x to return `x += y`, if the the x is not available, we would get an **Uncaught ReferenceError**.

```js
let x = 5;

function sum(y) {
  return x += y;
}
```

##### Side-effect 2 - Modifies External Code
- sum( ) is changing the value of exteranl variable by adding `y`, hence, sum( ) has a side effect of manipulating external code.

##### Side-effect 3 - makes sum() non-deterministic function
- A non-deterministic function—as you can never determine its output by solely reading it.



## <a name='spread'>Spread operator (...) in JS</a> <a href='https://www.instagram.com/reel/CpoSp34o_kg/?igshid=YmMyMTA2M2Y='>🎬</a>

- The spread operator is a feature in the Javascript language that enables you to expand (or "spread") an array into a list of individual values. 

- It is represented by three consecutive periods (...).

#### What `...` can do
- Copying an array
- Concatenating or combining arrays
- Using Math functions
- Using an array as arguments

#### Examples
**Copying an Array**

Using the spread operator, you can quickly make copies of an array without having to manually loop or push elements.
```js
const arr = [1, 2, 3];
const arrCopy = [...arr];
console.log(arrCopy) // [1,2,3]
```

**Array Concatenation**

The spread operator also enables you to quickly merge multiple arrays into one.
```js
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];
const arr3 = [...arr1, ...arr2];
console.log([1, 2, 3, 4, 5, 6])
```

**Spread in function calls**
```js
function myFunction(x, y, z) {}
const args = [0, 1, 2];
myFunction(...args);
```

**Using Math functions**

One of the best ways to understand the use of spread operator in JavaScript is to look at the the built-in functions Math.min( ) and Math.max( ), which both expect a list of arguments, not an array.

```js
const numbers = [37, -17, 7, 0]
console.log(Math.min(numbers)) // NaN
console.log(Math.min(...numbers)) // -17
console.log(Math.max(...numbers)) // 37
```



