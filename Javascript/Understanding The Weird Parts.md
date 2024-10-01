
JS - Interpreted or Compiled Language?
- ref: https://medium.com/@osmanakar_65575/javascript-how-the-engine-compiles-6df6d5c6439c
- Static typing , dynamic typing. -> static typing, executable code can be generated at compile time. with dynamic typing, executable code cannot be generated until run time.
- binding - Binding refers to the association of names in program text to the storage locations to which they refer

- Syntax Parsers:
	- A program that reads your code and determines what it does and if its grammar or syntax is valid.
	- Compiler/ interpreter : converts human readable code to machine hardware understandable instructions.
	- this passes through a syntax parser which interprets character by character, determines keywords.
- Lexical Environments:
	- where something sits physically in the code you write. for eg :  a variable  written within a func.
	- This determines where it sits physically in computers memory.
	- lexical env is all about where a specific piece fo code is written and it's surroundings.
- Execution Contexts;
	- a wrapper to help manage the code that is running.
- Name/Value Pairs and Objects:
	- Name/Value pair:
		- eg: name = 'Pragna'
	- Object:
		- collection of Name/Value pairs, value itself can be a object again
			- eg: 
			  x
- Global Environment and Global Object:
	- the code that someone has written to parse, evaluate syntax and execute - wraps the currently running code in a execution context.
	- the base execution context of javascript program is the global execution context
	- by global -> thing that is accesible everywhere by everything in the code.
	- This global execution context creates two things ( JS engine creates)
		1. Global Object : variable accessible to all the code running in that js file in side that lexical environment 
		2.  a special variable - 'this' : is through which the global obj is accessed
		3. global obj inside browser is window object
		4. at global level, this is equals to window object
	- By global we mean - not inside a function
- Execution Context : Creating and Hoisting:
	- <img width="752" alt="Screenshot 2023-07-01 at 11 54 50 PM" src="https://github.com/user-attachments/assets/029c8f0a-c9bd-433b-be8e-3b2d6c0928ab">

	- This is because execution context is created in two phases:
		1. creation phase: we have global object and this (both setup in the memory) 
			- this is when variables and functions are given space in memory.
			- this happens as a first step of js code execution
			- but there is a diff in creation of var and func in memory. 
				- in case of functions, function and it's entirity is created in memory
				- in case of variable, var is given space in memory but not yet assigned, all varibales in javascript are initially set to undefined.
		2. Code Execution Phase:
			- this is when variables assignment happens
			- also, includes interpreting, compiling and executing 
			- interesting observation:
				- <img width="283" alt="Screenshot 2023-07-02 at 12 08 53 AM" src="https://github.com/user-attachments/assets/e3c211b4-140f-4aa9-8a81-51ad6936b248">

				  
- JavaScript and undefined:
	- undefined is a special value which indicates the values isn't been set yet
- Single Threaded, Synchronous Execution
	- Single Threaded:
		- one command at a time.
	- Synchronous:
		- one at a time and in order...
- Func Invocation and Execution Stack
	- invocation : 
		- by definition , running the func, 
		- in JS, done by using parenthesis - ()
		- what happens when we invoke a func in javascript
			- execution context is created for the func  and pushes to execution stack. the one on top is currently in execution.
   - <img width="1013" alt="Screenshot 2023-07-02 at 12 55 07 AM" src="https://github.com/user-attachments/assets/999156b2-106a-4795-a97e-68d573400a63">

			  
- The Scope Chain:
	- Reference to Outer Environment, every execution context has reference to its outer environment.
	- <img width="1447" alt="Screenshot 2023-07-02 at 1 55 46 AM" src="https://github.com/user-attachments/assets/3e01fa05-1731-4dbc-9fc6-127a725b080f">

	- the outer environment is decided based on lexical environment (where code is written)
	- here, though b is called within a, b is defined at the same level as a (at global level) => b func sits lexically not inside a but at global level
	- If a particular variable is not defined in the execution context, JS engine tries to check in it's outer reference
	- This  whole chain is called scope chain.
