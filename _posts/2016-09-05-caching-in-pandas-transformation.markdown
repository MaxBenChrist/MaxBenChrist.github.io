---
layout: post
title:  "Caching in python pandas"
date:   2016-09-05 20:00:00 +0100
categories: Python, pandas
comments: True
tldr: A few examples why you should considering caching transformations
---

__TLDR: A few examples why you should considering caching transformations__

---
<br>

Caching describes a process where one saves results of calculations with the goal of not having to repeat costly operations.
If the memory and lookups costs are lower than one calculation and the same results is asked for several times, caching is the right thing to do.

Simple example with pandas Datetime transformations

Functionstools have a decorator that implements everything:

So if your are profiling your code and find methods that get a lot of heat, try to wrap it with the cache decorator.


"One of the things I was most excited about as Python evolved was the opportunity to use decorators to attach reusable functionality to functions and methods."

"
Typical uses for decorators involve altering or validating the input to a function, altering the output of a function, logging the usage or timing of a function, and—especially in web application frameworks —controlling access to a function. You can apply as many decorators as you want, too—it’s nesting dolls all the way down!
"

The hashing decorator only calls the function it wraps when it has not calculated the result before
