---
layout: post
title: "How to make your Python web app faster? Part 1: Best practices and basic tools"
description: "Python app performance"
category: programming
tags: ["python"] 
---

Imagine this picture. You just had commited the latest feature request,
tests are green and you deploy to production server. Suddenly, the unread count of your inbox starts to go up. 

One, two and then twenty emails from your server monitoring. Your website is timeouting like crazy.
Hackers? No, the server is ok, traffic isn't that bad. 
Bug? But the tests are ok.

After hours of debugging you find the problem and you're not going to like it. Your code is ok - it's just slow.
And deep in your heart you know fixing it is going to be painful.

**Should writing fast code be hard?**

Over the last few years I've seen a multitude of performance related problems in web apps written in Python.
There's lots of noise mixed and usefull information is scattered across multiple sources.

This post is the first in a series on making Python web apps fast. 

**What can you expect?**

I'm going to start from the level of function-level applicable practices and then I'll work my way up. I'll be covering approaches to storing data in memcache and there will even be a primer on using 'heavy' solutions such as Varnish to cache whole webapp for a while.

**Is this guide for you?**

It's for every level of craftmanship. People just starting programming will learn best practices and what's possible with Python.

Professional developers will get a comprehensive guide they can refer to anytime. And I hope even the tenured hackers will be able to pick up a trick or two.

**What will I get today?**

In this article you will read about best practices to make your work easier and what's the number one tool you need for performance profiling.

## How you can write code for performance

> "We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil" Donald Knuth

As a general rule of thumb, never think about performance and write code. 

Usually your code will be performant enough. But, there are cases when you will need to tweak the performance of your code. 

**How can you write code that's easy to rewrite for performance?**
 
Here's a few things you should do:

- Write readable code 
- Use datastructures  
- Write tests

Now, why I promised you performance and here I am starting from readable code. Why?. 

When I have to rewrite code for performance reasons, I read the existing code first. The faster I understand what it does, why and where's the problem - the faster I can fix it.  

That ties in directly to why writing tests is a good practice from performance view. When I make an assumption about the code  - I can be wrong. Tests help me validate my assumptions, since I see whether my new code passes or not.

The guidline I stick to is writing as little new code as possible . Python has terrific standard library and phenomenal collection of battle tested modules written by the community and available via pip.  Don't solve problems someone already solved.


## How you should about performance in Python

I used to make a terrible mistake. 
Low level languages are fast. So I let myself program in Python the way I did in C, to improve performance. You probably make the same mistake.

C is close to the bare metal. Performance in Python is not about being close to the metal. It's more about choosing the right tool for the job and applying it the right way.

There's no one simple way to have fast Python code. Sometimes you will have to implement an algorithm and sometimes you will have to think about what data you have to process. And yes, sometimes you will use a trick instead of fixing the code.

I hope you like the pursuit of optimal solution that is fast  and other can understand. That's your bread and butter when you work on performance.

## Get the swiss army knife of Python profiling

Code is still not fast enough? Use **IPython**. With the recent premier of the 2.0
version IPython is the most powerfull tool I know for performance focused work (and Python programming in general). 
It gives you:

- Code completion and ability to prototype code
- Smart paste via **%paste** magic method
- Ability to time code execution with **%timeit**  and **%time** magic method

Beyond that, **IPython** lets you install additional magic commands with **%load_ext** command, and there are modules you can hook to your profiling session using this.

For example, in case you want to profile memory of your code, you just need to 
```
pip install memory_profiler
```

and in your IPython session:

```
> %load_ext memory_profiler
> %memit print('a')
```
How cool is that? 

I won't go far into **IPython** in this. Instead, I will recommend the best materials that I've found

- looking for the best overview of IPython magic commands - check this [link](http://pynash.org/2013/03/06/timing-and-profiling.html)
- working with Big Data or AI - go [here](http://scikit-learn.org/dev/developers/performance.html#profiling-python-code) 

# Summing up

In this article I've covered ways to make sure your code is crafted well enough to be easy to rewrite for speed or better memory efficiency.

But, **there's a limit to what we can achieve just in Python**. 

Next articles will focus on that. What you can do, when you need more performance and there's just now way to make your code any faster just by utilizing traditional approaches.




———
# materials


- [http://pythontesting.net/framework/nose/nose-introduction/](http://pythontesting.net/framework/nose/nose-introduction/)
- [http://pythontesting.net/framework/unittest/unittest-introduction/](http://pythontesting.net/framework/unittest/unittest-introduction/)
- [http://www.huyng.com/posts/python-performance-analysis/](http://www.huyng.com/posts/python-performance-analysis/)
- [http://cgoldberg.github.io/python-unittest-tutorial/](http://cgoldberg.github.io/python-unittest-tutorial/)
