---
layout: page
title: "Expressions & Statements"
category: ref
date: 2016-11-16 14:18:42
---

A statement in RaptorScript is one of two things: A declaration or an expression. Everything that is not a function, class or variable declaration is an expression, and expressions are the most important structure. A couple of interesting "special" expressions are worth noting:

### The code block
One of the most versatile expressions is the code block. Any number of statements can be wrapped in brackets, returning the result of the last statement. This lets you do something like this:

    var weight = {
        if this.gender == "male"
            this.height * 40.2
        else
            this.height * 30.7
    }
    
Code blocks are also used for some more familiar code samples, like the body of functions and control statements.
