---
layout: post
title:      "You start learning new things when you get stuck"
date:       2020-03-15 22:55:56 -0400
permalink:  you_start_learning_things_when_you_get_stuck
---






Planning my CLI project started with a lot of  broad information I had learnt in the program this far. I  had very little idea how to use 'pry', I was always confused when using it , and what did  it actually do,  thus i tried to avoid it.  I had no idea how to use Github, besides just typing "learn submit" in learn IDE to submit my labs. And I practically didn't know anything on how to use Terminal, and OMG scraping terrified me. 

I was on the schedule with my labs, but it felt like I'm running a marathon, trying to grasp the concepts under the pressure of time, to finally get to the instructions and requirements for my CLI app.  
	When I read the requirements , at one moment I thought it was easy, because I learnt all this information , and another point I was overwhelmed, making choices was tough, which website to scrape, how my objects are going to interact with one and other. to prepare for a project I had to go a few weeks back read trough lab materials  again,  I  watched a “walk trough lecture” by  and before actually start planning it talk to my education coach, who told me, one very simple , but very important thing " You are going to learn a lot as you build this project!”;
I didn't didn't realize how true this statement was, until I started coding the project, and  constantly hitting one wall after another. When I got stuck I learnt the most. I was getting stuck almost on every step of my program. I started with finding a scrapable website, at least the website I thought was easily scrapable.
 	I wanted  my CLI gem to represent something of my surroundings and  Brooklyn Museum  like the best idea to represent my surroundings. Also, I like the museum for it's not so mainstream exhibitions. The museum is definitely worth a visit. 
	So my CLI gem goes out to Brooklyn Museum website scrapes current exhibitions from  the exhibition page and returns the names of the exhibitions in a numbered list, asks a user to enter the number associated with the current  exhibitions the user would like more information on, and displays three properties of the exhibition if the existing key is entered.  
	At the planning stage the scraping part of the entire project  seemed the most terrifying one. It was a fresh concept we only spent a few labs, learning it right before the  project assignment .  But it turned out to be one of the easiest parts of the program. To find the nodes I need  for scraping  I used Repl.it  to have a better visual of the way Nokogiri displays the code. Once I got the node i need , I began setting up the gem environment   following our technical coach's advice I installed a template for my gem using bundle gem, it took me  quite a few tries to properly interact with terminal, learn and use the commands, but I did it !!! 
	Now, I began planning my CLI logic , I remade this part many times over a course of the project , and even completely erased it couple of times and started  again until I  was more or less satisfied with the logic  and  the messages I wanted to display to  the user.  Now, when the logic was working, I went to create Sraper class, then Exhibition class, and required a few dependencies I used in the program.  I needed to make my logic real, after a few days of trail and error, getting stuck, and by getting stuck learning new things , which otherwise I would not had  understood  very well, remembering the words of my educational coach ,”You are going to learn a lot as you build this project!”  the words which comforted me every time I fell in a deep whole , and every time I  was able to get out of it. Now when the project is done and many new things were learnt from scratch, I can make a solid conclusion - you really learn new things when you get stuck, that’s when you start figuring things out.

1. 			You need to add Admin column to Users table. In our Terminal type:

 `rails generate migration add_admin_to_users `
 

2. 			In the migration file we should set the Admin’s attribute to boolean and default property of False . Like so :

       `class AddAdminToUsers < ActiveRecord::Migration[6.0]
           def change
              add_column :users, :admin, :boolean, default: false
           end
       end`
			 
3.     `rails db:migrate`

4. Create a new user either from Back-End(rails console), or Front- End(browser).

5. Once you created the user, this user should be your last user in the users hash. 

6. Enter rails console by typing: `rails c` in your terminal. 

7. Type `User.all`  in your terminal. You should get a hash of all users. 

8. Select the last user in users hash `user = User.last` .

9. And now is the best part, turn the assigned user to admin by entering : `user.toggle!(:admin)` in your terminal. 

From this point on this user will act as an admin in your application. Now you can start adding validations and build more logic associated with Admin’s actions.

I hope you found this post useful. Please check out my Rails Portfolio app on GitHub: https://github.com/Starcatch/Nursing-Home-Logs/tree/master
