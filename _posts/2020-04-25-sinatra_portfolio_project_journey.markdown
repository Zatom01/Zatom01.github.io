---
layout: post
title:      "Sinatra Portfolio Project Journey"
date:       2020-04-25 21:12:02 -0400
permalink:  sinatra_portfolio_project_journey
---


This project must be one of my favorite projects. Using Sinatra and ActiveRecord with some basic HTML knowledge, I was able to create beautiful looking user friendly webpages that mirrors the real world applications. I learned so many things from this project. For example, Route Handlers, 

Route Handlers: With the use of HTTP verb like get,post,patch,delete, we can manage the flow of information from one place to another. The concept of named parameters and how they are accessed using the params hash was so important to learn and to do this project. For example; 

                  get '/user/:id' do 
                        Userid= params[:id]
			            end 
			

    Here, we can access the value of Userid by using the params[:id]. /user/2 gives the params[:id]=>2. It is always good to check the params hash on the Pry console to see what exactly is it giving. Pry console has now become my best friend after this project for debugging. 

Learning how to render erb file from the Route handlers and passing user's information back to the controller was another important concept I got comfortable with during this project. This is where we will be using lots of params hash to load user data to the controllers. 

I remember when we had to hard code each methods in our class to do specific things. For example, In our class, we wrote methods like initialize, create,save,delete,find_by_name,find_by_id,etc. But, with ActiveRecord, we don't have to worry about any of them. However, it is really good to know how the engine really works behind the magic curtain. ActiveRecord is beast of its own.  It is an interface between the database and our application which will help us create models from the database tables information which is crucial. 

Some other cool concepts that I got to learn from this project was using Helpers method, Validation Controls, Sessions and cookies, forms, etc. I really liked working with the Forms and have implemented one of my POST routes a litle bit differently from any of my labs I have done. For example, When a user goes to their specific post, we have to use a form inorder to let them enter an updated post if they want to update. Right next to the "UPDATE" button, I have another button "DELETE" placed which when clicked will go to the same POST route like the "UPDATE" button does. With the help of params hash, I was able to differentiate which button was clicked so that I could write the logic according. For example;
``` 
                if !!params[:update] && !params[:content].empty?
                    @post.update(:content=>params[:content])
            
                elsif params[:content].empty? && !!params[:delete]
                        @post.delete

```
When a button(UPDATE/DELETE) is clicked, this block of code will be triggered in our controller. First we are checking if params[:update] exists and whether it is true. If it is true and if the params[:content] is not empty then we can be sure that user clicked UPDATE button, so we are going to Update the Post. And if params[:delete] is true instead of params[:update]  and params[:content] is empty, then user clicked DELETE button, so we will be deleting the post.

Overall experience from this project was awesome. I wish to learn more web development in our future Rails project and want to compare Sinatra and Rails.
