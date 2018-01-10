---
layout: post
title:  "About javascript asynchrony"
date:   2017-12-12 12:12:12 +0000
permalink:  about_javascript_asynchrony
---

Asynchrony is an important concept in javascript which allows single-threaded operations to behave more efficiently when dealing with code that takes longer to complete. Any code that is run on an event as opposed to running in order of the lines is asynchronous.

There are multiple reasons to have asynchronous designs. A major reason is improved efficiency. Think of an AJAX call. An AJAX call on average takes significantly longer to complete than other operations. However, after the request is sent, our thread sits idle under a synchronous design scheme, waiting for a response from the call before it proceeds. Asynchronous design allows the other code which doesn't rely on the AJAX response to run (if there are any), increasing the efficiency of our code.

Asynchronous design also provides for a better user experience since the DOM does not freeze up while running tasks like AJAX. For example, in a web text editor that autosaves, asynchronous code allows the text editor to do a AJAX PATCH request while still allowing continual editing of the text, which will present significant annoyance if the AJAX response time is long.

A concept in JS used to deal with asynchronous function is a callback. A callback is a function that is passed to another function as a parameter. Callbacks are particular useful in an asynchronous context because it notifies(calls) the JS engine to come back to the asynchronous code after it has moved on to process other code.

In the example below, when the ajax call is performed, the code returns returns immediately and runs the console.log("hi") lines below. When the ajax call provides a response, the callback fires and "ajax complete!" is printed before continuing to execute any remaining console.log("hi") lines.


Pseudo-code example of a callback:
```
function callback(resp) {
	console.log("ajax complete!")
}

//some arbitrary ajax call
ajax("url", callback);

console.log("hi")
console.log("hi")
console.log("hi")
console.log("hi")
console.log("hi")
console.log("hi")
...

```

Although asynchronous design provide advantages and are fairly indispensible for certain use cases for the modern web app, there are some interesting aspects that should be noted.

- "Race Condition"
Race conditions result when there are too asynchronous operations occuring at the same time. This is not ideal because it may lead to indeterminism in the results.

Example of Race Condition
```
let a = 1

function cb1 () {
	a += a
}

function cb2 () {
	a = a*a
}

//some ajax call that contains the functions above
ajax("url.1", cb1)
ajax("url.2", cb2)

//SCENARIO 1 RESULT
// a = 4

//SCENARIO 2 RESULT
// a = 2
```

As seen above, there are two different scenarios that can result from the code above depending on the response time of each ajax call. If cb1 is called first, scenario 1 results. If cb2 is called first, scenario 2 results. Because the two ajax calls interacts as they both manipulate variable a, indeterminism causes an issue for us and should be avoided. 

A solution can be to use jQuery.when().

```
let a = 1

function cb1 (resp) {
	a += a
}

function cb2 (resp) {
	a = a*a
}

$.when( ajax("url.1") , ajax("url.2").done( (cb1, cb2) => {
	cb1();
	cb2();
});

```



Reference:

(You Don't Know Js Chapter 1)[https://github.com/getify/You-Dont-Know-JS/blob/master/async%20%26%20performance/ch1.md]