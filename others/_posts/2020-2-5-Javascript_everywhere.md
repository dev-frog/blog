---
layout: post
title: JavaScript EveryWhere
description: >

---

# JavaScript EveryWhere


## Prettier

Prettier is a code formatting tools with support for a number of languages, including JavaScript, HTML, CSS, GraphQL and Markdown.
It makes it easy to follow basic formatting rules, meaning that when you run the Prettier command, your code is automatically formatted to follow
a standard set of best practices. 


## ESLint

ESLint is a code linter for JavaScript. A linter differs from a formatter, such as Prettier, is that a linter also checks for code quality rules, such as unused
variables, infinite loops, and unreachable code that falls after a return.As with Prettier, also recommend using the ESLint plug-in for your favorite text editor.
This will alert your to errors in real time as you write your code.


## API 

- Users will be able to create notes, as well as read, update, and delete the notes they've created.
- Users will be able to view a feed of notes created by other users,and read individual notes created by others,thought they will not be able to update or delete them.
- Users will be able to create an account,log in and log out,
- Users will be able to retrieve their profile information as well as the public  profile information of other users.
- Users will be able to favorite the notes of other users as well as retrieve a list of their favorites.
  
## Getting started

```bash

mkdir api && cd api

npm init -y

```

## A Web Application with Node and Express

We'll be using the  `Express.js` framework, a minimalist web framework for `Node.js` meaning that it does not ship with a lot of feature,but is highly configurable.We'll using `Express.js` as the foundation of our API server, but `Express`  can also be used to build fully featured server side web application.

```bash
npm install expression

```

Create a file named `index.js` and add the following

```javascript

const express = require('express')
const app = express()
const port = 4000

app.get('/', (req, res) => res.send('Hello from API'))

app.listen(port, () => console.log(`Server listening on http://localhost:{port}`))


```
