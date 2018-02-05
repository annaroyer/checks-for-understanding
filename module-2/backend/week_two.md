## Week Two - Module 2 Recap

Fork this respository. Answer the questions to the best of your ability. Try to answer them with limited amount of external research. These questions cover the majority of what we've learned this week (which is a TON - YOU are a web developer!!!). 

Note: When you're done, submit a PR.

1. At a high level, what is ActiveRecord? What does it do/allow you to do?
* ActiveRecord is an Object Relational Mapper. It helps you to query relational data from database tables and wrap that data in objects. It also goes in the other direction - it can take objects and use their attributes to create or update records in database tables.

2. Assume you have the following model:

```ruby
class Team << ActiveRecord::Base
end
```

What are some methods you can call on `Team`? If these methods aren't defined in the class, how do you have access to them?
* Team.all
* Team.first
* Team.last
* Team.new / Team.save / Team.create
* Team.update
* Team.destroy
* Team.count
* Team.sum(), Team.average()
* Team.order() / Team.join() / Team.group()

* We have access to them because the class team is inheriting all the methods defined on the ActiveRecord::Base module

3. Assume that in your database, a team has the following attributes: "id", "name", owner_id". How would you find the name of a team with an id of 4? Assuming your class only included the code from question 2, how could you find the owner of the same team?

* Team.find(4).name
* Team.where(id: 1).joins(:owners) --> or Team.find(4).joins(:owners) ..?


4. Assume that you added a line to your `Team` class as follows:

```ruby
class Team << ActiveRecord::Base
  belongs_to :owner
end
```

Now how would you find the owner of the team with an id of 4?
* Team.find(4).owner

5. In a database that's holding students and teachers, what will be the relationship between students and teachers? Draw the schema diagram.
* [students]        [student_teachers]            [teachers]
  [id]------------->[student_id]                  [id]
                    [teacher_id]<-________________/
  
6. Define foreign key, primary key, and schema.
* a foreign key is an attribute on a table that refers to an entity on another table in the database. The foreign key is the unique primary key of the entity on the other table
* a primary key is a unique identifier for an entity
* a schema is a representation of the tables in your database. It represents the attributes on the tables and the relationships between the tables

7. Describe the relationship between a foreign key on one table and a primary key on another table.
* A foreign key on one table is a reference to a primary key on another table.

8. What are the parts of an HTTP response?
* verb protocol URI
* headers
* body (optional for GET)


### Optional Questions

1. Name your five favorite ActiveRecord methods (i.e. methods your models inherit from ActiveRecord) and describe what they do.
* joins, runs a join on two tables with a one to one or one to many relationship (or specified), so you have access to the attributes of both simultaneously and you can do further analytics and calculations on their relationship with one another
* where, lets you search for a key/ value in a table and finds all instances that have that attribute with that value
* order, you can order by any attribute and choose descending or ascending
2. Name your three favorite ActiveRecord rake tasks and describe what they do.
* db:create  creates a new database
* db:migrate creates a new migration
* db:seed runs the commands in your seeds file to fill your tables with some data

3. What two columns does `t.timestamps null: false` create in our database?
4. In a database that's holding schools and teachers, what will be the relationship between schools and teachers?
* one-to-many (teacher belongs to school; school has many teachers)

5. In the same database, what will you need to do to create this relationship (draw a schema diagram)?
* teachers will have a foreign key that is the primary key for the school they teach at

6. Give an example of when you might want to store information besides ids on a join table.
* When there is data that is directly dependent on that relationship. Maybe students have many courses and courses have many students, and a students_courses table also holds the student's grade in that course.

7. Describe and diagram the relationship between patients and doctors.
* one to many; a doctor has many patients and a patient belongs to a doctor

8. Describe and diagram the relationship between museums and original_paintings.
* one to many; museums have many original_paintings and an original_painting
[original_paintings]  _--> [museum]
[id]                /      [id]
[museum_id]--------/
9. What could you see in your code that would make you think you might want to create a partial?
* repeated code / repeated html
