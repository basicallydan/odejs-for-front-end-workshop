# What is NodeJS?

NodeJS is a runtime environment for JavaScript in the same sense that Google Chrome, Firefox or Internet Explorer are runtime environments for JavaScript.

Node is something which can be executed on any system which supports it, including Unix-based systems like Linux or OSX, and of course Microsoft Windows.

Crucially, NodeJS allows us to write scripts, servers, tools and all sorts of other software applications in JavaScript to run them mostly on the command line.

---

# What will we learn?

Today we're going to learn about creating a new Node project, about the npm package manager, about writing a simple REST HTTP API and about creating command line tools in NodeJS, using Unit Tests. Along the way you'll be picking up NodeJS idioms and learning about some useful packages.

---

# Your First NodeJS Application

We start new NodeJS projects by initialising it on the command line. Go into a new folder for your project and type

```
npm init
```

You'll get an interactive wizard-style tool for defining a few project properties, each of which have defaults. For now, let's just hit enter through each of them and allow npm to set them up for us. This has created a file called `package.json`, which contains information about your project such as the name, version number, author and dependencies. More about that later.

The first program we're going to write is a classic: a Hello World application. You're probably all familiar with the syntax we're gonna use.

SEE `hello-world/index.js`

--

So, very simple, one line. To run it, we're just gonna go into our folder on the command line and type `node index.js`. You should now see your console writing out those timeless worlds.

Next thing we're gonna do is start getting some dependencies.

---

# Modules

Normally in front-end JavaScript, to include some code that someone else has written we just use an HTML `<script>` tag, right?

Well, in NodeJS we use split code into modules. A module is just a load of JS code, like a jQuery plugin or some other front-end JavaScript library, but it's written in such a way that it can be saved to your project easily and included in any other file easily.

Well in NodeJS, we use the `require()` function, which fetches the module that we need and gives us all of the functions and properties which it advertises.

In Node, there are a lot of modules which are available out of the box. For example, let's `require` the path module.

```js
var path = require('path');
```

SEE `hello-world-path/index.js`

---

# The Node Package Manager

The Node Package manager is a command-line tool and, in a way, a whole ecosystem of hundreds of thousands of JavaScript modules written by developers around the world to solve common problems.

The npm directory is searchable at http://npmjs.org/, so if you are looking for a module to do a certain task you can probably find it pretty easily.

Let's write a simple application which will make an HTTP request to Reddit's API and list all of today's most popular Today I Learned posts.

First let's make a new Node project in a folder called 'todayilearned'. In that, do an `npm init` and then type:

```
npm install request --save
```

This not only downloads the `request` module, but it also saves it as a dependency for your project. That means that if you ever delete the module's files, or someone has downloaded your project without all the modules in it, they need only type `npm install` and all the dependencies will be downloaded automatically.

So let's get to writing some code.

SEE `todayilearned/index.js`

---

# Writing our own modules

So, now that we know how to use modules, we can write our own!

We're going to turn our Reddit Today I Learned script into a self-contained module which can be called from other places. In order to make it work, because it contains asynchronous code, we'll need to give it an idiomatic node callback.

---

# Test-Driven Development

We're going to use the technique of test-driven develop to create a slightly more complex script now: one which will keep track of sales at a hypothetical shop. We need to be able to store sales in memory, as well whether the customer paid it, how much cash they paid with and how much change they are due.

For this we're going to use Mocha, a NodeJS test runner. We need to write automated tests whose job it is to describe a feature of our module. We'll write tests which execute our code with certain inputs, and validate that the code will produce certain outputs.

To install mocha, use `npm install mocha -g`

SEE `checkout-tdd/Checkout.js` and `checkout-tdd/index.test.js`

---

# REST

Rest stands for Representational State Transfer. The idea is that by using HTTP Requests with certain HTTP Methods such as GET, POST and PUT we can drive the state of an application.

In this example, we're going to use the module we wrote in the last section and turn it into a REST API.

SEE `checkout-rest/server.js`

---

# Executing your code as a standalone package

---

# Publishing your code to npm

---

# NodeJS Packages of Note:

* ExpressJS: `npm install express`
* Commander: `npm install commander`