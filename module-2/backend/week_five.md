### Week 5 Questions

Re-pull from this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON!). 

Note: When you're done, submit a PR. 

### Week 5 Questions
1. How do we make flash messages display on a page?
```
flash.messages.each do |type, message|
  <div class="#{type}">
    <p><%= message %></p>
  </div>
end
```

* idk, I think that would work, although it's not exactly what we did..

2. Where is cart information/temporary information usually stored?
* In a session + a PORO

3. What might be some reasons not to store a cart in our database? Are there any reasons why we would want to persist that information?
* Because the information is constantly changing and it would be 
  a. slow to constantly be running updates to the database table every time they add or remove something from their cart
  b. space-consuming
* Also because we often want visitors to be able to add things to their cart before creating an account, so they only need to create an account when they choose to checkout.
  * we wouldn't want to store database information about a cart without the information about who that cart belongs to
  
4. What is the purpose of the asset pipeline?
  1) concatenate assets, aka reduces the number of requests the browser makes to render a web page
  2) minification and compression, aka make things smaller for less overhead on loading
  3) allows code assets via a higher level language with precompilation down to the actual assets

5. Why do we precompile our assets?
* it's nice for us humans to have nicely organized files and different categories so we know where to look for things
* it's nice for browsers to have smaller, more compressed amounts of text to parse and assets that stay in cache until they change

6. What do each of the following tags do?

```ruby 
<%= stylesheet_link_tag "application" %>
<%= javascript_include_tag "application" %>
<%= image_tag "rails.png" %>
```
  1) renders the compiled stylesheets
  2) renders the compiled scripts
  3) renders a compiled image 
  
7. What are some of the elements of a great read me? What are some of the benefits of taking the time to update a readme for our project?
  * a table of contents (with links!)
  * a descriptive title and summary
  * information about how to configure and run the application
  * what technology you will need
  * information about how to contribute
  * examples with code snippets or even videos or images
    * file (and line?) of where these come from if they are in the project itself
  * acknowledgement of people involved

8. What are the top four accessibility issues that we as developers should be aware of?
1) visual
2) mobility
3) cognition
4) auditory? language? -> don't know the 4th

9. `before_save` is an example of a what? Where in our Rails application would we find a `before_save`?
* callback
* a model

10. Given the following object, how would we create a scope for all users who are active?

```ruby 
User.create(name: "Happy", active: true)
```
scope :active -> { where(active: true) }

11. What is the difference between a scope and a class method?
Nothing

### Review Questions:  
12. Given the following hash:  

```ruby
{cart: {"17" => 4, "204" => 52, "29" => 22}}
```

  12a. How would you add item with id of 48 with a quantity of 4?  
  
  ```
  given.default = 0
  given[:cart][item.id.to_s] += 4
  ```
  
  12b. How would you increase the quantity of item 29?  
  
  ```
  given[:cart][item.id.to_s] += 1
  ```
  12c. How would you find out how many items your user is thinking about purchasing?   
  ```
  given.values.sum
  ```
  
13. What is polymorphism? How does it relate to duck-typing? What are two ways you use this in everyday Rails applications?  * wikipedia says it is the provision of a single interface to entitities of different types, which is a good, general definition for what I understand polymorphism to be.
* It relates to duck-typing, because a single method can apply to different data types and different types of objects. For example, the method + can apply to integers, stings and arrays. Duck typing would be used to specify the data types that method was being used with
* model specs vs. feature specs 
* erb tags

14. How would you clean the string "(630) 854-5483" to "630.854.5483"?  
```
given.gsub(/[^0-9]/, ' ').strip.split(' ').join('.')
```

### Self Assessment:
Choose One:
* I was able to answer every question without relying on outside resources
* I was able to answer most questions independently, but utilized outside resources for a few
* **I was able to answer a few questions independently, but relied heavily on outside resources 

Choose One:
* I feel confident about the content presented this week
* **I feel comfortable with the content presented this week
* I feel overwhelmed by the content presented this week
* I feel quite lost by the content presented this week
