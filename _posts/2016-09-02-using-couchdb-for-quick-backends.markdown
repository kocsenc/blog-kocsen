---
layout: post
title:  "Using CouchDB for a quick REST API backend"
date:   2016-09-02 8:00:00 -0500
---


## You have a great idea for a small web app, but you don't want to deal with the backend?

### ENTER CouchDB!

![PC Engines Box](/assets/couch.png)

# It takes less than a minute to setup a RESTful backend

Excerpt below is copy-paste fiendly :).

```
brew install couchdb &&

couchdb -b &&

curl -X PUT http://localhost:5984/recipes &&

curl -X POST http://localhost:5984/recipes -H 'Content-Type: application/json' -d  '{"dish":"omelet","serves":2,"needs":["eggs","oil","love"]}' &&

open http://localhost:5984/_utils/index.html
```

> Tip: The `&&` executes the next command given the previous one succeeds.

### Breakdown
The first commands install and run couchdb in the `-b`ackground.

The first `curl PUT` command creates a database called `recipes`.

The second `curl POST` command creates an entry in the database with the json data.

The website at `_utils` is the magic sauce. It's called [Fouton][fouton].
It's CouchDB's administrator console. Where you can view, edit and perform
anything you will ever want to do with your data.

You can also update or delete documents. See this [tutorialspoint post][tpoint] for a detailed explanation.

That's it. Before you know it you have a database where you can just save
JSON data.

Now grab your favorite front-end web framework like `AngularJS` or `React` and
start saving data.

# Ideas

Here's a quick brainstorm:

- I recently used this to keep track of my wedding RSVP's. I could execute queries like see how many guests are coming or how many guests have dietary restrictions. I even hooked in Twilio to text my bride and I every morning how many people were going to attend.
- Keep track of score on your weekend poker or sports game.
- Set up a private twitter with you and your friends.
- Keep track of your favorite recipes.

# Security Concerns

Although this is immensely convenient, there are some drawbacks - security.
You can put Couch behind SSL and password protect Fouton but unless you want
to implement your own auth system this wont really store your data securely.

### Additional Reading
- [Official docs][official]
- [Free online book][http://guide.couchdb.org/editions/1/en/index.html]
- [Quick angular prototype guide][angularprototype]
- [Use PouchDB for offline data sync][offline]

[couchdb]: http://couchdb.apache.org
[fouton]: http://docs.couchdb.org/en/stable/intro/futon.html
[angularprototype]: http://thewebhacker.com/rapid-app-prototyping-with-angularjs-and-couchdb/
[offline]: https://medium.com/@redgeoff/is-pouchdb-fast-enough-for-my-app-5e36d28a831f#.u59o1v2hi
[tpoint]: http://localhost:4000/2016/09/02/using-couchdb-for-quick-backends.html
[official]: http://docs.couchdb.org/en/stable/intro/tour.html
