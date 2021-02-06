# React Project! 

You've made it! You're ready to build a React application! Before you start ideating, think about some of the project requirements. 

## Requirements

You've been through one Project Mode now. As you progress through the program, your projects will become more complex. This is good - it is a display of your own growth. Complexity, however, can increase the amount of time and energy you need to put into your projects. Keep this in mind from the beginning of your project.

While you're ideating and designing for your project, keep in mind that the project should be scoped appropriately around the project requirements and the work involved should be doable within the designated time. Take time to read through the requirements and use them to help you prioritize tasks. There may be extra features you'd like to add to your project, but focus on completing requirements first. If you end up with extra time, you can then choose to build additional features and stretch goals

The guidelines here are minimal but be sure that you:

1. Build a React frontend that uses at least two different *client-side routes* (i.e. use react-router). Ex: even if your whole app is mostly a single page app, have the form to signup be found at `/signup`
2. Use an external API to populate data or content on you frontend
3. Set up a JSON server to persist user inputs of some kind. This could be storing posts, comments, likes, image links, etc... anything you can send in a POST request to a JSON server.

**Note:** Since a JSON server must be run locally, publishing this project may result in some features not working properly. However, when we learn about backend servers, you'll be able to come back and 

1. Use a _Rails API backend_ with a separate _React frontend_ that are created in two different Github repositories.
2. Have at least three resources (three DB tables) on the backend and your application must have full CRUD actions for at least one resource.
3. Must have at least two different *client-side routes* (i.e. use react-router). Ex: even if your whole app is mostly a single page app, have the form to signup be found at `/signup`
3. **Optional:** Your application can have authentication/authorization. You are welcome to use an auth template as discussed in class.

It is highly suggested that any calls to 3rd party APIs are made _through your backend_.

Example: A user clicks a button that says 'Get Gifs'
* React makes a request to Rails
* Rails makes a request to the Giphy API
* Rails receives the response from Giphy and sends to React
* React receives the response from Rails and you do something with it on the client

This is so you can avoid any *CORS* issues. If you are unable to hit an API from your React app due to a CORS restriction, it is very likely that it is impossible to do so. _Brief Refresher on CORS: the idea is that from one domain (the port your webpack development server is running on) you are not allowed to access another domain.  You must make the request from a server (i.e. Rails), so the request is exempt from the Same-Origin Policy restriction._


## Backend Setup
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

## Frontend Setup
To create your React project, you may use a tool called [create-react-app](https://github.com/facebookincubator/create-react-app), an awesome project generator developed by Facebook. To use this
+ `npm install -g create-react-app` - this installs the generator as a global package
+ In the directory where you'd like to create your project, `create-react-app my-project-client`. It's that simple!

We'd recommend to begin by removing any of the default stuff given to you by Create React App that you do not understand. The following are some really great resources on how to think about setting up a React project (_Spoiler: They both say the same thing, "There's no right answer!"_)
* [React Docs](https://github.com/reactjs/reactjs.org/blob/71788c647daa07392a8156609fdbede8e9ed24f7/content/docs/faq-structure.md) This was written by Dan Abramov himself <3 <3 <3....
* [The 100% Correct Way to Structure a React App (or why there’s no such thing)](https://hackernoon.com/the-100-correct-way-to-structure-a-react-app-or-why-theres-no-such-thing-3ede534ef1ed)

## Notes
By default both your client app and your rails app will run on port 3000. You'll have to specify one or the other to run on a separate port.
* Rails: `rails s -p <some_number_thats_not_3000>`
* React: Check out this [issue](https://github.com/facebookincubator/create-react-app/issues/1083)

A great article on how [DHH thinks about setting up controllers in Rails](http://jeromedalbert.com/how-dhh-organizes-his-rails-controllers/)
