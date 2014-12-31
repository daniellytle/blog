---
layout: post
title: Understanding a Simple Node.js Server with ExpressJS
tags: 
    - code 
---

In this post we will build and review a simple Node.js server using ExpressJS. When I first began working with Node.js, I was amazed by how simple it was but I still didn't fully understand what was going. In this post, we will go over each line.

##Prerequisites

You will need to have Node and npm installed in order to load ExpressJS and run our server locally.

First we use **npm** to load our node dependancies **Express.js** and **Socket.io**. Run these commands in your working directory to do so.

```
$ npm install socket.io --save
$ npm install express --save
```

**install** will find the package by name and save it to your node dependencies in the directory **/node_modules**. The **--save** option saves the package to your dependencies. There are other options for saving to enhance your workflow, check out the [npm install documention](https://docs.npmjs.com/cli/install).

##The Server

Lets create our Node.js server in a file called **server.js**

```javascript
var app = require('express')();
var server = require('http').createServer(app);

// listen on port 8080
server.listen(8080;
```

Now run the server locally.

```
$ node server.js
```

You now have created a Node.js server listening on port 8080! While this server is nearly useless, well done!

Lets add a default Express route that will send back a simple message for any request. Add the following code to the bottom of **server.js**.

```javascript
app.get('*', function(req, res) {
    res.send('well hello there');
});
```

Now point your browser to localhost:8080 were our server is listening. You should be greated with our prepared message.

That's cool but lets bump it up a notch. Create a file called **index.html** that we will send to clients rather than just simple text.

```html
<body>
    <h1>Hello Folks</h1>
</body>
```

to be continued...
