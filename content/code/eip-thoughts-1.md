+++
title = "Wrapping my head around Enterprise Integration Patterns"
date = "2018-12-30T12:13:33-08:00"
draft = false

+++

Currently I am slowly chugging away at reading about [enterprise integration patterns](https://github.com/vaquarkhan/vaquarkhan/blob/master/integration%20design%20pattern/Addison%20Wesley%20-%20Enterprise%20Integration%20Patterns%20-%20Designing%2C%20Building%20And%20Deploying%20Messaging%20Solutions%20-%20With%20Notes.pdf). Working as a developer primarily at a company focused on making business applications, my cool problems I am exposed to are real time streaming messages, from multiple sources, sometimes not within our control. It is important to know the best industry practices to integrate them smoothly into our applications and infrastructure.

When someone is going to learn something, they practice it, in bite size pieces then work there way up. Software Developers, hobby coders, programmers, etc can work on small problems, hobby projects to gain their skills... essentially get more comfortable coding and making things. Well, when it comes to EIP in practice, I find it difficult to practice designing large systems as a side project. Take away the fact that it sounds daunting to design something alone, without guidance... in our everyday life outside of work, when would we design something so big as a hobby project that would require us to start developing/coding in a way to put the patterns into action?

At the moment, I can only think of reading into each message pattern carefully and seeing if there is a smaller scale design pattern equivalent. Then write that out with yoru toolset of choice using abstract/random methods and classes besides starting off with the idea of making an application that will go live. 

One example is the Observer (publish/subscriber) Behavioural Pattern. It is a pattern where we have senders of messages but do not explicitly send them to the receivers. Instead, subscribers only listen to the topics that they are interested in. In EIP that are coincidentally called the same thing. Another example where the small scale pattern is named differently to the EIP is the Client-Server Architecture, you can one shared server with multiple clients. The server provides a variety of services and requests to the clients, the server is up and listens to the clients requests. A similar idea in EIP is the shared database concept. 

Well, we have to start with what we know and start small right? 