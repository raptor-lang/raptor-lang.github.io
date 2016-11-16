---
layout: page
title: "Control Statements"
category: ref
date: 2016-11-16 14:12:52
---
RaptorScript has a fairly standard set of control statements, but there are some slight implementation details that are different, mainly regarding how they use expressions

### Conditional statements

`if` statements in RaptorScript use the `if` keyword, take a conditional expression and a statement. An optional `else` clause can be specified.

This is an example of an if statement. Note that code blocks, and thereby brackets, are only necessary if the body consists of more than one statement.

    if a > 4 {
        print("a is greater than 4")
    } else if a == 4 {
        print("a is equal to 4")
    } else {
        print("a is less than 4")
    }


### Loops

1.  Infinite Loop

        loop {
            print("I'm working")
            sleep(3)
            if time.now() > time.from_string("19:30") {
                print("It's late, I'm heading home")
                break
            }
        }

2.  While Loop

        while time.now() <= time.from_string("19:30") {
            print("I'm working")
            sleep(3)
        }
        print("It's late, I'm heading home")
        break

3.  For Loop

        // TODO

### Pattern Matching
