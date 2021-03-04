---
layout: post
title:      "Building a full stack food ordering App with Ruby on Rails, React, Redux."
date:       2021-03-04 09:19:33 +0000
permalink:  building_a_full_stack_food_ordering_app_with_ruby_on_rails_react_redux
---


For the past year we probably ordered more food deliveries than did ever before. Due to COVID-19, and the lockdowns caused by the pandemic, food ordering apps and food delivery services like DoorDash, UberEats, GrubHub, and Seamless gained a lot of popularity. As a result of restrictions many restaurants are in a desperate need of solid online representation. I decided to build a burger ordering system, in which a client can go online select a restaurant near him/her and order burgers from the menu.
In my application there are three restaurants, all located in Brooklyn, just because Brooklyn is awesome. When a customer enters the website he/she lands on a landing page where she/he can choose a restaurant that is closer to one’s location to order burgers for either a pick up or a delivery.


After the customer chooses the restaurant location the customer is redirected to the menu page of the restaurant and can start adding desired items to the order, as well as deleting them from the order.

On the right hand side of the page there is a Menu Control which is only available to the restaurant personnel, and can only be accessed by an existing authorized user, through a login functionality, which is handled by Redux. The authorized user can manipulate the menu, by changing prices, names, and other properties of the menu items, as well as adding burgers to the menu, and deleting them.
Burger Hub is a small Full Stack Web application which was built with Ruby on Rails on the back end and React and Redux on the front end. In this blog series I would like to share the steps of the building process with you, and hope you find them useful.

**# 1.Preparation**

This was by far one of the hardest processes in building the app. The idea of food ordering app didn’t just come naturally to me. I had many half-baked ideas, which sounded great in theory but were extremely hard to implement when starting from scratch. In order to pick a right idea for an app I found it helpful to put all the ideas on the paper first. If you don’t have an idea for an app, there are a few things you can do, look at you current place of employment and see how a potential app can make a your work process easier, enjoyable, and more effective. Currently, I’m a manager at an educational facility for special children, in which direct care employees have to write progress notes and report vitals of the children they work with manually on a piece of paper. So for my Ruby on Rails project I built a centralized management system, which is easy to use and practically eliminates paper work. Down the road I would like to create a React app, which helps nonverbal autistic kids to vocalize their desires by pressing on pictures, and other visual content. Another place where you can look for ideas is your everyday life. Things you do on daily bases, track expenses, manage calorie and carb intake, as well as track and manage exercises, etc. I chose food ordering domain.

**# 2. Planning it out**

This process could be very overwhelming and to overcome the overwhelmingness, I realized that it helps to think big, but start small. The focus of the app should be the user and the user’s interaction with it. I wrote a few statements about what I wish a client should be able to do using my app. Things like, “user should be able to login and logout”, “user should be able to add menu items to the order” , “user should be able to delete items from the order” , “user should be able to track the delivery” , “user should be able to manipulate menu”, “an admin should be able delete, update, and add items to the menu”, etc. While thinking big like this, it is important to start with basic functionality, like “user should able to see the menu items coming from the backend’’ user should be able to add then to the order”. However, before all that, our next steps should be drawing a wireframe for the app, building the backend with models, associations, and creating some seed data to work with.

**# 3. Wireframing**

There are many tools. Here are some popular tools :

Figma

draw.io

Because I have a background in Photography and Graphic Design I naturally gravitate towards Photoshop. Nevertheless, for this project I used a pencil and a paper to draft my basic wireframe. It’s important to note that initial layout of your app is a subject to change as you build it, speaking from experience.

**# 4. Drawing out Models and Associations for later use in Rails .**

I decided to come up with most essential models for my app to work first, and then build more, and add more functionality later as the project grows.
My essential Models are :

**User**
`has_many :burgers`

**Burger**(MenuItem)
`belongs_to :restaurant`
`belongs_to :user` (an authorized user who creates it)

**Restaurant**
`has_many :burgers`

Model to add as the app grows:
**Order**(for now just built on the frontend)
**Delivery**

**# 5. Model Attributes and making a draft of the schema file**

**User**
```
name: string
email: string
username: string
password: password_digest
burger_id: integer
```
**Burger**
```
restaurant_id: integer
name: string
price: float
image: string
status: string
description: string
```
**Restaurant**
```
title: string
url : string
```

**6. Creating Rails App with Postgres**

Rails uses SQLite as a default, so to create Rails app with Postgresql we need to specify our database by entering

`rails new yourapp — database=postgresql — api`

in your command line.

Once the app was created run

`rails db:create`

to create the database otherwise you won’t be able to make the migrations.


**7. Scaffold generator**
To speed up the process I used scaffold generator to build out RestaurantsController, Restaurant Model, and resources :restaurants route in config/routes.rb file.
In order to create a table with attributes(migration) in my database for my Restaurant Model I ran this command:

`rails g scaffold restaurants title:string url:string`

You can use scaffold generator for all your models, I didn’t. I built the rest of the models manually. In order to just build a model and a migration you can use this command:

`rails g model user name:string username:string email:string burger_id:integer password:digest`

After building your models, make sure your migrations look good for migrating, if they look good, run :

`rake db:migrate`


This is the end of Part 1 in this blog series. In the next blog post I will talk about cors, routes, seed data, Rails Controllers and Serializers.

Please checkout [Github](http://github.com/Starcatch/burger-hub-frontend/tree/main)repo and the  [demo video](http://https://youtu.be/TskrOAz0Flw)  for this project.
