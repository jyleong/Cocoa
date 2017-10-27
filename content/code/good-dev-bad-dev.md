+++
title = "How to tell a good engineer/developer from a bad one"
date = "2017-10-26T21:27:48-07:00"
draft = false

+++

I see that this title is sort of an explosive one that could lead to some debates.
However, these are the qualities I look into a person to tell if they are a good engineer/developer or scientist in terms of technical skills and work habits:

### 1. They know how to science.
### 2. They know how to shorten their feedback loop
### 3. They know when to ask for help

Let's dive deeper into these points:

### They know how to science
As in, they know how and when to apply the scientific method to to figure out problems, and to find out about something they don't know. See, the scientific method isn't just for experimentation, it can be used to solve everyday problems, by trial error, expecting what happens, observing what happens, and trying again.

Programming is like 10% writing your code, and 90% debugging, which is fixing whatever broken mess you wrote. Basically programming is like an experimental and observational science.

### They know how to shorten their feedback loop
This is crucial, if you are spending the majority of your time trying to figure out what is wrong in your code, you better be efficient about it. The principle of this is that you can reduce down a problem into its smallest component under question, test it, make the process very quick, and make this experimentation process very reproducible

I also learned this tip from a good youtube video by [Charisma on Command](https://www.youtube.com/watch?v=YLwFbwPbqyY) 

I see junior dev's, interns, CS students, coders do this constantly. They basically compile, build their whole project, to test out if one particular piece of code is working. THAT IS NOT A GOOD USE OF YOUR TIME. There is a lot of room for optimization.

Take this example here where I'll apply the top two tips into one:

Say we are going to write some Python code to make some http requests to a new third party API that we intend to develop for some product.
Firstly, we don't know what or how this REST API behaves, just that we want to use it in the end.
We don't dive into writing X amount of lines of code in Python scripts composing of methods, classes, imports and such.

Let's see how it works, via a nice tool interpreted languages have: the interactive shell

```python
Python 3.6.2 (default, Aug  5 2017, 16:38:58) 
[GCC 4.2.1 Compatible Apple LLVM 8.1.0 (clang-802.0.42)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```
Let's import the python requests library to communicate with the api

```python
>>> import requests
```
Form a request to endpoint in question:
```python
>>> url = 'https://api.jyleong.github.io/some/endpoint'
>>> r = requests.get(url)
>>> print(r)
```
Get feedback, say we get a 401 error, indicating we need some headers with auth token
try again
```python
>>> url = 'https://api.jyleong.github.io/some/endpoint'
>>> headers = {'authorization': 'Bearer tokenxyz'}
>>> url = 'https://api.jyleong.github.io/some/endpoint'
>>> r = requests.get(url, headers=headers)
>>> print(r)
```
Let's say this returns 200 code with the json response body

See what I did there, I experimented with the api in question to figure out whats wrong. It was my own example, but that is how I would have approached a problem. Done some work to see some feedback, although it was negative, it provided me with some information with how to proceed.

Also I utilized something like the Python interactive shell, so I wouldn't have to write up my code, put it all together and run it just to check the small behaviour of this GET endpoint. Using python's interpreter is but one example. Other examples for different problems could be to run your server locally and test out behaviour when you are developing locally, rather than building, packing and deploying project to test.

You can apply these steps to learning any skills you want really.

### They know when to ask for help
When someone says they did this all by themselves and made it to 'the top', bullshit. No one—and I mean NO ONE—got anywhere alone. You cannot and should not do everything yourself. You are not always the best person for the job, or the “only” person who can do it. Asking for help is a sign of strength, not weakness. Asking for help clears space for you and frees your time and energy. You remember what those last two points were right? Hah, it could also shorten your feedback loop for learning and continuing with your work.

Often, people are quite eager to help you, if they know you need help. Let's think about what you will gain from the ask—a chance to connect, a chance to value a colleague, a chance to get something done faster or better, a chance to optimize your own time and talents.

This is just as important of a skill and quality, not just for an engineer, for any aspect of work. To me also a sign of a persons humility. I hate being around bigots, but I digress... Often we are afraid of letting others know we need help because we believe they would think we aren't capable of doing something or that we appear weak. However we have to reframe this way of thinking.

Each of your colleagues will have their own strengths and weakness. For example, their familiarity with a certain task that they could demonstrate to you, so that you can do said task. The more you get to know about your colleagues and how they work, the more effective you can strive to be. The more effective your team will be.

In the end engineering or software development still requires communication, and asking for help is a crucial part in communication within your team.



