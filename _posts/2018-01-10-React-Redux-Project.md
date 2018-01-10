---
layout: post
title:  "React-Redux Notes App with Rails 5 API Backend with JWT Authentication"
date:   2018-01-10 16:12:12 -0500
permalink:  React_Redux_Project
---

#React-Redux Notes App + Rails 5 API Backend + JWT Authentication

I built a [notes app](https://obscure-garden-84871.herokuapp.com) with react redux for my final project.

To begin using the application, user submits an email and user to the API and API returns a JWT auth token. The API then provides authenticated users with routes to do CRUD actions on notes and users, with the exception of creating users(sign up), which can be done prior to authentication. The auth token is persisted in localStorage so if the page is refreshed, user is not logged out.

For JWT authentication I chose to use [knock](https://github.com/nsarno/knock). It is very simple to use and takes care of all the basic utilities of JWT auth on rails, and I highly recommend it.


On the front end side, [axios](https://github.com/axios/axios) and [thunk](https://github.com/gaearon/redux-thunk) was used to take care of async actions. Axios was easy to use except there seems to be some strange behavior with errors and Promise.reject() if the request fails.

[Bootstrap](https://getbootstrap.com/) and [react-bootstrap](https://react-bootstrap.github.io/) was used to style the pages.

Although the project is functional, there is still alot of features that can be added to make it more refined.

###Possible future features:
1. key binding
2. autosave
3. batch save
4. tags
5. search
6. authorization for different user groups


###Things to keep in mind for building future react-redux apps:
1. Put more things into state. Still have too much logic on components and reducer.
2. Make components small and build them to be fairly shallow, because passing props deep is very hasslesome. 
3. As usual, plan ahead.



##Notes api code structure
Note: only relevant files shown
```
notes-api
├── Gemfile
├── Gemfile.lock
├── README.md
├── Rakefile
├── app
│   ├── channels
│   ├── controllers
│   │   ├── application_controller.rb
│   │   ├── concerns
│   │   ├── notes_controller.rb
│   │   ├── user_token_controller.rb
│   │   └── users_controller.rb
│   ├── models
│   │   ├── application_record.rb
│   │   ├── concerns
│   │   ├── note.rb
│   │   └── user.rb
│   ├── serializers
│   │   ├── note_serializer.rb
│   │   └── user_serializer.rb
│   └── views
│       └── layouts
│           ├── mailer.html.erb
│           └── mailer.text.erb
├── config
│   ├── application.rb
│   ├── boot.rb
│   ├── cable.yml
│   ├── database.yml
│   ├── environment.rb
│   ├── environments
│   │   ├── development.rb
│   │   ├── production.rb
│   │   └── test.rb
│   ├── initializers
│   │   ├── application_controller_renderer.rb
│   │   ├── backtrace_silencers.rb
│   │   ├── cors.rb
│   │   ├── filter_parameter_logging.rb
│   │   ├── inflections.rb
│   │   ├── knock.rb
│   │   ├── mime_types.rb
│   │   └── wrap_parameters.rb
│   ├── locales
│   │   └── en.yml
│   ├── puma.rb
│   ├── routes.rb
│   ├── secrets.yml
│   └── spring.rb
├── config.ru
└── db
    ├── migrate
    │   ├── 20171220004821_create_users.rb
    │   ├── 20171220030913_create_notes.rb
    │   └── 20171220035849_add_user_ref_to_notes.rb
    ├── schema.rb
    └── seeds.rb

```

## Client code structure
Note: only relevant files shown
```
notes-client
├── README.md
├── node_modules
├── package.json
├── public
│   ├── favicon.ico
│   ├── index.html
│   └── manifest.json
└── src
    ├── actions
    │   └── index.js
    ├── components
    │   ├── AddNewButton.js
    │   ├── DeleteButton.js
    │   ├── Messages.js
    │   ├── NavBar.js
    │   ├── NextButton.js
    │   ├── NoteContainer.js
    │   ├── NoteList.js
    │   ├── NoteListItem.js
    │   ├── PrevButton.js
    │   ├── PrivateRoute.js
    │   ├── Routes.js
    │   ├── SaveButton.js
    │   ├── SaveStatus.js
    │   ├── StarButton.js
    │   └── StatusAndActionBar.js
    ├── configs
    │   └── domain.js
    ├── constants
    │   └── constants.js
    ├── containers
    │   ├── App.css
    │   ├── App.js
    │   ├── Home.css
    │   ├── Home.js
    │   ├── SignInForm.js
    │   ├── SignUpForm.js
    │   └── UserPage.js
    ├── index.js
    ├── logo.svg
    ├── reducers
    │   ├── alertReducer.js
    │   ├── index.js
    │   ├── notesReducer.js
    │   └── userReducer.js
    ├── registerServiceWorker.js
    └── store
        └── configureStore.js
    


```


##Live Demo
Click [here](https://obscure-garden-84871.herokuapp.com) to see the live demo.

##Additional Resources







