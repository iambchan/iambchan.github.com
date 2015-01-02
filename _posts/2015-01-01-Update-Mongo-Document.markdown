---
layout: post
title: "Updating a record in Mongo with Mongoose"
date:   2015-01-01 15:45:00
categories: Mongo
---

###Feature: 
Basic increment counter in mongo to keep track of total amount of messages being sent

###Issue: 
I was using a method "findAndModify" but was getting "has no method" error but kept thinking it was because I was incorrectly using the wrong method (I was looking at mongo documentation for findandmodify and assumed mongoose had the equivalent!) It turns out the correct method to use was "findOneAndUpdate".
I was initially used the update method but it didn't return the object after modification!

###Lessons learned:
  * Take the error message seriously -- if it says there's no method, look for the right method!! 
  * If you don't need the object after you've updated it in the db, then use update. Otherwise use updateOneAndModify. Using the latter allows you to use the object after it updates successfully!

    ```javascript
    function UpdateCounts(db, onSuccess, onFailure) {
        var query = { name: 'totalMessages' };
        var update = { $inc:{value:1} };
        var options = {};
        db.Globals.findOneAndUpdate(query, update, options, function (err, results) {
            if (err) { console.log(err); }
            else { console.log(results); }
        });
    ```

###Reference:
[Mongoose reference](http://mongoosejs.com/docs/api.html#query_Query-findOneAndUpdate)

    > Query#findOneAndUpdate([query], [doc], [options], [callback])
    > Issues a mongodb findAndModify update command.