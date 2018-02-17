## Week Four Recap

### Instructions
Fork or re-pull this repository. Answer the questions to the best of your ability.

Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week.

Note: When you're done, submit a PR with a reflection in the comments about how this exercise went for you.

### Week 4 Questions

1. What is a cookie?
* a small piece of data stored on the client for a website that identify that client. They have to be associated with a specific domain, and they carry the data created by that user's browsing in http headers (cookie data).

2. What’s the difference between a session and a cookie?
* sessions match up with a cookie
* cookies are not accessible to the server but sessions are -> in a rails application, sessions are available to the controllers and the views
* cookies are always client side, but sessions can be client or server side
* cookies can be changed by the user, but sessions cannot

3. What’s a flash and when do you want to use flashes?
* A flash is a special kind of session that only lasts for the the following request and then gets destroyed
* You usually would want to use a flash to display a message or notice about the user's previous request - often times, when they are submitting a form. You can display whether it was sucessful or if it was not, and why.

4. Why do people say “HTTP is stateless”?
* People say HTTP is stateless because it does not store information about previous requests. Each request a client sends is treated in isolation.

5. What’s authentication? Explain.
* Authentication is the application confirming that the user is who they say they are.
* When a visitor registers for an application, and they create a username and password (or whatever else), they are added to that application's database and given a unique user id.
* The next time they log in, the application will authenticate their information against the information in the database (and the encrypted password). If the user is authenticated succesfully, the application creates a session that is matched to the client's browser and holds that user's unique id. 
* Until they log out, the application will use that session to display that user's information on the pages they visit.

6. What’s the difference between authentication and authorization?
* Authorization is the process of validating that a user has VIP privileges
* An 'admin' is a user that has been specially created in the application database, and allowed certain privileges
* In our experience, we have defined "roles" in the users' records in the database, and if the user is an admin, then they have access to actions and views that regular users may not.

7. What’s a before filter?
* A before filter is a method that we have told our application to run prior to performing certain actions. 
* In the context of authentication and authorization, the before filter may check whether the user is authenticated or authorized before performing certain actions and rendering certain views.

8. How do we keep track of a user once they’ve logged in?
* With a new session that holds that users user id

9. When do you want to namespace a resource? When do you want to nest a resource? What's the differences between those two approaches?
* Namespacing allows us to organize our controllers into a separate directory under that namespace
* Both namespacing and nesting changes the route a user would visit and the path helper prefix
* Namespacing is helpful when you want to organize certain actions and views under a sub-type of a resource. The main example I can think of / am aware of, is namespacing routes under admin, so you can apply the same before filter to all the controllers within the admin directory and render specific admin views
 * I think namespacing is also useful for large apps with many resources and databases -> this would allow you to organize them under larger categories
 * Nesting is generally used to clarify paths for resources with one-to-many / dependent relationships. If you want to show all of a director's movies, you would nest the movie show action under the director show action. 
 
10. At a high level, what tools can you use to implement authorization? How would you use them?
* roles with a default role in your users db table (& an enum)
 * enum gives you access to methods like .role, .admin?, .default?, .admin! and .default!
* namespaced routes with an admin controllers directory and an admin views directory
* a base controller in the admin controllers directory with a before_action filter
 * inheritance -> all other admin controllers inherit from this base controller
* sessions
* db seeds to seed admin users (there must be a better way..?)

11. What's an enum, and what advantages does it offer? What data type needs to be in your database to use an enum? Where do you declare an enum?
* An enum attribute (defined on the model) maps an array of values passed to integers for that attribute in the db table and can then be queried by name. 
 * Alternatively, you can define an enum as a hash and define which integers match which values. With an array, it defaults to using the  index of that value in the array
* It offers the advantage of additional instance methods added to your model

12. What are some strategies you can use to keep your views DRY?
* partials
* layouts
* if else?


### Reviews Questions 
13. Given the following array of hashes, how would I print an alphabetical list of holidays?
```ruby
[
 {holiday: {name: "St Patrick's Day", supplies: ["Corned Beef and Cabbage"]},
 {holiday: {name: "Halloween", supplies: ["Candy", "Costume"]},
 {holiday: {name: "Hanukkah", supplies: ["Menorah"]}
]
```
```ruby
holidays = given.map do |hash|
 hash[:holiday][:name]
end

puts holidays.sort.join(', ')
```

14. How would you clean incoming data to ensure "$300" or "300.00" is stored as 300? 
```ruby
amount.split('.').first.sub(/[^0-9]/, '').to_i
end
```


### Self Assessment:
Choose One:
* I was able to answer every question without relying on outside resources
**I was able to answer most questions independently, but utilized outside resources for a few**
* I was able to answer a few questions independently, but relied heavily on outside resources 

Choose One:
* I feel confident about the content presented this week
**I feel comfortable with the content presented this week**
* I feel overwhelmed by the content presented this week
* I feel quite lost by the content presented this week
