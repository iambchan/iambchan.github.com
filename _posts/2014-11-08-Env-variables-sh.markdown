---
layout: post
title: "Working with Environmental Variables in the terminal"
date:   2014-11-08 16:28:54
categories: terminal
---

I will talk about how I set up my variables for my application. This was useful when I don't want to store important information in the code, especially if it is being pushed to a public repository.
Here are a few important commands you can use in the terminal to set, view and unset environmental variables in shells.

Set sessional variables

```sh	
> export EMAIL_PW=somesortofpassword
> export EMAIL_USER=ephemeral.messages@gmail.com
```

How to view environmental variables

```sh
> env
```

how to set temporary variables for a specific application

```sh
> env PORT=3000 node app.js 
```

How to unset variables

```sh
> unset PORT
```