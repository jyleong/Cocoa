+++
title = "Workarounds for invoking Lambda"
date = "2018-04-20T21:05:25-07:00"
draft = true

+++

I have been working with some friends/fellow students/colleagues for awhile on personal projects.
At first it was to develop my skills and hangout with a good bunch of people. It has become a positive, productive, healthy hobby of ours.

For a new project we are tinkering on we are playing around with [Serverless Framework](https://serverless.com/). It's a framework/toolkit to deploy, house and operating code made for serverless architectures. It is a useful thing to deploy out some production ready code without much hassle, especially for personal side projects where the code is alot of tinkering and hacking.

Behind serverless, it wraps around AWS Lambda. This is the feature from Amazon to Functions as a Service (FaaS). Therefore, we are actually just using AWS Lambda behind the scenes, the hardwork has been abstracted for us with Serverless

When it comes to software engineering, ahem I mean hacking something together as a personal project, we won't be prepared or have prior knowledge to these new tools. We will also use the tools for specific things that the documentation does not have good instructions for.

For example this thing I had to do with my lambda functions:

Make a restful api that is serverless to start and stop my AWS EC2 Instance.

Little did I know Serverless did not allow me permissions to start and stop EC2 Directly.

Well derp, what did I do? Try try again, make lots of mistakes, spend some sleepless nights over this issue pulling out my hair. Haha.

Turns out my hack/workaround was:
* make an actual lambda function in AWS that had full access to modify EC2 since they were both hosted with my credentials in AWS
* using serverless framework and a python library to interface with AWS called 'boto3', call the lambda functions to invoke my lambda made inside AWS

My serverless.yml config file looked like this:
```
frameworkVersion: ">=1.2.0 <2.0.0"

provider:
  name: aws
  runtime: python3.6
  stage: dev
  memorySize: 128
  versionFunctions: false
  cfLogs: true
  iamRoleStatements:
        - Effect: "Allow"
          Action:
              - lambda:*
              - ec2:*
          Resource: "*"

```

This is not a guide to how to work with EC2, Lambda, AWS or Serverless. This is more of an adventure of a developer who codes personally and how I run into issues and find solutions to my problems. It is to show that solutions aren't always perfect or clean  the first time around. Software development is an iterative process working towards a better solution everytime.

If people would like, I can make guides on certain tools and technologies.