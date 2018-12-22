---
layout: post
title:      "CLI Web Scraping Project"
date:       2018-12-22 19:34:58 +0000
permalink:  cli_web_scraping_project
---


I felt well prepared for this project. I had progressively learned many relevant skills since starting at the Flatiron school. I coded along with three different CLI web scraping videos, and I followed along with my section lead as she built one live over three or four hours. I was all laid out in my head, all I neeed to do was start typing. While I never hit a wall during this project, there were a few hurdles that sent me to Google to get past.

The main steps for this build were:

0. Write up what your project is about, what it does, and how it does it.
1. Setup file structure
2. Add needed gems
3. Stub out general responibilities for each class
4. Get each class working
5. Refactor
6. Style


**0. Write up what your project is about, what it does, and how it does it.**
    HOW: I had a list of requirements and a checklist that asked me some good questions for this project which after answering, I had a good writeup for my project.

    HURDLES: The biggest hurdle here was to take the time to do this step because my initial reaction was to just start trying to code.

    LEARNED FOR NEXT TIME: Taking the time to complete this step makes subsequent steps go more smoothly.
    
**1. Setup file structure**
    HOW: I used bundle gem [project name] to setup the initial file structure. This was beautiful and painless but it was my first time doing it on my own.
        By default bundle gem [project name] creates a lib/[project name]/ directory where you are to put your classes and a lib/[project name].rb file that is meant to be used to require all the classes in lib/[project name]/ with require_relative. I saw somebody else rename their [project name].rb file to environment.rb and that made sense to me so I followed that pattern. 

    HURDLES: I had to spend some time getting the hang of require and require_relative to get all of my files talking to each other. I defined a start method in my cli class that simply executed puts 'sup'. I had my console file call to cli.start so when I ran ruby bin/console and saw sup in my terminal, I knew that I was atleast going in the right direction.

    LEARNED FOR NEXT TIME: The file in bin/ which will call to my classes should require "./lib/environment"
    lib/environment.rb should require_relative "..lib/[project name]/[class]" for each class in the project.

**2. Add needed gems**
    HOW: I did a few different things to get the extra gems to work in my project. I ended up using gem [gem name] in my Gemfile

    HURDLES: First let me just say that there is more than one way of adding a gem to your file and making it work even though I'm sure there is a best way to do it. In the beginning I modified my .gemspec to have spec.add_development_dependency [gem name] and this worked just fine. I learned from a Flatiron instructor that for my project to run on another computer I need to add them to the Gemfile and not the .gemspec. So I cloned my project on to my Chromebook and sure enough it didn't work. I moved everything over to the Gemfile and that fixed the issues so that all I needed to do was run bundle install and all the gems in the Gemfile would be installed and the project would run.
        Another hurdle was the use of require [gem name] in my class files. I had required some gems in multiple files and that didn't make sense after I took some time to understand how the Ruby Interpreter looked my project. The require statement should just teach the interprete how to understand some specific lines of code that it otherwise wouldn't understand. For example, binding.pry, that means nothing to the interpreter. However, if you have require 'pry' in your class file, then the interpreter can actually read that and know how to respond. So here I am with some gems being required in multiple classes and I have an environment file sitting there just requiring classes. I moved all the require [gem name] statements into environment.rb and removed them from the class files and... nothing changed. Which is exactly what I wanted so that was cool.

    LEARNED FOR NEXT TIME: The Gemfile is the right place to add other gems to your project and is simply done with gem [gem name].
        If you have an environment file and plan on using a gem in multiple classes, just require [gem name] in environment.rb and then you can use that gem in ever class which is required in your environment file. I'm not sure the best way to handle a case where you only want to use a gem in class though, maybe only require it in that class?

**3. Stub out general responibilities for each class**
    HOW: I had already written out a general idea of what my program was going to do. So I used the verbs to create methods such as list, scrape_events, scrape_more_info, add_more_info, quit. Then I added comments to all of my methods to describe what they were supposed to do which included my best guess as to how certain values would be accessed. I filled in the basic code for some of the methods that made sense to me even though I knew some of it would change as the project developed.

    HURDLES: The only real challenge at this step was feeling confident in how I wanted the program to run and in the names I chose for variables, methods, and properties. 

    LEARNED FOR NEXT TIME: A project shouldn't start with code. Having a well written understanding of what your project is going to accomplish and how it will go about doing that really helps in creating the pseudo code that becomes the code.

**4. Get each class working**
    HOW: Now that I had created the main methods for each class and had some logic in them, I needed to actually make them do what they were created for. This process is really hard to explain in writting. I think that's because even though it is one step, it is really a lot of little steps, many of which are very unique to each class and class method. 
        A summary of this step might look like:
        a) have class method puts out a string 
        b) call class method and confirm the string is displayed in terminal 
        c) add binding.pry to the method 
        d) confirm that any values being passed to the method are coming in the way you expect
        e) create the method logic
        f) confirm that the method is returning what you expect it to return and in the way you expect 
        * Every step mentioned and forgotten here has the necessary Google search, ask a friend, and look at previous code lifelines.

    HURDLES: Typos, logic, bad assumptions. 

    LEARNED FOR NEXT TIME:
        I'm not really sure what I can apply to my next project from this section except for the general skills required and honed by performing this step. Skills such as logic, analysis, language specific capability familiarity, using obeject orientation, etc. These are skills which improve as you use them and I think that if you don't enjoy this process at all, you are probably going to have a bad time building software. For me this was great. Even simply figuring out how to make the quit method work felt like a great achievement.

**5. Refactor**
    HOW: Changed some variable names, decided not to out put some data, modified some of the data being returned so it looked better.

    HURDLES: This is another instance of trying to figure out what makes the most sense or best accomplishes a goal. Feeling confident that I was making the best choices and not overlooking something was difficult.

    LEARNED FOR NEXT TIME: Don't stress over the initial names or logic, just get it to work because chaning names and making something work better is easy. Just keep making progress.

**6. Style**
    HOW: I added in some newlines into my strings to make the output more readable and used the colorize gem to add some color.

    HURDLES: I spent too much time looking into various gems to style the console output...
        I had puts printing out a single long string with interpolated values and escaped newlines and colorize works with individual strings so I had to break up my string into longer parts. I ended up using a combination of interpolation and concatenation with comma separated sections to accomplish my goal. 

    LEARNED FOR NEXT TIME: Styling can take a long time.
