---
layout: post
title:      "CLI Project- Web Scraping"
date:       2020-03-27 08:24:10 +0000
permalink:  cli_project-_web_scraping
---


I did a CLI Web Scraping project. It is based on the movie streaming website HULU. To be specific, our web scraping starts from the Movie section of the site. Users retrieve information based on the inputs they provide. User-friendly CLI greets the user and converts user inputs into meaningful outcomes. There are different categories from where user can choose movies from, for example, Newly Added, Featured, Hulu Originals, etc. Interestingly, categories and movies are stored in a 2D Matrix. For example, to obtain the index of 2nd movie from the 3rd category, first, we have to pass the index argument of ‘2’ to the Category array and ‘1’ to the Movie array since both indices start from ‘0’. Once the user selects the specific movie, they will be provided with the information on that movie from a completely different page.

Behind the wheel are Open-Uri, Nokogiri gem, and Object-oriented Ruby classes. With the help of the Inspect feature on the browser and Nokogiri, I was able to locate and strip all the required classes for all the Categories and Movies using css selector. There are almost 19 different categories on the movie page with 30-60 different movies on each category which will have their properties like title, genre, descriptions, etc. My main concern was how am I going to store such a huge amount of data. Figuring out the index for each category and movie was not a big deal. Things start to get complicated when a user selects Category, then Movie because we have to dive deeper into the individual movie and store its property somewhere. To make it even worse, the design had to be an infinite loop where the user can start over again and again if they want to and request different categories and movies. To tackle the data storage problem, Object-Oriented Ruby comes to rescue. Once I collected an index of a category and a movie, I decided to create an object of a new movie class that will have their storage for their attributes. Then I created a CLI class where I create an object of an original Category class. Cli class is responsible for communicating with other classes, user and to maintain the infinite loop. Finally, it also lets the user exit the program if they want to.

To summarize, this project taught me how useful Object Oriented programming can be. I appreciate how gems like Nokogiri and inspect features on the browser can play a significant role while web scraping. Overall, I loved this project and wish to implement new features in the future!

