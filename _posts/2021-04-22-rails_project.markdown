---
layout: post
title:      "Rails Project"
date:       2021-04-23 01:43:00 +0000
permalink:  rails_project
---


I decided to create a sales order management application for a business facing company to track the products they sell and the businesses they sell too. I enjoyed working through this and testing my understanding of Rails. Even though my project is able to pass the requirements right now, there are so many little details left unfinished that I plan on revisiting this at a later date to really flesh it out.

My process was to first sit down with a text editor and think through some of the basic requirements I would need. This included figuring out who I thought might use the app and what kinds of things they would need it to do. After about fifteen minutes of this brainstorming, I used MySQLWorkbench to map out by schema. The schema process helped me to see more clearly some of the issues I would need to tackle in the project and it was at this stage that I began to cut back the scope of my project. The original version included a full inventory management component with the mindset that the company was manufacturing their own products to sell. I don't think it would be any more difficult to implement this now, it would just add more time before I could move on in my curricullum. I plan to revisit this inventory management at a later date.

After settling on my schema it was time to create the project and generate some resources. I quickly decided that I had poorly named one of my resources and wanted to change it; from purchase order to sales order. It was a small change but one I needed to search documentation to learn how to do...something that would become a regular part of the rest of my process. 

At this point I didn't need to think too deeply about what I was doing so I turned on some music and went about creating the basic code for my migrations, routes, controllers, models, and views while testing them in browser. Everything was going smoothly...until I began to implement a form that needed to create an object that was associated with another object.

I knew that this was the time to implement a nested form but I did it the wrong way. If you look at commit: 4e8ca22, you will see my first solutiion to this problem using a form builder that accepts two objects at once. There were a number of challenges with this approach but I got it working. After this, I began working on using a proper neested form with nested attribute writers. In order to really push my understanding I went ahead and implemented a doubled nested form too. Afer adding some logic into my nested attributes writer to handle a couple different cases, I felt confident that I actually knew what was going on. I struggled with this enough to justify its own blog post.

The rest of the project went smoothly. I created a handfull of branches along the way so that I could have a safe sandbox to try out my new code. After finishing the new feature I merged the branch back into master and began working on the next problem. 

The last thing I did was to clean up my code. Some things were obvious to me, nested logic in a view to determine what gets rendered went into a partial. Was a controller action complicated, move some of that work to the model. I created two special controller actions for omniauth and that seemed wrong so I moved all of that into the model too. I'm not sure what the best practice is here so I just came up with my own strategy. I passed the request and the params to a custom class method in the User model called make user. I did a quick check to see wheter the request included 
"auth" in the  "path info". If it did, I passed part of the request to another class method called make by omniauth which performs a create or find by using information from the request. Otherwise, I passed the params to a different method called make by local wich just finds a user using the params. Either way, a hash is returned to the controller with a user key and a method key. The user is used to set the user instance varialble in the controller and method is used to decide wether or not the controller action needs to authenticate the password when determining if the user is valid. 
