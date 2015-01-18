---
layout: post
title: "MVC - Separating state from presentation!"
date:   2014-10-26 23:44:00
categories: Projects Ephemeral
---

The other day I was working on adding logic to the date picker on the main page of my application.

I wanted to add a feature to add days and months to the date picker with a single click.
The first approach I had taken was to directly write a js function in my main js file:

```javascript
function addDays(numDays) {
 // grab date in the date picker
 // add num days to date
 // update the date picker date with the newly calculated date using jquery
}
```
I had a span element with the on click listener hooked on to the addDays method above.
However, in this function, I was mixing logic with presentation. i.e. Logic where I was doing the calculations and 
updating the date picker value in the same function!

How can I separate this function such that it follows the MVC pattern? Essentially I have a variable that holds the state of the application:

```javascript
var appState = {};
```

In this variable I plan on holding the current value of the Date picker I have defined in my view. It is initiated on document ready to the current date.

I have a separate function (i.e. addDays(numDays) ) that has the job of updating the current date whenever I want to change it.
Finally I have an update view function that updates the view with the appState variable that I have declared earlier!

```javascript
function addDays(numDays) {
    var selectedDate = appState.currentDate;
    appState.currentDate = selectedDate.addDays(numDays);
    updateView();
    return false;
}
```
In the updateView method here, Im only concerned with updating the view with the values stored in my appState variable. I can call this function whenever appState is updated.

```javascript
function updateView() {
    $('#send_date').val(appState.currentDate.toDateInputValue());
    // Other values to update based on the appState variables I want updated.
}
```

Lesson learned today, separation of concerns! The method I learned today is to use a variable to hold the state of the application and update the view with my updateView() method.