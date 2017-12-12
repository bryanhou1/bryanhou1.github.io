---
layout: post
title:      "Fridge Share - Rails Portfolio Project"
date:       2017-10-03 19:19:21 +0000
permalink:  fridge_share_-_rails_portfolio_project
---


As students or young professionals, living with roommates/flatmate has become a typical arrangement. While you save significantly on rent, it is common to have increased food waste because the fridge is more packed. The pint of moldy berries hidden behind the milk could have been salvaged if someone had noticed it. FridgeShare is an content management RoR web app created to help users keep track of their groceries and avoid having wilted lettuce or moldy berries sitting at the back of your fridge.

This application involves 3 models: Item, Fridge, and User, where the User is managed through  the Devise gem with the option to login through facebook implemented with the omniauth gem. Items belongs to Fridge and User, and Fridge and User has_many Items. User also has many Fridges through Items, and vice versa.

Without signing in, anyone is still able to view the details about the fridges and the items. However authentication needs to be provided if any CRUD action is to be done. 

To build the app, a large hurdle that I had to overcome was building facebook oauth login with Devise. I had trouble with getting the facebook graph API to return the user's email, which Devise relied on.  It was a problem I was stuck for days on and never figured out. I believe I was doing everything according to the documentation but it didn't seem to work as intended. In the end, I only managed to implement a work around for the issue, but would still really like to figure out what went wrong. 

Building the app was definitely a good refresher since I came back from a long hiatus of coding .The task definitely forced me to revisit concepts such as forms and nested_attributes , MVC structure, and devise. It was especially important to be familiar with these concepts and gems as going forward the course will be more focused on javascript.

While the app definitely needs some work on beautifying it, with alot of additional functions that can be expanded, I'm happy with how the project looks so far.





