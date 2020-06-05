---
layout: post
title:      "My Rails Project"
date:       2020-06-05 02:29:10 +0000
permalink:  my_rails_project
---


I built a user-blog web application where user can signup, sign, create post, comment on each others post, update and delete their post/comments. Coming from Sinatra, Rails has lot to offer with automatic route generation where as in Sinatra we manually wrote our routes which was not fun. My Models were all related to each other in such a way that a nested routes had to be created where nested resources comes handy . Since User had many posts, and postcomments, and post belongs to a user, with many post comments, I nested Post and PostComment resources under User resources and rails gave me all the possible nested routes I could ever need. For example, users/:id/posts/22. 

First thing that I learned from this project was to learn about powerful gem like Devise which can be used for User model for authenticating the user attributes and also provides with its own controller with Session controller. Second, toying around the nested routes gave me ideas of what params needs to be passed through certain forms. I got tons of errors while working on this project, so I got to most of the errors and be familiar with them. Third, the way we set up our relation in our Model is very important. I think I spent the most of my time trying to debug errors all because of the improper model relation setup. 

My main problem that I was having during this project was when a user1 comments on user2's post, the same commented post would show up in user1's table as well from where user1 could edit/delete just like as if it belonged to them.  My User, Post and PostComment model initially had relation like this

```
User has_many PostComments
User has_many Posts, through PostComments

Post has_many PostComments
Post has many users through PostComments

PostComment belongs_to :post
PostComment belongs_to :user



```

Because Post had many users through PostComments and User has_many Posts, through PostComments, whoever commented on a particular post, they would automatically have the commented post as their own because of the join table PostComment. 


I corrected the Post model relation by making User has_many posts, and Post belongs_to user and adding a user_id as a foreign key in Post table.


OAuth was the one of the coolest thing I have ever done. Implementing features of signing with third party services like Github and Google gave me this vibe of being a real world developer. 

To sum up, this is one of the best and challenging project I have ever had. Loved it! Can't wait for Javascript project!

