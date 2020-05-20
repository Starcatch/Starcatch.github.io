---
layout: post
title:      "**Sinatra Book Review App - done!**"
date:       2020-05-20 00:52:32 +0000
permalink:  sinatra_book_review_app_-_done
---



	After coming up with what I would like to do for my project, which is to build a minimalist Book review application.  I used corneal in order to build a structure for it.
After scaffolding it, adding dependencies,  relationships , and building logic. It took some time and  a lot of sweat, for the  app be  somewhat functional. Then I began testing it and running into issues, which learnt how to fix. And I would like to share my experience, and hopefully help some people who might run into the same issues.  

	My app is a simple Book review app , in which users can sign up, log in, add a book they like to share , add a review to other books in the list. As I ran **shotgun** and my app appeared in a browser I manually started adding the books I have lying around my apartment. I didn’t want to create seeds file in which we usually hold default data. I wanted to test my app and thus I wanted to add everything manually as a user. Everything seemed to work as I wanted except for one thing. I made a syntax error in my  books_controller class, instead of (**name: params[:book_name]**, author: params[:book_author]), I wrote (**name: [:book_name]**, author: params[:book_author]) leaving out the word** params **before the square bracket. As a result, my book title appeared to be **[:book_name]**, instead of the actual title of the book. I realized where the mistake was, and quickly fixed it, expecting, somehow, ** [:book_name]** to despair. I entered the correct  name of the book while adding a new book to the page. After that  I added 9 more books, they all had  the correct title and the author, except for this very first one. I thought of a solution, I’m going to allow user to delete only the book he or she enters, but there was a problem, what if I had book reviews, which belonged to other user, they would be deleted too. After doing a little bit of research, and going back to Learn material, I realized that there is “**tux**”. Running “**tux**” in the terminal allows a developer to access the data in data base, and deleting a specific piece of data. In my case it was a first book on the list, so I ran **Book.all.first.destroy**, and it solved my issue.  

	After building the functionality of the app, I slowly started adding some visual features. Thus, I stumbled upon another problem, for some reason my flash alerts , didn’t fire. I was sure to add right dependencies ** require ’rack-flash'**  in my application_controller and user_controller files, nothing worked, the terminal showed me an error, it had had to do with a gem, but it wasn’t clear. I was sure I had a **gem ‘rack-flash’** in my **Gemfile**, and I did. After a while at staring at my code trying to find a problem, I have decided to ask Google for help and the third link lead me to Learn study material about  [flash alerts in Sinatra](http://)https://learn.co/tracks/online-software-engineering-structured/sinatra/activerecord/sinatra-playlister and only than I realized that I’m using an outdated gem, and the gem I should be using is **gem ‘rack-flash3’**. Everything worked perfectly after I corrected the mistake. 

	I wanted to build a minimalist application, but I also wanted it be a bit more than just  functional, I wanted it to have some character.  It would be a great idea to have something displayed on the Home page of my app. I found a complimentary photo for my app, and now was the time for me to learn how to add it to my app.
	 After a quick search I found the answer, after having the photo ready, go to public folder, then go to images and drag the photo there. Once I had a picture in my images folder, I went to index file in views to write the HTML code in order to add the photo to my Home page.

That’s what it looks like: 
     

 ``<h2> Books Review Application </h2>
<img src=“images/bookshelf.jpg” height=“300”, width=“480”/>

So the formula is simple **“images/filename.filenam_extention”**

here is a link to my app , please check it out
SINATRA BOOK APP (http://)http://https://www.youtube.com/watch?v=oGHA7QHpqI4
