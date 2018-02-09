## Week Three Recap

### Instructions
Fork this repository. Be sure to pull the latest changes to your local repo. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Questions

1. What is the entry at the command line to create a new rails app?
* (we have been doing): rails new <project_name> -T -d:"postgresql" -skip--spring -skip--turbolinks

2. What do Models generally inherit from in rails?
* ApplicationRecord (which inherits from activerecord)

3. What do Controllers generally inherit from in a rails project?
* ApplicationController

4. How would I create a route if I wanted to see a specific horse in my routes file assuming I'm sticking to standard conventions and that I didn't want other CRUD functionality?
* get '/horses/:id', to: 'horses#show'

5. What rake task is useful when looking at routes, and what information does it give you?
* rake routes / rails routes
* It gives you all the routes available to your app, based on what you have defined in your config/routes.rb

6. What is an example of a route helper? When would you use them?
* horses_path for '/horses'
* You would probably use route helpers anytime you have multiple paths for a resource and you have used rails resources syntax in config/routes.rb to define those paths

7. What's the difference between what `_url` and `_path` return when combined with a routes prefix?
* `_path` returns the URI and `_url` returns the full url (aka prefixed by the protocol and host/port)

8. What are strong params and why are they necessary?
* strong params are params for a resource that you specifically permit your public methods access to
* They are necessary because they keep your application, and specifically, your database secure by only allowing users to send the data that you expect

9. What role does `form_for` play in helping us create our forms?
* `form_for` takes an argument, an instance of an object, and determines which resource the form action is on. It determines the method for the form base on whether that instance has been saved (update) or not (create). It then takes a block that defines the labels and fields for the form, and generates a string of html that will display that form.

10. How does `form_for` know where to submit the user's input?
* It determines the model/class of the instance passed to it and sends it to the corresponding controller
* If the instance passed to `form_for` already exists ( i.e. it has been saved in the database), then `form_for` knows to send it to action update. If the instance is empty / has not been saved to the database, then `form_for` knows to send it to action create.

11. Create a form using a `form_for` helper to create a new `Horse`.
```ruby
<%= form_for @horse do |f| %>
  <%= f.label :breed %>
  <%= f.text_field :breed %>
  <%= f.label :name %>
  <%= f.text_field :name %>
  <%= f.submit %>
<% end %>
```
12. Why do we want to validate our models?
* We validate our models so we can control what kind of data gets entered into our database. It makes sure that columns you require for records are required, that columns you require to be unique are unique, and that columns that you require to be a certain format or datatype are in that format
