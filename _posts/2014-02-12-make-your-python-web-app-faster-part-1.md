---
layout: post
title: "How to make your Python web app faster? Part 1: Best practices and basic tools"
description: "Python app performance"
category: programming
tags: ["python"] 
---

Imagine this picture. You just had commited the latest feature request,
tests are green and you deploy to production server. Suddenly, the unread count of your inbox starts to go up. 

One, two and then twenty emails from your server monitoring. Your website is time outing like crazy.
Hackers? No, the server is ok, traffic isn't that bad. 
Bug? But the tests are ok.

After hours of debugging you find the problem and you're not going to like it. Your code is ok - it's just slow.
And deep in your heart you know fixing it is going to be painful.

**Should writing fast code be hard?**

**Yes, it should.**

We focus on optimising Python, we use it for business logic **(BL)** only. 

But a typical app architecture usually looks like this:

![Actual app arch](/public/app_arch.png)

The problem is that only write **BL** in Python, but there's a database, a web server and a lot more. Optimising apps is an art, where sometimes you rewrite and sometimes you cheat.

## How you can write code for performance

> "We should forget about small efficiencies, say about 97% of the time: premature optimisation is the root of all evil" **Donald Knuth**

As a general rule of thumb, never think about performance and write code. 

Usually your code will be performant enough. But, there are cases when you will need to tweak the performance of your code. So…

**How can you write code that's easy to rewrite for performance?**
 
Here's a few things you should do:

- Write readable code 
- Use datastructures  
- Write tests

When I have to rewrite code for performance reasons, I read the existing code first. The faster I understand what it does, why and where's the problem - the faster I can fix it.  And don't tell me to check specs - they usually do not exist.

That ties in directly to why writing tests is a good practice from performance view. When I make an assumption about the code  - I can be wrong. Tests help me validate my assumptions, since I see whether my new code passes or not.

The guideline I stick to is writing as little new code as possible . Python has terrific standard library and phenomenal collection of battle tested modules written by the community and available via pip.  Don't solve problems someone already solved.


## How you should think about performance in Python

Low level languages are fast. I let myself program in Python the way I did in C, to improve performance. You probably make the same mistake.

C is close to the bare metal. Performance in Python is not about being close to the metal. It's more about choosing the right tool for the job and applying it the right way.

And yes, sometimes you will use a trick instead of fixing the code.

## The swiss army knife of Python profiling

Code is still not fast enough? Use **IPython**. With the recent premier of the 2.0
version IPython is the most powerful tool I know for performance focused work (and Python programming in general). 
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

**There's a limit to what we can achieve just in Python**. 

Next articles will focus on that. What you can do, when you need more performance and there's just now way to make your code any faster just by utilising traditional approaches.




———
# materials


- [http://pythontesting.net/framework/nose/nose-introduction/](http://pythontesting.net/framework/nose/nose-introduction/)
- [http://pythontesting.net/framework/unittest/unittest-introduction/](http://pythontesting.net/framework/unittest/unittest-introduction/)
- [http://www.huyng.com/posts/python-performance-analysis/](http://www.huyng.com/posts/python-performance-analysis/)
- [http://cgoldberg.github.io/python-unittest-tutorial/](http://cgoldberg.github.io/python-unittest-tutorial/)
