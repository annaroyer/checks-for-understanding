## Week Three Recap

### Instructions
Fork this repository. Be sure to pull the latest changes to your local repo. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Questions

1. What is the entry at the command line to create a new rails app?
* (we have been doing): rails new <project_name> -T -d:"postgresql" --skip-spring --skip-turbolinks

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
* They are necessary because rails doesn't allow your public methods access to parameters in post/put requests (unless you make them strong parameters) in order to  keep your application, and specifically, your database secure by only allowing users to send the data that you expect. 

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

13. What are the steps of the DNS lookup?
* The browser and the operating system first look in their cache to see if the name is stored there. If it isn't there, the resolving name server takes the IP Address and goes to the Root Name Server. The root name server directs the resolving name server to the top level domain server, who directs the resolving name server to the correct authoritative name server. The authoritative name server gives the resolving name server the correct domain name. The resolving name server stores this in cache and returns it to the operating system, which gives it to the browser.

### Review Questions
14. How would you call the method prance from within the method move on a Horse instance?
* self.prance

15. Given the following hash:
furniture = {table: {height: 3, color: "red"}, purchased: true}
What is the different between how you would return true vs returning 3?

* return 3: `furniture[:table][:height]`
* return true: `furniture[:table][:height]`

16. What is inheritance?
* inheritance is where a class inherits the methods defined in a different class

Self Assessment:
Choose One:

**I was able to answer every question without relying on outside resources**
I was able to answer most questions independently, but utilized outside resources for a few
I was able to answer a few questions independently, but relied heavily on outside resources
Choose One:

I feel confident about the content presented this week
I feel comfortable with the content presented this week
**I feel overwhelmed by the content presented this week**
I feel quite lost by the content presented this week

