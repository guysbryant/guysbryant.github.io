---
layout: post
title:      "Rails With Javascript"
date:       2021-05-12 06:15:56 +0000
permalink:  rails_with_javascript
---


This project was a lot of fun for me. I really enjoyed connecting all the pieces I've learned so far in my education. Rails made setting up the backend extremely easy and the fast jsonapi gem simplfied serializing my data to send to the front end quick. I learned that you can create custom attribute readers with fast jsonapi and I wanted to figure that out. I created an attribute on my ProjectsSerializer called tasks. This returned all tasks associated with a project in the same format that the TasksSerializer would, except now its part of the project object. It also returns all users associated with a task, in the same way that the UsersSerializer would. This allowed me to build out the entire relationship chain in the frontend using classes for each object.

Each of the three classes associated with my api, Project, Task, User, all use a constructor to instantiate their respective objects. An instantiated project uses the Task constructor to instantiate its tasks when it is being built from data recieved from the api. Likewise, the User class constructor is used to build users that belong to tasks. This allows me to call someProject.tasks and get an array of User objects back and someTask.users yields an array of User objects. I built some static methods into these classes to store all instances of their own class for faster rendering when time to reload their data. This also prevented another call to the db and significantly sped up my load times.

I also implemented a static findById method on the Project class so I could pull out a specific project from Project.all. This project is the one rendered when selecting project from the homepage. Its tasks are then rendered with their associated users. It was interesting figuring out how to display data on a single page after growing accustomed to using restfull routing conventions in Rails to load various templates. I decided early on to just clear the innerHTML of the main content div and build out the HTML for the various cards fresh each time. This gives the appearance of making get requests to other urls and rendering different templates, without actually doing that. I put each class in charge of rendering its own content. They each build up the HTML needed and append it to the appropriate tags.

I build a Helper class to reduce some of the redundancy in the main JS file called index.js and to move out some of the HTML finding and generating code. I believe this enhances the clarity of the file so you can see exactly what the focus of the file is without getting bogged down in createElement, appendChild, and querySelector statements. Among the various additions this project could use, the rendering code in each of the three main object classes really should be cleaned up into the Helper as well. I'm sure that with a little effort, I could create a few generic Helper static methods which accept appropriate parameters to generate the necessary HTML to render all the content.

I'm now looking forward to React and Redux.

Thanks,
Guy Bryant

