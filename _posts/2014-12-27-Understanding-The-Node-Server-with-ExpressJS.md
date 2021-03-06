---
layout: post
title: Understanding a Simple Node.js Server with ExpressJS
tags: 
    - code 
---

In this post we will build and review a simple Node.js server using ExpressJS. When I first began working with Node.js, I was amazed by how simple it was but I still didn't fully understand what was going. In this post, we will go over each line.

##Prerequisites

You will need to have Node and npm installed in order to load ExpressJS and run our server locally.

First we use **npm** to load our node dependency **Express.js**. Run this command in your working directory to do so.

```
$ npm install express --save
```

**install** will find the package by name and save it to your node dependencies in the directory **/node_modules**. The **--save** option saves the package to your dependencies in the file **package.json** located inside **/node_modules**. --save isn't required but it does a little extra work for you.

There are other options for saving to enhance your work-flow, check out the [npm install documentation](https://docs.npmjs.com/cli/install).

##The Server

Lets create our Node.js server in a file called **server.js**. This is the same file used in the [ExpressJS API Docs](http://expressjs.com/API.html).

```javascript
var express = require('express');
var app 	= express();

app.listen(8080);
console.log('listening on port 8080');
```

This is all you need to start your Node server, but let's go a little deeper on what's going on here.

**Require**, from a high level, is used to load Node libraries and modules. In the first line we are loading the **ExpressJS** Module into a the variable **express**.

The next line, running **express()** returns a JS function that is passed to Node's HTTP servers as a callback to handle requests. This enables you to write functions for API routes using our **app** variable.

The last line simply binds the object to your current host and port specified. Here we are listening for requests on **Port 8080**.

##API Routes

Lets add some routes to our server.js file and give our server some purpose. Add the following lines to the bottom of **server.js**.

```javascript
app.get('/', function(req, res) {
	res.send('Hello World');
});
```

This route will catch any **GET Request** to our host on port 8080 and send back the text **"Hello World"**. 

**Try it out** by running the following command and then pointing your browser to **localhost:8080**.

```
$ node server.js
```

You should be greeted by our message above.

##Sending HTML Files

Express allows you to catch specific routes and requests and send back files, JSON data, and much more.

When we point our browser to **localhost:8080** it makes an empty GET Request to our server and the text is sent back. 

Let's add a simple HTML file to make our server useful. 

Create a file called index.html shown below for our server to send to clients.

```html
<h1>
	Hello World 
</h1>
```

We will then reconfigure our Express API route to send the file we just created to clients and log the request.

```javascript
app.get('/', function(req, res) {
    res.sendFile(__dirname + '/index.html');
    console.log("got a request");
});
```

Now re-run your server with the command above and browse to **localhost:8080**. If you did everything right you should be greeted by the message in index.html!

##Moving Forward

Now with a fully working Node server you can make any changes to your index.html file, add some styling, and make it live for everyone to use!

##Full Files

**structure**

```
- server.js
- index.html
```

**server.js**

```javascript
var express = require('express');
var app     = express();

app.listen(8080);
console.log("listening on 8080");

app.get('/', function(req, res) {
    res.sendFile(__dirname + '/index.html');
    console.log("got a request");
});
```

**index.html**

```html
<h1>
	Hello World 
</h1>
```




