# For Interview

> By Zain Mansuri 🐉

---

>## Types of Microservices
1. All Types (FE(UI), BE(Business logic), Data Access layer) - Mini Monolith 
   1. Why is still still a "Microservice"? -- because it is service specific purpose and all layers are related to the same purpose   
2. REST API (BE, DB)
3. Socket API (Similar to REST API Service, this service (usually) does not have UI layer and it is serving its consumers via Socket Connection.)
   1. UDP -- commonly used for video/voice streaming, gaming controller data.
   2. TCP -- commonly used for realtime text messaging, push updates and etc.; more reliable than UDP, but much slower
4. Scheduler Service
   1. This service (usually) does not have open API to receive incoming communication/traffic and it used for background processing tasks in scheduled manner.
   2. In some systems it can be called CRON-Jobs or Batching-Jobs Service, or simply "Jobs Service".

---

>## JS In Detail

#### 1. Closure : A closure is a function that preserves the outer scope in its inner scope.
```javascript
// The magic of this is closure. In other words, the sayHi() function is a closure.
function greeting(message) {
   return function(name){
        return message + ' ' + name;
   }
}
let sayHi = greeting('Hi');
let sayHello = greeting('Hello');

console.log(sayHi('John')); // Hi John
console.log(sayHello('John')); // Hello John
```
2. 
   1. **Var will print the same values right ?**
```javascript
for (var index = 1; index <= 3; index++) {
    setTimeout(function () {
        console.log('after ' + index + ' second(s):' + index);
    }, index * 1000);
}
// 4
// 4
// 4
```

2. 2. Wanna print different values ?
Use Let..... WHY LET ?? using block scope what difference does it make ?
```javascript
for (let index = 1; index <= 3; index++) {
    setTimeout(function () {
        console.log('after ' + index + ' second(s):' + index);
    }, index * 1000);
}
// 1
// 2
// 3
```

    In ES6, you can use the let keyword to declare a variable that is block-scoped.

    If you use the let keyword in the for-loop, it will create a new lexical scope in each iteration. In other words, you will have a new index variable in each iteration.

    In addition, the new lexical scope is chained up to the previous scope so that the previous value of the index is copied from the previous scope to the new one.

2. 3. You can use IIF(Immigrate invoke function)
```javascript
for (var index = 1; index <= 3; index++) {
    (function (index) {
        setTimeout(function () {
            console.log('after ' + index + ' second(s):' + index);
        }, index * 1000);
    })(index);
}
// 1
// 2
// 3
```

>#### IIF : Immediately Invoked Function
```javascript
(function (hi) {
    console.log(hi); // Hello
})("Hello"); // <---- IIF
```

>#### Hoisting : Default behaviour of JS to move all declaration of function and variable move to top.
```javascript
console.log(a); // Undefined
a = 1;
a++;
var a=0;
console.log(a); // 0
```
To avoid this use "USE STRICT" <br/>

    Hoist won't work with Let & Cost

>#### Spread Operator(...) : convert array into one or more argument function call.
<ul>
<li> The spread operator is commonly used to make deep copies of JS objects. When we have nested arrays or nested data in an object, the spread operator makes a deep copy of top-level data and a shallow copy of the nested data
<ul>
    <li><b>Deep Copy:</b> Copy By Value</li>
    <li><b>Shallow Copy:</b> Copy By Reference</li>
    
```javascript
let array1 = ['h', ['e', [1, true, 9], "hello"], ['y']];
let array2 = [...array1];
console.log("Array 2 after nested copying:\n", array2); //  [ 'h', [ 'e', [ 1, true, 9 ], 'hello' ], [ 'y' ] ]
// Updating array1[0] from 'h' to 'a'
array1[0] = 'a'
console.log("Array 2 after updating array1[0] to 'a':\n", array2); // [ 'h', [ 'e', [ 1, true, 9 ], 'hello' ], [ 'y' ] ]
// Updating array1[1][0] from 'e' to 'b'
array1[1][0] = 'b'
console.log("Array 1 after updating array1[1][0] to 'b':\n", array1); //  [ 'a', [ 'b', [ 1, true, 9 ], 'hello' ], [ 'y' ] ]
console.log("Array 2 after updating array1[1][0] to 'b':\n", array2); // [ 'h', [ 'b', [ 1, true, 9 ], 'hello' ], [ 'y' ] ]
```
</ul>
</li>
</ul>


> JavaScript has private and protected properties and methods. Protected Fields are prefixed with a _; private fields are prefixed with a #. Protected fields are inherited. Private ones aren’t.</li>


>### OOP concept and use case
**The four pillars of object-oriented programming are:**
<ol>
<li> <b>Inheritance:</b> child classes inherit data and behaviors from the parent class</li>
<li> <b>Encapsulation:</b>> containing information in an object, exposing only selected information </li>
<ul>
<li>Encapsulation adds security. Attributes and methods can be set to private, so they can’t be accessed outside the class. To get information about data in an object, public methods & properties are used to access or update data.</li>
<li>Note: JavaScript has private and protected properties and methods. Protected Fields are prefixed with a _; private fields are prefixed with a #. Protected fields are inherited. Private ones aren’t.Ex. </li>

