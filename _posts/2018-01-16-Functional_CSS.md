---
layout: post
title:  "Functional CSS"
date:   2018-01-16 19:58:14 -0500
permalink:  Functional_CSS
---
While working on my react-redux project, I figured I needed some sort of front end framework to beautify my pages so I instinctively went with bootstrap as it is easy to get started and has many many examples to go off of. I knew bootstrap at one point in the past but I was a hard time remembering how to customize using the framework. I didn't want to dwell too much on the subject at the time and just built out my own custom css and overwrote when needed. It is definitely much quicker to just write my own css for small scale project than taking the time to relearn bootstrap, but it also defeats the purpose of using the framework. while writing my own css, I also realized I didn't really know how to organize my selectors and which selectors to use. My solution worked but it was definitely not ideal for maintenance and debugging or just good code, for that matter. I revisited it to come up with a better solution and I found a solution that I am sold on: functional css(atomic css).

## What is functional CSS
In functional css, a class selector is written for each reusable property setting. To style a component, one or multiple classes(or none) can be added to the element to complete the desired effect. Functional css place emphasis on keeping elements shallow. By having one property definition for each class selector, it ensures that the css selectors are as reusable as possible.

## The Positives
* #### Write minimal new css
Because functional css limits all the class selectors to one property definition. to you can easily reuse all the class selectors without having to understand what the class names mean. Imagine coming onto a new project and within the file you have 4 nested div containers. Each with the container name 

* #### So, so easy to get started
Functional CSS is kept shallow on purpose. to get started you just need to stick with a format for naming classes. If working with techyons or basscss-like toolkits, it's easy to read up on documentation quickly to get started. If a programmer is joining a team midway through a project that uses functional css, even without documentation it is easy to get into the zone as the css file it self is the dictionary.

* #### Easy to debug
Shallow structure means when something is not working the way you desire, you only have to look at that individual problematic component. With other css styles it can be hard to sift through all the display:none and complex css rule sets commonly present in other css organization styles.

## The Negatives
* #### Difficulty in making batch changes
Due to the nature of functional css, there may be significant redundency when you want to create an element that is styled the same way. For example, in a scenario that you have 100 radio button that have 5 different functional classes defining the display, cursor, padding, vertical-align and margin. The cursor behavior desired has changed. To solve this you can find and replace all radio buttons with the same classes. But what if the 5 classes were not in the same order? Supposedly you can write a script to sort the classes, but this is already getting complicated. Now, What if you want to change half the buttons to a different style? Now we are back to manually changing the checking through components that have 5 classes each, a task that is definitely done more easily when classes are semantic.

* #### CSS still has to be written sometimes
Functional css is an organization way for CSS modules that can be reused. However, what if you have a component that you will likely never use again? For example, if you want arbitrary paddings or margins of 98px, it seems highly unlikely that a css class definition written for that particular property is reasonable. A specific css definition set still has to be written for that component.

## References
* [Functional CSS From A Pure UI Perspective](https://medium.com/javascript-inside/functional-css-from-a-pure-ui-perspective-bd04c8af4fdc)
* [Functional CSS - The Good, The Bad, and Some Protips for React.js Users](https://github.com/chibicode/react-functional-css-protips)