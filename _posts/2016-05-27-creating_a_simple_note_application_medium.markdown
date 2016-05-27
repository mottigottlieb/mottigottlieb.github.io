---
layout: post
title:  "Creating a simple Note application. — Medium"
date:   2016-05-27 14:57:57 +0000
---


## Creating a simple Note application.

To gain a deeper understanding of object relations i have decided to go ahead and create my own simple Note application, splitting it around 2 classes of Note and a User while having them relate to each other.

**Note Class basics: **  
Note instances have an id, title, time-stamp, and of course a note.  
 attr_accessor :id, :title, :note, :time_created  
 @@set_note_id = 0  
  
 def initialize(id=nil,title,note,time_stamp=nil)  
[[email protected]][5] = title   
[[email protected]][5] = note  
[[email protected]][5]_stamp = time_stamp  
[[email protected]][5]_stamp = Time.now  
 self.id = @@set_note_id += 1  
 end  
end

**User Class Basics: **  
User objects have an id, username and a collection of notes.

```ruby
    class User  
        attr_accessor :id, :username, :notes  
        @@set_user_id = 0  
      
        def initialize(id =nil , username)  
            @id = id  
            @username= username  
            self.id = @@set_user_id += 1      
            @notes = []   
        end  
    end
  ```

Relating the classes:

Assigning a note to a user was done by setting the user attribute of the Note class instance to the instance #add_song is operating on, while saving a note was accomplished by shoveling a Note instance passed in as an argument to the #add_note.

    def add_note(note)  
        @notes << note  
        note.user = self  
    end

Searching for a note:

A user can search for a note either by i'ts title or id

    def find_by_title(title)  
         self.notes.detect do |note| note.title == title  
            end  
        end  
      
         def find_by_id(id)  
                 self.notes.detect do |note| note.id == id  
                end  
            end


[1]: https://medium.com/
[2]: https://medium.com/m/signin?redirect=https%3A%2F%2Fmedium.com%2F%40mottigottlieb%2Fcreating-a-simple-note-application-67d29f6159f8
[3]: https://cdn-static-1.medium.com/_/fp/img/default-avatar.dmbNkD5D-u45r44go_cf0g.png
[4]: https://medium.com/@mottigottlieb
[5]: /cdn-cgi/l/email-protection
[6]: https://medium.com/tag/ruby?source=post
[7]: https://medium.com/@mottigottlieb "Go to the profile of Motti Gottlieb"
  