```javascript
class dog {
    _attendance = 0;
    getAge() {
        return this.calcAge();
    }
    updateAttendance() {
        //add a day to the dog's attendance days at the petsitters
        this._attendance++;
    }
}
```
**Benefits:**
<ul>
<li>Adds security: Only public methods and attributes are accessible from the outside</li>
<li>Protects against common mistakes: Only public fields & methods are accessible, so developers don’t accidentally change something dangerous</li>
<li>Hides complexity: No one can see what’s behind the object’s curtain!</li>
</ul>
</ul>
<li> <b>Abstraction:</b>> only exposing high-level public methods for accessing an object </li>
<ul>
<li>data abstraction allows developers to work with complex information without worrying about its inner workings. In this way, it helps to improve code quality and readability.</li>
<li>Abstraction also serves an important security role. By only displaying selected pieces of data and only allowing data to be accessed through classes and modified through methods, we protect the data from exposure</li>
<ul>

**Benefits:**
<li>Simple, high-level user interfaces</li>
<li>Complex code is hidden</li>
<li>Security</li>
<li>Code updates rarely change the abstraction & Easier software maintenance</li>
</ul>
</ul>

<li> <b>Polymorphism:</b>> many methods can do the same task </li>
<ul>
<li>Polymorphism means designing objects to share behaviors. Using inheritance, objects can override shared parent behaviors with specific child behaviors. Polymorphism allows the same method to execute different behaviors in two ways: method overriding and method overloading.</li>
<ul>
<li><b>Method Overriding</b>: Runtime polymorphism uses method overriding. In method overriding, a child class can implement differently than its parent class.</li>
<li><b>Method Overloading</b>: Compile Time polymorphism uses method overloading. Methods or functions may have the same name but a different number of parameters passed into the method call. </li>
</ul>
</ul>
</ol>

>### How to do Testing ? 
**White box Testing** :  COMING SOON..... ⌛ TODO
**Black box Testing** :  COMING SOON..... ⌛ TODO

>### What is Node.Js ?? [Interview-questions](https://www.interviewbit.com/node-js-interview-questions/)
<ol>

<li>Node.js is based on an event-driven architecture where I/O runs asynchronously making it lightweight and efficient</li>
<li> Node.js provides simplicity in development because of its non-blocking I/O and even-based model results in short response time and concurrent processing, unlike other frameworks where developers have to use thread management.</li>

<li>The main advantage of using promise is you get an object to decide the action that needs to be taken after the async task completes. This gives more manageable code and avoids callback hell</li> 
<li>What is event loop ? Whatever that is async is managed by event-loop using a queue and listener. </li>
So when an async function needs to be executed(or I/O) the main thread sends it to a different thread allowing v8 to keep executing the main code. Event loop involves different phases with specific tasks such as timers, pending callbacks, idle or prepare, poll, check, close callbacks with different FIFO queues. Also in between iterations it checks for async I/O or timers and shuts down cleanly if there aren't any.
<li>What is Event Emitter ?</li>
EventEmitter is a Node.js class that includes all the objects that are basically capable of emitting events. This can be done by attaching named events that are emitted by the object using an eventEmitter.on() function. Thus whenever this object throws an even the attached functions are invoked synchronously.

```javascript
const EventEmitter = require('events');
class MyEmitter extends EventEmitter {}
const myEmitter = new MyEmitter();
myEmitter.on('event', () => {
 console.log('an event occurred!');
});
myEmitter.emit('event');
```
<li>What are stubs in Node.js?</li>
Stubs are simply functions that are used to assess and analyze individual component behavior. When running test cases, stubs are useful in providing the details of the functions executed.
<li>Why is assert used in Node.js?</li>
Assert is used to explicitly write test cases to verify the working of a piece of code
<li>What is the use of the connect module in Node.js?</li>
is used to provide communication between Node.js and the HTTP module. This also provides easy integration with Express.js, using the middleware modules.
<li>What is the purpose of the crypto module in Node.js?</li>
provide cryptographic functionalities, ciphering, deciphering, signing, and hashing.
<li>What is the difference between readFile and createReadStream in Node.js?</li>
    <b>readFile:</b> This is used to read all of the contents of a given file in an asynchronous manner. All of the content will be read into the memory before users can access it.
    <br/><b>create ReadStream:</b> This is used to break up the field into smaller chunks and then read it. The default chunk size is 64 KB, and this can be changed as per requirement.
<li> What is a passport in Node.js?</li>
Passport is a widely used middleware present in Node.js. It is primarily used for authentication, and it can easily fit into any Express.js–based web application.
<li>Difference between SetTimeout() & setImmediate()</li>
<b>setImmediate()</b>:  is to schedule the immediate execution of callback after I/O events callbacks and before setTimeout and setInterval . 
 function is meant to execute a single script once the current event loop is complete.
<br/><b>setTimeout()</b>:  is to schedule execution of a one-time callback after delay milliseconds. function is used to hold a script and schedule it to be run after a certain time threshold is reached.
<li>What are some commonly used timing features of Node.js?</li>

    setTimeout/clearTimeout: This timing feature of Node.js is used to implement delays in the code execution.
    setInterval/clearInterval: The setInterval or clearInterval timing feature is used to run a code block multiple times in the application.
    setImmediate/clearImmediate: This timing feature of Node.js is used to set the execution of the code at the end of the event loop cycle.
    nextTick: This timing feature sets the execution of code at the beginning of the next event loop cycle.

<li>What is REPL? What purpose it is used for?</li>
REPL stands for (READ, EVAL, PRINT, LOOP). Node js comes with bundled REPL environment. This allows for the easy creation of CLI (Command Line Interface) applications.
</ol>


#### Problem Solving : 
   <ol>
    <li>Solved in JS <a href=https://www.scribd.com/document/477224976/Problem-Solving-2>Click here</a></li>
    </ol>
