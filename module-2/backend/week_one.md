## Week One - Module 2 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON!). 

Note: When you're done, submit a PR. 

### Week 1 Questions

1. List the five common HTTP verbs and what the purpose is of each verb.
* GET: retrieve a resource from a URL
* POST: create a new resource
* PUT: edit all of a resource
* PATCH: edit part of a resource
* DELETE: destroy a resource

2. What is Sinatra?
* Some call it a web framework, but apparently Sinatra technically considers itself to be solely a DSL and not a "framework." It is a Domain Specific Language that gives you access to methods that parse http requests, generate http responses, and handle routes using ruby. 

4. What is MVC?
* It stands for "Model View Controller," and it is a design pattern that outlines how data is passed and manipulated within a web application. The models interact with the database and handle the way data gets manipulated. The views render the presentation in a format that a browser can interpret and display to a user (html, xml, javascript, etc.). The controller coordinates the responses to http requests, i.e. it parses the requests, decides how to handle them, delegates to the models and the views and generates a response.

5. Why do we follow conventions when creating our actions/path names in our Sinatra routes?
* We follow conventions in order to maintain a uniform interface between client and server and simple architecture that allows for every request and response to stand in isolation without having to maintain state.

6. What types of variables are accessible in our view templates without explicitly passing them?
* instance variables

7. Given the following block of code, how would I pass an instance variable `count` with a value of `1` to my `index.erb` template?
  
  ```ruby
  get '/horses' do
    @count = 1
    erb :index
  end
  ```

8. In the same code block, how would I pass a local variable `name` with a value of `Mr. Ed` to the view?

  ```ruby
  get '/horses' do
    name = "Mr. Ed"
    erb :index, :locals => {:name => name}
  end
  ```
  
9. What's the purpose of ERB?
* ERB allows you to embed ruby within HTML so you can create templates for dynamic views that change according to the user requests.

10. Why do I need a development AND test database?
* We want a development database that allows us to access existing data when we view our application as we are developing it. 
* We want a test database that allows us to clear the database after each test, so that we can test functionality in isolation. We want to be able to test that user actions will impact the data in specific ways and that the user can interact with the web app in the ways that we expect. We have to clear the database so that we can confirm our expectations without the database getting polluted every time we run our tests. 

11. What is CRUD and why is it important?
* CRUD stands for "Create Read Update Destroy," which are the four ways that users are able to interact with our database from the web app. It is important because it structures our entire application and directly correlates to the http verb and URI path combinations that should exist within our controller.

12. What does HTTP stand for? 
* HyperText Transfer Protocol

13. What are the two ways to interpolate Ruby in an ERB view template? What's the difference between these two ways?
* <% %> executes, but does not render the ruby code between the brackets
* <%= %> executes and renders the return value of the ruby code between the brackets

14. What's an ORM?
* Object Relational Mapper - it takes data from our database, which is a framework written in an object oriented language that maps object classes to data tables in a database and maps object instances to rows in those tables.

15. What's the most commonly used ORM in ruby (Sinatra & Rails)?
* Active Record

16. Let's say we have an application with restaurants. There are seven verb + path combinations necessary to provide full CRUD functionality for our restaurant application. List each of the seven combinations, and explain what each is for.
* GET '/restaurants'
  * user can see all the restaurants in our database
* GET 'restaurants/:id'
  * user can see one restaurant in our database
* GET 'restaurants/new'
  * user can see the form or page to create a new restaurant
* POST 'restaurants'
  * user can enter and submit information to create a new restaurant
* GET 'restaurants/:id/edit'
  * user can see the form or page to edit an existing restaurant
* PUT 'restaurants/:id'
  * user can enter and submit information to edit an existing restaurant
* DELETE 'restaurant/:id'
  * user can delete (or destroy) an existing restaurant from our database
  
17. What's a migration? 
* A migration is a blueprint (or instructions) for a change we want to make to a table in our database

18. When you create a migration, does it automatically modify your database?
* No, it doesn't modify the database until you run the migration

19. How does a model relate to a database?
* a model is an object class that is related to a table in our database. A model's instances relate to a row in that table. 

20. What is the difference between `#new` and `#create`?
* `#new` instantiates a new model instance that represents a record for a table in our database, but it doesn't save it into our database.
* `#create` both instantiates a new model instance and saves that record into our database

### Review Questions:  
21. Given a CSV file (“films.csv”) with these headers [id, title, description], how would you load these into your database to create new instances of Film?  

  ```ruby
  require 'csv'
  
  CSV.foreach('films.csv', headers: :true, header_converters: :symbol, converters: :numeric) do |row|
    Film.create!(row.to_hash)
  end
  ```
  
22. Given the following hash:
```
activities = {
  hiking: {cost: $0, supplies: ['hiking shoes', 'water', 'compass']},
  karaoke: {cost: $10, supplies: ['courage', 'microphone'],
  brunch: {cost: $35, supplies: ['mimosa flutes'],
  antiquing: {cost: $200, supplies: ['list of antique stores'] 
}
```
How would I add 'granola bar' to things you should have when hiking?

```ruby
activities[:hiking][:supplies] << 'granola bar'
```

23. What are the 4 Principles of OOP? Give a one sentence explanation of each.
* *inheritance*: allowing a more concrete class access to the attributes and behavior of the class or module it inherits from
* *encapsulation*: Protecting data from being accessed or manipulated outside its class
* *abstraction*: Hiding complexity away and writing code that mimics real life things and behaviors 
* *polymorphism*: a method derived from a common class behaves differently in different classes

### Self Assessment:
Choose One:
* I was able to answer every question without relying on outside resources
* *I was able to answer most questions independently, but utilized outside resources for a few* -> _essentially just my notes to help me phrase my answers more clearly. I understand things conceptually and can provide examples, but have a harder time defining them clearly and succinctly_
* I was able to answer a few questions independently, but relied heavily on outside resources 

Choose One:
* I feel confident about the content presented this week
* *I feel comfortable with the content presented this week*
* *I feel overwhelmed by the content presented this week*
* I feel quite lost by the content presented this week
