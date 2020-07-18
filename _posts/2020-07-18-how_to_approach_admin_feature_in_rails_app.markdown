---
layout: post
title:      " How to approach building an Admin feature in Rails App?"
date:       2020-07-18 00:32:02 -0400
permalink:  how_to_approach_admin_feature_in_rails_app
---


When building my app I’ve learnt a lot of new things, including simple shortcuts to make a developer’s life easier when building a project. One of these shortcuts I’d like to share with you, which might be very useful for building CRUD application. 
	
My app is a Nursing Home Server, which staff members use to enter logs and report about individuals they are working with. There are a lot of paper work involved working with individuals who require medical attention and care. Most of the paper work is analog,  nurses and other care givers have to write a lot of these reports by hand, and carry large folder around. Would it be much nicer, if a staff member could come to work, and enter those reports from his/her phone , or a work tablet, or a work computer, and all the information would be stored in the Database, and extracted and printed as needed. So my app is meant to make Staff’s life easier.
	
I have a few players in my app, User who is a regular staff member,  Admin of the app who acts as a manager of the facility, Individual a person who lives in a group home facility,  Daily Logs the reports users should fill out at the end of the shift for each Individual, and last but not least  an individual’s Vitals. The list can go on and on , we can add Daily Activities, Medication Intake record and on, but for the purpose of this post, we are just going to be working with the User model in our application.  Our goals include: Users should only be able to log in, and perform CRUD actions on themselves, and notes and reports they have entered, a User should not be able to delete of modify the log which was created by another employee. As well as should not be able to add and delete Individuals. The Admin, our manager should; however, be able to perform this actions on all the Models in our app, except for editing User’s(employee’s) personal information, like password and username, we can add here the hours that our employee worked. 
		
There are a few ways to approach it, we can either build an Admin Model and add all  Models’ ids as foreign keys to Admin’s table along with other Admin’s attributes, like username and password. Or we can implement an easy solution and  add Admin attribute to our user. Because we already built  CRUD logic we are going to take a second approach, add Admin to Users and add some validations.
 Here are simple 9 steps on how to do that:
1. You need to add Admin column to Users table. In our Terminal type: 
`rails generate migration add_admin_to_users `

2. In the migration file we should set the Admin’s attribute to boolean and default property of False . Like so : 
   `class AddAdminToUsers < ActiveRecord::Migration[6.0]`
      `def change`
          `add_column :users, :admin, :boolean, default: false`
      `end`
    `end`
			 
3.  `rails db:migrate`

4. Create a new user either from Back-End(rails console), or Front- End(browser).

5. Once you created the user, this user should be your last user in the users hash.

6. Enter rails console by typing: `rails c` in your terminal. 

7. Type `User.all`  in your terminal. You should get a hash of all users.

8. Select the last user in users hash `user = User.last` .

9. And now is the best part, turn the assigned user to admin by entering : `user.toggle!(:admin)` in your terminal. 

From this point on this user will act as an admin in your application. Now you can start adding validations and build more logic associated with Admin’s actions.

I hope you found this post useful. Please check out my Rails Portfolio app on GitHub: https://github.com/Starcatch/Nursing-Home-Logs/tree/master



	
