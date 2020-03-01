---
layout: post
title:      "Associations (Project Review)"
date:       2020-03-01 02:31:36 +0000
permalink:  associations_project_review
---




- A foreign key points to a primary key in another table.

- The foreign key is going to be the primary key of your association.

- The foreign key always sits on the table of the object that it belongs to.



So given that, if we have two models; article and author we would want an author_id column in our articles table.

So to give a step by step example of how to create associations for this blog post, lets talk about those two models.

If we have an author class it’ll look something like this;

class Author < ActiveRecord::Base

has_many :articles      *# Anytime you have a hasmany association, that will be pluralized.*

end

And our article class would look something like this;

class Article < ActiveRecord::Base

belongs_to :author

end

The next thing we would want to do is create our new migrations, one for “authors” and one for “articles”

$ rake db:create_migration NAME=authors
$ rake db:create_migration NAME=articles

Those would look like this;

class Authors < ActiveRecord::Migration

def change
	create_table :authors do |t|
		t.string :name
	end
end


class Articles < ActiveRecord::Migration

def change 
	create_table :articles do |t|
		t.string :title
		t.string :content
		t.integer :author_id
	end
end 

Ok so now we’d want to do a quick rake db:migrate so we can go into tux and start making some associations

So we would want to make some objects from each class and save them to the database first or there would be nothing to associate. 

>> author1 = Author.create(name: “Alex”)
 => #<Author id: 1, name: "Alex">

>> article1 = Article.create(title: “Generic Title”, content: “Some content”)
=> #<Article id: 1, title: "Generic Title", content: "Some content", author_id: nil>

So currently we can see that there is no association yet since “author_id: nil”

But if we do this;

>> article1.author_id = author1.id
=> 1

And then 

>> article1
=> #<Article id: 1, title: "Generic Title", content: "Some content", author_id: 1>

You can see that the author_id attribute of our article object is no longer nil but is the id associated with author1.

The last thing we’d need to do to commit this association to our database is;

article1.save

Now we could create new articles and associate them in the same way so that we could then say something like;

author1.articles.all 

I’ve added a couple more articles so we’d get this;

=> #<ActiveRecord::AssociationRelation [#<Article id: 1, title: "Generic Title", content: "Some content", author_id: 1>, #<Article id: 2, title: "Generic Title2", content: "Some more content", author_id: 1>, #<Article id: 3, title: "Generic Title3", content: "More and more content", author_id: 1>]>

Also, an easier in my opinion way we could’ve created the associations is this;

>> article4.author = author1
=> #<Author id: 1, name: "Alex">

>> article4
=> #<Article id: 4, title: "Generic Title4", content: "The most content of all", author_id: 1>

Of course we’d have to do;

>> article4.save

To commit these associations so that if we wanted to check;

author1.articles.all 

We would see article4 has been added.

Now we can do other things like;

>> author1.articles.last(2)
=> [#<Article id: 3, title: "Generic Title3", content: "More and more content", author_id: 1>, #<Article id: 4, title: "Generic Title4", content: "The most content of all", author_id: 1>]

Or 

>> article3.author
=> #<Author id: 1, name: "Alex">


___________________________________________________________________________________________________

Writing this blog post and using corneal to make these models/migrations in a simpler form to tinker around in tux I feel has really helped my understanding of associations. I’ve added a link to the repo I created to write this blog post if you’d like to check it out. 


https://github.com/AlexJMartinez/associations


















