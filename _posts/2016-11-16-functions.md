---
layout: page
title: "Functions"
category: ref
date: 2016-11-16 14:19:54
---

Functions are declared using the `fun` keyword. Its arguments _must_ be type annotated, and a return type also has to be specified after the parenthesis.

After the return type and an equals sign, is the body of the function. The body is any expression, so of course a [code block](#the-code-block") will work too.

    // TODO: Improve example
    fun is_odd(a: Int): Bool = {
        a % 2 == 1  // No return keyword required because it's the last expression of the function
    }

