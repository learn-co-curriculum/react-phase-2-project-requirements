# React Project! 

You've made it! You're ready to build a React application! Before you start ideating, think about some of the project requirements. 

### Requirements

You've been through quite a few Project Modes by now and should have some idea how to think about scoping a project, what you can accomplish in a the designated time, and what is expected of you in terms of meeting complexity requirements.

The guidelines here are minimal but be sure that you:

1. Use a _Rails API backend_ with a separate _React frontend_ that are created in two different Github repositories.
2. Have at least three resources on the backend and your application must have full CRUD actions for at least one resource. 
3. **Optional:** Your application can have authentication/authorization. You are welcome to use an auth template as discussed in class.

It is highly suggested that any calls to 3rd party APIs are made _through your backend_.

Example: A user clicks a button that says 'Get Gifs'
* React makes a request to Rails
* Rails makes a request to the Giphy Api
* Rails receives the response from Giphy
* React receives the response from Rails

This is so you can avoid any *CORS* issues. If you are unable to hit an API from your React app due to a CORS restriction, it is very likely that it is impossible to do so. _Brief Refresher on CORS: the idea is that from one domain (the port your webpack development server is running on) you are not allowed to access another domain.  You must make the request from a server (i.e. Rails), so the request is exempt from the Same-Origin Policy restriction._


### Server Setup
```
rails new <my-project> --api -T --database=postgresql
```

Let's go through this in detail:

* `--api`
  *  Make a [Rails 5 API](http://edgeguides.rubyonrails.org/api_app.html), basically you're telling Rails you don't want any of the stuff you wouldn't need for an application where Rails is not rendering views. Think the ActionView library (`form_for`, `link_to`, etc..), ERB, Security protections that ensure forms were rendered by the Rails app, things like that.
* `-T`
  * don't generate tests for this app
* `--database=postgresql`
  * Set this up to use a Postgres (as opposed to SQLite) database. If you ever want to push this to Heroku, Heroku requires a Postgres database. There won't be too much difference in how you have to write your code. You'll have to be sure to run `rails db:create` and make sure you have postgres running (i.e you can see the elephant)
* Be sure to do the necessary setup for the [rack-cors-gem](https://github.com/cyu/rack-cors)
* You may want to use [active-model-serializers](https://github.com/rails-api/active_model_serializers/tree/0-10-stable)

Your apps should live in separate repositories. This means you will have two separate repos. 

1. You should generate your API using the following command: `rails new my-project-api --api -T --database=postgresql`. (Setting your database up as Postgres initially will make deployment easier at a later stage.) 
2. To create your React project, you may use a tool called [create-react-app](https://github.com/facebookincubator/create-react-app), an awesome project generator developed by Facebook. To use this
	+ `npm install -g create-react-app` - this installs the generator as a global package
	+ In the directory where you'd like to create your project, `create-react-app my-project-client`. It's that simple! 

**NOTE** by default - both your client app and your rails app will run on port 3000. Check out this [issue](https://github.com/facebookincubator/create-react-app/issues/1083) if you'd like to change the default.
