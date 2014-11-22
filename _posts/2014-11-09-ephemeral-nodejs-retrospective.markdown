---
layout: post
title: "Ephemeral Retrospective - Learning and Summary"
date:   2014-11-09 16:19:00
categories: Projects Ephemeral
tags: nodejs ephemeral mongodb express jade
---
I closed off my project at the end of October since I had enough fun with the idea for now. In this post, I will write about design decisions for this web application. Here is where I really test my knowledge by thinking back on what I learned and what I still don't understand!

###Nodejs
- I feel like I have barely touched the surface of this platform
	With such a simple idea, I didn't really fully utilize the features node is useful for. 
- Managing dependencies and installing Nodejs programs were easy using the node package manager npm. The dependencies are managed in a file called package.json and it's a great place to keep track of them and their versions. If anything goes wrong you can easily delete the entire node modules folder and reinstall them using the command 

	```bash
	> npm install
	```

###Expressjs, web framework for nodejs
- It didn't take too many lines to get started with express in my application. 

	```javascript
	// Set up express
	var express = require('express');
	var app = express();
	app.use(express.json());
	app.use(express.urlencoded());
	app.set('views', __dirname + '/views');
	app.set('view engine', 'jade');

	// Example of a get request
	app.get('/', function(req, res) {
    res.render('index', {});
	});
	```
- As you can see, express was set up in about 6 lines of code! After that I'm free to set up the routing for the application!

###MongoDB
- A very different approach to storing data, everything you store in this noSQL database is called a document. They are essentially json objects!
- Didn't have to do much parsing since I was already working with a js framework. I was able to could work directly with the json objects returned by the database. I didn't have to write a completely different language (i.e. sql) for the database queries. The syntax fit really well with each other.
- When I had to change the schema, it was easily changed without affecting all of the existing data (not that there were many to begin with...). When I had to add a field to the form, I just had to change the schema in my models.js file which included the schema of my database and all of the database related functions I needed for the app. 
- I believe using MongoDB was a pretty good decision since the application was relatively simple and I only needed to store ephemerals. I'm not sure how well it would fare with larger applications with more than one type of "item". I have looked up on how to do joins in MongoDB and it doesn't seem as straight forward as joins in SQL. see [Mongo Docs](http://docs.mongodb.org/manual/reference/database-references/).

###Jade syntax, templating system
- First time I used a templating engine for html
- Extremely clean, no requirement to add closing tags!
- No angled brackets anywhere~!! 
- Removal of those extra ending tags made it easier to find things in the document
- Con: The spacing threw me off sometimes. My sublime was switching between tabs and spaces which is pretty important when you're using Jade! Rendering would break if you confuse the engine with the wrong number of spaces/tabs. Stick to one or the other -- spaces!!



##Personal thoughts

This is the first full stack nodejs application I started and completed. I wanted to make it short and sweet so that it wouldn't drag on forever. 
In this project, I was introduced to the templating library Jade, strengthened my working knowledge of routes in web development and noSQL database MongoDB, learned how to contribute to a large open source project hosted on Github, and practiced separating logic from presentation.  

###What I enjoyed most about this project
- Building the project from scratch and finishing it with no regrets!
- Learning new tools that help achieve a message that needs to be conveyed
- Broadens my understanding of web applications and how they're built
- Real application of design patterns learned in class (mvc)

###What was difficult
- Getting setup and geting started -- isn't that always the case?
- Gaining momentum - I learned that I really needed to work at it everyday or else I would lose momentum
- Getting the hang of callbacks!!! At first I was really confused, now I understand the true meaning of callback hell. :)

###What I learned
- Contributing to open source [blog post here](http://bchanisprogramming.blogspot.ca/2014/10/i-made-my-first-contribution-to-open.html)
- MVC: [date picker mvc](http://bchanisprogramming.blogspot.ca/2014/10/mvc-separating-state-from-presentation.html)
- Web application architecture
	
##Future
- Increasing development speed by getting more familiar with vim
- Strengthen knowledge on callbacks
- More testing to speed up development instead of manually testing things after big changes
- I hope to get more experience with different frameworks so I can compare and see the bigger picture of and develop an opinion about what type of framework works best for what.- Learn a new web framework -- perhaps rails..

Visit my page here:
[Ephemeral-messages](http://ephemeral-messages.herokuapp.com)