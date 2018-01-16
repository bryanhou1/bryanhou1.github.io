---
layout: post
title:  "Await/Async Quick Start"
date:   2018-01-15 14:11:14 -0500
permalink:  Await:Async_Quick_Start
---

While working on a code challenge recently, I was faced with a task I haven't encountered before. Part of the challenge requires doing multiple ajax requests to fetch information. However, prior to the first request you do not know how many requests are required.

See following json response as a sample.

when posting an ajax request to someurl?id=1&page=1, the response if the Promise is resolved successfully is as below:
```
{
  "data":[
    {"id":1,"name":"Amy"},
    {"id":2,"name":"George"},
    {"id":3,"name":"Preety"},
    {"id":4,"name":"Mike"},
    {"id":5,"name":"Kim"}
  ],
  "pagination":{
    "per_page":4,
    "total":15
  }
}
```

According to the above example, in order to obtain all of the data, we will have to make 4 total requests to obtain the full set of data. However, we do not know that prior to the first AJAX returns successfully.

I thought it would be ideal opoprtunity to implement the solution with javascript await/async. We will be going through how to implement a solution to the problem and hope we will solve the problem.

## Why use await/async
Async/await are built on promises. Async functions returns a promise, while await returns when the promise is resolved. This behavior allows your code to look a lot more synchronous and is much easier to manage and debug than callback or simple promises. (This article)[https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9] speaks in depth and have specific example that compares the two.

## Implementing our solution

1. We start by writing a ajax function to access the API.

```
const fetchData = async (page) => {
  try {
    const content = await fetch(`someurl?id=1&page=${page}`);
    const json = await content.json();
    return json;
  } catch(err) {
    console.log(err)
  }
}

```

2. calculate the amount of remaining fetches required

```
const makeRequest = async () => {
  const firstFetch = await fetch(1);

  //counter to calculate remaining fetches required
  const counter = Math.ceil(firstFetch.pagination.total/firstFetch.pagination.per_page)-1;
}
```

3. write function to perform the remaining fetches
```
const fetchRemaining = async (counter) => {
  const collection = [];
  for(let i=0; i < counter; i++){
   collection[i] = await fetchData(i+2);
  }
  return collection;
}
```

4. add fetchRemaining to makeRequest and return the results, we have:

```
const makeRequest = async () => {
  const firstFetch = await fetchData(1);
  const counter = Math.ceil(firstFetch.pagination.total/firstFetch.pagination.per_page)-1;
  const remainingFetch = await fetchRemaining(counter);

  //return all response data in an array
  return [firstData].concat(remainingData)
}
```

## Things to keep in mind: 
1. Async/await are built on promises, and are non-blocking
2. You can only use await within an async function.


More reading:
(Understand promises before you start using async/await)[https://medium.com/@bluepnume/learn-about-promises-before-you-start-using-async-await-eb148164a9c8]
(JavaScript loops — how to handle async/await)[https://blog.lavrton.com/javascript-loops-how-to-handle-async-await-6252dd3c795]
(6 Reasons Why JavaScript’s Async/Await Blows Promises Away (Tutorial))[https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9]