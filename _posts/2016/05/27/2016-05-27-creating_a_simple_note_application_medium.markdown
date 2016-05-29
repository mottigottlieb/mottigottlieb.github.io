---
layout: post
title:  "Recognizing the power of `self`"
date:   2016-05-27 10:57:57 -0400
---

At the early stage of Object-Oriented Ruby I was introduced to the idea of self.

At first, the ability to invoke 'self ' showed me what “everything in Ruby is an object” really means.

However, the "Aha!" Moment for me was at a later point in the curriculum, when self was used to collaborate classes.

In an example of a simple note application consisting of Note and User class:

```ruby
class User
    attr_accessor :id, :username, :notes
    @@set_user_id = 0

    def initialize(id=nil,username)
      @id = id
      @username= username
      self.id = @@set_user_id += 1    
      @notes = [] 
    end
end
```


```ruby
class Note
    attr_accessor :id, :title, :note, :time_created
     @@set_note_id = 0
 def initialize(id=nil,title,note,time_stamp=nil) 
    @title = title 
    @note = note
    @time_stamp = time_stamp
    @time_stamp = Time.now    
    self.id = @@set_note_id += 1
  end
end
```
Having a two-sided relationship where a note “Belongs To” a user and a user “Has-Many” notes can easily be achieved through self in a single method. 

```ruby
Class user
  #most of class ommited...
  def add_note(note)
    self.notes << note
    note.user = self
  end
end
```

here a note can “Belong To” to a user by assigning user's attribute of a note object to the instance #add_note is operating on, while “Has Many” notes was accomplished by shoveling a Note object passed into the method's argument.

Yet, the “Aha!” wasn't over, the further i got I've learned how self was way beyond object relationships, it can be used from saving data with Object-relational mapping:

```ruby
 def save
    sql = "INSERT INTO students (name, grade) VALUES (?, ?)"
    DB[:conn].execute(sql, self.name, self.grade)
  end
```  

To knowing my location while debugging in a repl:

```ruby
[1] pry(main)> self
=> main
```

As my journey to a full stack web developer continues  i  look forward to many more uses of `self` Where I'll truly see how every instance is uniquely an object in itself.

