---
layout: post
title:      "Rails App with a jQuery Front End - FridgeShare"
date:       2017-11-29 02:52:53 +0000
permalink:  rails_app_with_a_jquery_front_end_-_fridgeshare
---


For this portfolio project, I updated FridgeShare to have some elements rendered with jQuery. I decided I wanted to alter the Fridge index page to be able to do everything using jQuery, from viewing each fridge, editing the fridge, adding a new fridge, and adding comments to the fridge. 

The largest challenge for this project is to think about the seperation of tasks required. When writing building Rails front-end, Rails seems to be fairly opinionated on how the code should be organized; for the most part, the decision is already made for you, which is very nice for new web developers like us. When using javascript, there seems to be alot more freedom. Combined with a lack of experience with working with jQuery that proved to be the most challenging task.

In the future, I envision the app would provide an even better user experience if it is converted into a single page application (*with the exception of the Devise generated pages, which if converted would defeat the purpose of using devise*) and load all information through jquery since our application is small.

