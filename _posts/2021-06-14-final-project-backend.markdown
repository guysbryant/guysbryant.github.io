---
layout: post
title:      "Final Project Backend"
date:       2021-06-14 19:20:41 +0000
permalink:  final_project_backend
---


I decided to create category and posts project similar to a forum. The categories are called circles and the posts belong to a circle. The goal being that a user can create a new circle, and create posts on any available circle. The backend of my project was easy to setup. I used the following command to setup a new rails project as an api, without tests, and using postgres as the database: rails new connect-api --api -T --database=postgresql
I setup a few basic models, circle, post, and user. After setting up all the necessary relationships and verifying they worked as expected in the rails console I moved on to the serializers. I brought in the fast json api to handle the serialization for this project as I had some experience with it from a prvious one. I used rack-cors and configured the cors.rb initializer to accept data coming from my react server. This whole process was relatively quick, painless, and easy to test as went. Once I was able to visit routes in my browser and see the json data I wanted, it was time to move on to the front end of the project. I'll put this into another blog post. 
