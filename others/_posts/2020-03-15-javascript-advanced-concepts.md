---
layout: post
title: JavaScript Advance Concepts
description: >

---

# Javascript 

## Javascript Engine

An **ECMAScript engine** is a program that executes source code written in a version of the [ECMAScript]() language standard, like _JavaScript_.

These new generation ECMAScript engine for web browsers,all implementing `just-in-time compilation` (JIT) or variation of that idea.The performance benefits for _just-in-time compilation_ make it much more suitable for web application written in _JavaScript_.


- **Carakan**: A JavaScript engine developed by _Opera Software ASA_.
- **Chakra (JScript9)**: A [JScript]() engine used in _Internet Explorer_.
- **Chakra**: A JavaScript engine used in _Microsoft Edge_.
- **SpiderMonkey**: A JavaScript engine in _Mozilla Gecko_ application, including _Firefox_.
- **Tamarin**: An [ActionScript]() and ECMAScript engine used in _Adobe Flash_.
- **V8**: A JavaScript engine used in _Google Chrome_, _Node.js_ and _V8.NET_.
- **Nashorm**: A JavaScript engine used in _Oracle Java Development Kit_ (JDK) since version 8.

> Who created the first Javascript Engine ?

Brendan Eich is the creator of the JavaScript programming languages and _SpiderMonkey_ engine. He co-founded the Mozilla project.


## JavaScript Engine

<!-- need to add image it doesn't  make meaning -->
[JS Code] --> [Parser (Lexical analysis)] --> [AST (abstract syntax tree)](https://astexplorer.net/) --> [Interpreter] |-> [Byte Code] |-> [Profiler] --> [Compiler] --> [Optimized code] 


## INTERPRETER & COMPILER

> Is JavaScript an Interpreter languages?

> Why not just use machine code from the beginning ?

### VASCRIPT Engine

- `eval()`
- `arguments`
- `for in`
- `with`
- `delete`


> inline caching
```javascript
function findUser(user) {
    return `found ${user.fistName} ${user.lastName}`;
}

const userData {
    fistName:'john',
    lastName: 'doe'
}

findUser(userData)
```
> hidden classes

```javascript
function Animal(x,y){
    this.x = x;
    this.y = y;
}
const obj1 = new Animal(1,2);
const obj2 = new Animal(3,4);

obj1.a = 30;
obj1.b = 100;
obj2.a = 30;
obj2.b = 100;


```

[WebAssembly]()

## Javascript is single threat





because is has one `callStack` what why JavaScript `synchronous` 


> What problems do you see with synchronous code ?


[laten flip](http://latentflip.com/loupe/)