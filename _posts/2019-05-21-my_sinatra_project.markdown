---
layout: post
title:      "My Sinatra Project"
date:       2019-05-21 22:28:42 +0000
permalink:  my_sinatra_project
---


For my Sinatra Project, I created a basic inventory management system. There are two types of uses, basic users, and management. Basic users can access their assigned department's inventory and perform all the CRUD actions on items in the department inventory. Management can do everything a basic user can do, plus they get to perform CRUD actions with the users and departments. 

At first I only used two models, one for items and one for users. A user has_many items and an item belongs_to a user. I had to look up quite a bit to get everything setup and found myself just trying to finish the project so I could submit and move on in the course. As I got near the end, I decided that I needed some more hands on experience with some of the concepts I was meant to be learning.

I added another model, departments, to my project. I decided that items should belong to a department and users should access those items only if they have access to that department. I thought this matched up more closely with real world inventory management. Adding what seemed like such a small change resulted in a considerable amount of additional work. I needed a join table, two has_many through relationships, and I had to figure out how to control access to the different departments.

Even though I found myself debugging an infinite loop for an hour, this extra complexity was so much more fun to work with than the basic project I started with. I really enjoyed figuring out how to take the two model basic relationship app that I started with and turn it into something more complex and more useful, I know those two concepts don't always go hand-in-hand.

