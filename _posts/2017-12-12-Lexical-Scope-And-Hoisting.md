---
layout: post
title:  "Lexical Scoping and Hoisting"
date:   2017-12-12 12:12:12 +0000
---

This is a review of lexical scoping and hoisting for myself as I continue to work with javascript and I hope it will prove to be useful for others as well.

##Lexical Scope

Lexical scope is a way of resolving variable scoping and it is how scoping works in javascript. 

The inner functions have access to all variables 

The rules are as below:
1. Functions have access to all variable declared in its parent functions
2. When there are variables of the same name declared, the most recent one is returned.

```
//Example 1.1

const a = "global var";
function layer1() {
	const a = "layer 1 var"
	function layer2() {
		const a = "layer 2 var";
		return a;
	}

	return layer2();
}

layer1(); //=> "layer 2 var"
```
```
//Example 1.2

const a = "global var";

function layer1() {
	const a = "layer 1 var"

	function layer2() {
		return a;
	}

	return layer2();
}

layer1(); //=> "layer 1 var"
```
```
//Example 1.3

const a = "global var";

function layer1() {
	function layer2() {
		return a;
	}
	return layer2();
}

layer1(); //=> "global var"
```
```
//Example 1.4

const a = "global var";
function layer1(b) {
	const a = "layer 1 var"
	function layer2(b) {
		const a = "layer 2 var";
		return b;
	}

	return layer2(b);
}

layer1(a); //=> "layer 2 var"
```

In examples 1.1 to 1.3 we can see lexical scoping working. All variables that declared in the parent functions and globally are accessible. When there are variables of the same name, the most recent one is queried. In our example, the variable will be first looked up in layer 2, then layer 1, then within the global scope. Example 1.4 demonstrates that the function parameters belong to the same layer as the function block. It also demonstrates how variables with the same name in a parent level can be accessed through parameter passing.

##Hoisting

In javascript, at the compilation stage, certain portions of the code is hoisted to the top of the queue and compiled first before others.

| What?                         | Hoisted?      |
| :-----------------------------|:-------------:| 
| statements (no return value)  | NO            |
| expressions (has return value)| YES           |


```
//acutal code
var hello = 5; 
//the line is composed of a statement and an expression

// statement:
// var hello;
// expression:
// hello = 5; => 5

```

Similarly, functional statements aren't hoisted but functional expressions are.

Functional Statement:
```
//actual code
func();
var func = () => alert("hi")
//ReferenceError: Cannot access uninitialized variable.

//How compilers sees the code due to hoisting;
var func;
func();
func = () => alert("hi");

```

Functional Expression:
```
//actual code
func();
function func() {
	alert("hi");
}

// "Hi" alerted


//How compilers sees the code due to hoisting;
function func() {
	alert("hi");
}
func();

```

Due to the behavior above, it is recommended that variables are systemically declared at the top of the code. Additionally, const and let are suggested over var when declaring variables because variables declared with const and let aren't allowed to be referenced before they are assigned, adding a layer of check for bugs.