- Scope:
	- where a variable is available in  your code.
- var vs let:
	- with var
		- variable is given space in creation phase 
		- and assigned in execution phase.
		- and considered undefined if used before the value is assigned 
	- with let
		- variable is given space in creation phase 
		- and assigned in execution phase.
		- and throws error if used before assignment,  it is given space but javascript doesn't allow to read it.
		- accessible within the block only
			- for eg:, if let is used inside for loop, everytime the body executes, diff instances of let variable is created in memory.
		- Allows for block scoping.
- Synchronosity of JS:
	- Asynchronous : more than one at a time.
	- By nature, JAVASCRIPT IS SYNCHRONOUS, it executes one at a time.
	-  Since Javascript is synchronous, How is it handling asynchronous events?
		- for eg:, before loading the page, if we do a onclick action or an api call get's trigerred.
		- Similar to Execution Context, we have another concept called eventQueue.
		- once the entire execution context stack is done with execution, then JS Engine creates execution context for the items in event queue once by once. ( event is moved out of event queue and execution context is created)
	- Asynchronous events are mostly what happens outside the javascript engine.

---
- Types and JS:
	- Dynamic Typing:
		- we don't tell JS engine what type of data a variable holds, instead js figures out itself while the code is running
	- Primitive Types:
		- a type of data that represents a single value, i.e, not an object
		- 6 types of primitive types;
			- undefined -> represents lack of existence, not a good practice to explicitly set a variable to undefined.
			- null -> also represents lack fo existence but this can be used to assign explicitly
			- boolean -> true/false
			- number -> it's always a floating point number 
			- string => seq of characters in single/double quotes
			- symbol
	- Operators :
		- A special function that is syntactically written differently 
	- Operator Precedence and Associativity
		- operator precedence :
			- which operator func get's called first ?
			- the operator with higher precendecne gets called first
		- operator associativity :
			- what order the operator get's called in - right to left or left to right
			- left to right -> left associativity 
			- right to left -> right associativity
		- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_precedence
	- Coercion:
		- converting a value from one type to another
		- eg: var x = 1 + '2'
		- here, 1 is coerced to string and then '12' is assigned to x
		- because it is dynamically typed, coercion is a part of execution of an expression
	- Comparision Operators
		- when we give unexpected numbers to operators, it tries to coerce the operands
		- eg: 3<2<1 => return true. 
			- because both the < has same precedence, we need to follow associativity -> left to right
			- 3<2 is false ==> 0 < 1 ==> true
		- while comparing, == tries to coerce the values if both operands don't belong to same type, where as === doesn't coerce the values.
		- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Equality_comparisons_and_sameness

---
- Objects and Functions
	- Objects and the Dots:
		- left to right precedence
	- Object literal syntax
		- JSON is different from plain JS objects. JS has built in functionality to translate between two. this is the reason why we are able to do JSON.stringify and JSON.parse etc.
		- https://medium.com/geekculture/json-object-v-javascript-object-f00ae788cc1f#:~:text=A%20Javascript%20object%20has%20a,braces%20and%20key%2Fvalue%20pairs.&text=The%20main%20difference%20in%20syntax,string%20written%20with%20double%20quotes.
	- Functions are Objects/Values:
		- First class Functions:
			- Java script is the one of the languages which has first class functions.
			- anything that you can do with other types ( like strings, objects) can be don with Functions - assigning, passing them around, creating them on the fly etc.
			- Function is a special type of Object, on which all functions that we do on Object can be performed along with few more.
			- name property-> optional, can be anonymous
			- code property -> this is invocable. 
		- Properties can be assigned to functions.
		- <img width="223" alt="Screenshot 2023-10-12 at 12 28 49 AM" src="https://github.com/user-attachments/assets/2eaf6a17-b6bf-474e-b227-d02f9c9f8735">

		  when annymous functions are created, they are given space first and then assigned like variables. and function hoisting is not applicable.
		  <img width="458" alt="Screenshot 2023-10-13 at 1 00 31 PM" src="https://github.com/user-attachments/assets/a77cfac9-207b-4ddc-be35-fe9f785628fa">
    <img width="225" alt="Screenshot 2023-10-13 at 1 09 01 PM" src="https://github.com/user-attachments/assets/54de0ed6-46bd-41ef-815f-12c0e5e3055b">

		- function can be created on fly and can be passed as object, invoked later on - same behaviour as objects - first class functions
	- Pass by Value & Pass by Reference:
```
// pass by value
var a = 3;
var b = a;
a = 1
console.log("a b ", a, b) // 1 3
// pass by reference (all obejcts (including functions))
var c = {
    'abc':123
}
var d = c
c.abc = 456
console.log("d c ",d,c) //  { abc: 456 } { abc: 456 }
// equals operator creates new memory space 
c =  {
    'def':567
}
console.log("d c ",d,c) // { abc: 456 } { def: 567 }
```
	- Objects and 'this':
		- this refers to global/window object when used directly in functions etc.
		- But when it's written within an object, it refers to the object that it is in.
	- Arrays: JS array can hold values of multiple types
	- Arguments & Spread:
		- arguments keyword - which has list of all arguments passed to a function and performs all operations as JS Array
		- <img width="452" alt="Screenshot 2023-10-13 at 5 10 21 PM" src="https://github.com/user-attachments/assets/cf14977c-9321-4072-81b9-740bd0825b38">

	- Immediately Invoked Functions Expressions (IIFEs):
		- To invoke a function as soon as it's defined.
	- Closures:
		- ![image](https://github.com/user-attachments/assets/2796f2dc-0e76-4ef1-a9cf-2484adcc3ef0)

		- A closure is a feature of JavaScript that allows inner functions to access the outer scope of a function. Closure helps in binding a function to its outer boundary and is created automatically whenever a function is created.
		- when a function is defined within another function, it has access to all the outer execution context variables.
		- https://www.udemy.com/course/understand-javascript/learn/lecture/2562690#content - good examples
	- Factory Functions:
		- https://www.geeksforgeeks.org/what-are-factory-functions-in-javascript/
		- When a function is enclosed in another function, then reference to the outer world is maintained via memory spaces though execution context is removed. function along with the outer world variable memory creates a closure.
	- Closures and Callbacks
		- setTimeout etc runs Asynchronously on Event loop - what if outer variables are used with in these callbacks, it works in the same way as above, it has closure to those outer variable memory spaces.
		- Call back function: a function when you give to another function to run when other function is finished.
	- Call(), Apply() and bind()
		- All functions along with name and code properties, they also have apply, call, bind methods which can be invoked.
		- when a function is defined with in an object, then "this" points to the parent object and not window object.
		- bind()
			- object, whatever we want to be this variable in that function can be passed as parameter.
			- bind creates a copy of the function, which needs to be assigned. 
		- call()
			- unlike bind, it executes the function without creating the copy of it.,  invokes function.
			- takes, the value of this as first argument and followed by other paramters of the function.
		- Apply()
			- takes, the value of this as first argument and array of other paramters of the function as second argument.
			- could be useful when sending lot of paramters like for mathematical operations etc
		- Function Borrowing
			- apply/ bind can be applied on the borrowed funcitons as well. 
			- borrowed funcitons? -> which are taken from an object,
				- eg: x = { fun1: function(){}}
				- x.fun1.apply(y) can be done.
		- Function Currying
			- creating a copy of func but with a preset values of parameters.
			- bind takes multiple arguments, where 1st arg is the value of this keyword and rest are static values given to other params.
		- <img width="777" alt="Screenshot 2023-10-23 at 4 09 12 PM" src="https://github.com/user-attachments/assets/4abebd86-06c8-430c-b154-2a01c73ae076">

	- Functional Programming:
		- entire code in terms of functions, can be achieved with first class functions
		- modular programming, which makes code more reusable.
		- https://www.freecodecamp.org/news/functional-programming-in-javascript/
---

Functional Programming with Javascript

- Higher Order Functions:
	-  
---

OOPs
- Inheritence:
	- one object gets access to methods and properties of another object
	- classical inheritence
	- Prototypal Inheritence
- Protype
	- all objects have an additional property - proto, simply a reference to another obj and call it's proto.
	- prperties/methods can also be attached again to prototype object.
	- a property attached to prototype property need not be accessed as obj.prototype.prop -> it can be accessed as obj.prop
	- JS starts search at the top of chain and walks its way down, and stops when it finds the first time its looking for.
- Everything is an Object( or primitive)
	- Every Object has a default protoType - Base Object
	- Every Function has a default protoType - Base Function - up on which apply(), bind(), call() etc are defined.
	- <img width="731" alt="Screenshot 2023-10-24 at 3 27 32 PM" src="https://github.com/user-attachments/assets/07cf96ca-b8e9-4bad-9d4a-3b643426047b">

	- That's how default properties or methods like push, remove, concat etc are avaiable to the variable though we don't explicitly set them, cause JS takes care of it, by setting and making them accessible using prototype.
- Reflection and Extend:
	- _.extend 
		- Shallowly copy all of the properties in the source objects over to the destination object, and return the destination object. Any nested objects or arrays will be copied by reference, not duplicated. It's in-order, so the last source will override properties of the same name in previous arguments.
	- when obj1 extends another object, then to know whether a property is an immediate property of obj1 or a property of any prototype though prototype chain, "hasOwnProperty" can be used, it returns true if it's immediate property.



---

Building Objects
- Function Constructors, 'new' keyword - ways of creating objects
	- one way of creating objects is using object literal syntax.
	- using "new" keyword:
		- eg: const x = new y();
		- new is an operator which creates an empty object.
		- now, upon that y func is called and with in y -> this.prop1,this.prop2 etc are set.
		- with in y, this points to the new ibject that was created by new.
		  <img width="499" alt="Screenshot 2023-10-24 at 4 21 25 PM" src="https://github.com/user-attachments/assets/cdc58baf-60e6-480a-a818-5d554d316d05">

		- But if we explicitly return an object, then that's what get's assigned to x. If any other type liek string is returned from function, then this will be considered.
		- function constructors are just functions, before which new keyword is used.
		- these can take parameters.
	- how to set protoType to these objects created with function constructors?
		- for all functions , along with code, name properties, it has protoType property which starts it's as an empty object., used only when function is used to create objects.
		- add more properties or functions to function constructor later on using funcName.prototype.xyz = 'abc' -> here prototype is a property of function and not the __proto__ of object.
		- why can't these properties be added to fun1 function constructor only ? this is because the properties defined with in the function constructor takes up new space for every new obj that is created, memory consuming. whereas the properties defined using .prototype. will get created only once in memory and all objects will point to same memory space to access that property.
- Built - In Function Constructor
	- const x = new Number() -> now x.prototype has all the built in functions, 
	- new methods can also be added and used. 
	- x.newMethod() works but if const y = 7 and y.newMethod() doesn't work, as JS is not smart enough to consider 7 as an object.
	- <img width="245" alt="Screenshot 2023-10-25 at 8 46 59 PM" src="https://github.com/user-attachments/assets/452b7fc1-447f-4edc-8d21-393435972029">

- Object.create()
	- another way of creating objects 
	- const x = Object.create(person) 
	- <img width="250" alt="Screenshot 2023-10-26 at 7 45 53 PM" src="https://github.com/user-attachments/assets/54860adf-6ec9-409b-aa3b-92f216f07460">

	  now person will be attached as prototype to the x and what ever are direct properties will remain a direct properties.
- PolyFill
	- code that adds a feature which engine may lack.
- ES6 and Classes
	- classes can be created in ES, Extends sets the prototype.
---
Odds and Ends
- type of, instance of
	- instance of is used with prototype chain
	- type of null is an object

---
JQuery
- a Javascript library which helps query and manipulate the DOM Tree.
- https://github.com/jquery/jquery/tree/main/src
- Method Chaining:
	- calling one method after the other on the same object in a row.
		- eg: obj.method1().method2().method3(), where all 3 methods points to the same this object which is obj.
---
- when we write typescript code, it internally transpiles to javscript and runs. 
- ES6 Features - https://github.com/lukehoban/es6features
---
Callback Hell
- 
---
Promises, Async, Await
- Javascript is by default - single threaded and synchronous -> runs one at a time, in order.
- Promises:
	- a standard approach to deal with asynchronous events and callbacks.
	- by definition: The Promise object represents the eventual completion (or failure) of an asynchronous operation and its resulting value.
	- In other terms, Promise is a container for a future value
	- anything that is returns with in .then() is wrapped within a promise, which needs to be resolved again.
	- PromiseObject has 3 main properties:
		- Promise State:
			- there are 3 states of promise
				- pending - before the promise is resolved.
				- fulfilled - promise resolved and returns a value without error - then control goes to .then()
				- Rejected - promise rejected because of some error or exception - then control goes to catch()
		- PromiseResult:
			- the value that will be returned by the promise.
		- Prototype:
			- <img width="443" alt="Screenshot 2023-10-29 at 1 34 44 PM" src="https://github.com/user-attachments/assets/8594af68-beb5-4bfa-a093-88e0059d493a">

		- 
	- Promise is immutable.
- Promise Chaining of multiple async operations
	- whenever we do chaining, we should keep returning values in each then(), then only next then will have something in value
	- If we have one catch at the end, then it is responsible for all then's on top of it in the chain.
	- if we have a catch in between then's then the "then" which is next to this catch will be definitely called no matter what.
	- 
- Async Function:
	- always returns a promise
	- If we return a non promise - like any string or number , then the value will be wrapped in a promise and it returns, will needs to be resolved using .then()
	- If we return a promise, then it will not be wrapped in other promise, it returns as is.
- async await are used to handle promises.
	- how we used to handle promises before async await:
		- using .then()
	- await is used infront of a promise that needs to be resolved.
	- eg: let x = await prom ; => x has the resolved value of promise prom.
	- await is a keyword that can be used only inside async functions.
- why async await is needed:
	- it suspends the func execution until promise is resolved.
- Error handling with async await:
	- for normal promises handling with .then() -> we use .catch()
	-  for async await ->One way is to  use try catch to handle errors.
	- Other way is to use .catch over the async func:
		- eg: async func1(){}
		- func1().catch()
		- since func1 is an async function, it always returns promise.
- async await is just an syntactic sugar over promise, behind the scenes it uses promises .then() only.
---

WEB WORKERS
1. script that runs in seperate thread for browser.
2. helps with multi threading
3. diff global context - other than window
4. No Access to DOM.
5. long / computation intensive tasks - offload to Worker thread

---

Internals of JS 

- Javascript is a single-threaded, non-blocking, asynchronous programming language.
- How could a single-threaded program, be non-blocking? How could it also be asynchronous?


JS Runtime

- It's a combination of 4 : (with context to browser)
	- JS Engine
	- Web APIs
	- Callback Queue
	- The event loop


JS Engine

- brain of JS Runtime, where it executes the human redable js code.
- it takes care of call stack, execution contexts, garbage collection etc.
- Any JavaScript engine typically contains a call stack and a heap. 
	- The call stack is where the code is executed. 
	- The heap is an unstructured memory pool that stores all the objects needed for the application.
- ![image](https://github.com/user-attachments/assets/7c7090e6-724a-4881-b83e-09173eb93102)

- 

































