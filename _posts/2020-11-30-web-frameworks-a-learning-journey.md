---
layout: post
title: "Web Frameworks - A Learning Journey"
categories: technology development
author: Anas Najaa
---

![Web Frameworks - A Learning Journey]({{site.cdn_url}}/blog/2024/08/c1f071d7-88f2-4a2e-912d-6ac82233847b.png)

If you are new to programming and interested in web development, you'll most likely stumble upon the term framework. As you start delving into the frontend or backend development paths, you'll be tempted to try out one or more of those web frameworks that promise to simplify your development flow and increase your productivity. As tempting as it might be, you should probably skip them in the beginning. In this post, I'll discuss when should you start considering using frameworks and what to keep in mind when picking one.

# What is a framework?

To put it simply, a framework is a tool that is designed to make your development experience easier by abstracting some of the complex logic, providing helper methods and laying out distinct flow that if followed would yield a greater productivity and easier code maintenance on the long term. They can be opinionated (tells you exactly how to do things and what to avoid when using them) or unopinionated (leaves you some room to apply your own flow that suit you).

# What are the types of frameworks available for the web?

There are mainly two types of frameworks that span across the web development stack, frontend and backend. Frontend frameworks deal with whatever is presented to the end user such as a website or an Application. While a backend framework is meant to be hidden from the end user and runs on some form of server, connects to a database and serves requests to clients.

# Why should you avoid them in the beginning?

It is tempting to start with an existing framework and just use it to build your next project right off the bat. But you should take your time learning the underlying logic first.
For example, if you're picking a framework for the frontend, consider learning the fundamentals of HTML/CSS/JavaScript. What is HTML/CSS? How does CSS and HTML work together to shape the page? What's the browser role in the rendering process? How does JavaScript control the frontend and make web requests? What is the DOM? etc... Learning how to build a website with minimal reliance on frameworks and libraries will strengthen your understanding of how the frontend stack works. This will help you debug errors and better understand what is going on behind the scenes when using a framework. Albeit it won't make you as productive as you want to be initially, but this investment will pay off as you progress towards mastering your stack. Learning how to walk before running so to speak.
The backend is no different, there are many questions that you need to answer before relying heavily on frameworks. What are the protocols we use to interact with servers? how requests are made from the client side? What are headers and cookies? how does a server process requests and access the database to retrieve the required data? What is middleware and how does a session or a JSON Web Token work? and many more questions that you need to investigate before jumping in head first into the world of frameworks.

# Reinventing the wheel

You're going to spend a considerable amount of time figuring out how the basic components work and interact with each other. This will get tedious as the project requirements grow and that is ok. This forces you into the mentality of actually needing a tool to solve your problem instead of using one just for the sake of it. When you reach that level of verbosity, you should start first by pulling in third party libraries to coverup the repetitive and unproductive code that you might end up needing to write yourself. This prevents you from building tools or functions that have been implemented by others numerous amounts of times. It is a crucial to understand that we are not being lazy here but reasonably productive. For example, if we want to implement frontend validation of forms, what is the correct approach? We already know that to validate a form we need to pull input fields inside the form tag, parse the values, validate them against set of conditions, then show errors or warnings for fields with faulty data. However, is it really worth the hassle to implement such a solution yourself? the answer might differ from a project to another and from a developer to another. You decide at what reinventing the wheel looks like to you. In the end, having this mentality onward will ensure that you avoid infesting your project with third party libraries that can make you too reliant on them which makes it difficult to replace them later if they brake or get outdated.

# Either or

I might've made it sound like that you have to pick one, using a framework or not using one at all. That is not true, you can try out a framework and learn the fundamentals at the same time. It might be overwhelming and take more time but it is definitely a style of learning, though a rushed one indeed. In this case, it might be better to pick a lightweight framework that does not hide a lot of the underlying implementations under layers of obscurity. Unopinionated frameworks fit this description and can be a great asset to learning how the stack works.

# Your own web framework

Fast forward two months into the starter project which you were building. You learned a lot about the basic components of the stack and know your way around the code and how things work. You ended up rebuilding some components as you learned the "right" approach to do things, which is part of the learning/growing process. If things break, you can fix them and understand the error messages clearly or at least know what keywords to search for. You pulled in few libraries to save your time, but you are still capable enough that when those libraries break, or degrade with time, you can implement your own workaround or replace them as you abstracted their implementation in some form. When the project structure becomes clear and certain development patterns start to emerge, then you've basically established your own framework! but don't stop here, the learning journey is just beginning.

# Improving by learning from existing projects

We need to point out that learning how to do something on your own does not mean that the way of doing it is right. During your journey, you have to take breaks and get out of your own development loop of code, run, debug, test and release, and jump into a different kind of learning which comes from existing projects. Developers are lucky to have vast number of open-source projects that are of high quality and built by many great developers. Picking a project that is similar to what you are building and learning from it is one of the best ways to acquire knowledge that is applicable to real-world projects. Reading the documentation can be extremely useful as well which will help you understand the thought process that went through implementing the solution. Don't be tempted by large projects, the amount of code might be overwhelming at first, but you will likely have many tools to assist you in your discovery journey such as the ability to search the project and its references. The more you read, the better you get at dissecting the project and understanding its flow. This topic by itself can become too complicated, so I won't go deeper into it, the bottom line is: improve your coding style and learn good coding patterns from senior coders and established project. Try to fork the project and play around with the code, you'll gain tremendous experience from following this approach.

# Too much magic

What we are trying to avoid when picking up a web framework is imitation coding or not understanding what is going on behind the scenes. This will have negative impact on the development experience and can lead to many problems such as failure to understand the flow of the code and having too many unnecessary workarounds.
Take some time to read the documentation of the framework thoroughly. Try to migrate one of your existing projects to the new frameworks to see if it clicks with you or not. And most importantly, learn the ins and outs of the framework. Don't use previous knowledge to implement your old coding patterns from the get go. Take some time to unwind and unlearn the way of working you're used to. This might sound unintuitive at first, but this is the only way to be open minded about the way the new framework works. By giving it a chance, you might stumble upon a new flow that is much more convenient for you.

# Too many frameworks!

At this point you're probably wondering, which of the hundreds of frameworks out-there should I pick for my next project? The answer is and will always be "it depends" which is not a very useful answer but it implies that it is best to avoid using one framework to solve all your problems (if all you have is a hammer...). At any rate, here are some general guidelines that will hopefully assist you in picking your next framework:

-   Ask yourself before starting, do you need a framework at all? Not every project requires a framework.
-   If you are working on a personal project, then there is a chance that picking one of the new and shiny frameworks might be beneficial. You get to learn a new tool and enjoy doing it without the stress of deadlines and the fear of the unknown issues that might emerge as you're learning.
-   If you are planning on starting a serious project, then try to go with a framework that is well established and have a good community and resources behind it. You'll be able to make use of these resources during your development and this in turn will help you meet deadlines and fix bugs as they emerge.
-   Avoid bleeding edge frameworks as much as possible, unless you have a lot of free time on your hands as most of the time such frameworks don't take off and become failed experiments.
-   Check if the framework you're planning to use is opinionated or not. The selection will depend on your coding style and the project you're planning to implement.
-   Boring frameworks are not bad. Learning something new and hip is tempting and exciting, but remember that at some point you need to stop testing around new stuff and start working on the problem you're trying to solve. Picking something familiar to you is a good way to master it and learn its quirks. Some developers never bother learning more than one or two frameworks to begin with, which helps them remain focused and deliver code more quickly and efficiently.

# Roadmaps

One of the effective tools that might guide you through your learning journey overall are roadmaps. Here are two roadmaps for frontend/backend development that will help you understand when is the most suitable time to pick up and invest in learning frameworks: (These are simplified roadmaps of the originals found [here](https://roadmap.sh/frontend) and [here](https://roadmap.sh/backend))

![Backend Development Roadmap](https://najaa-files.s3.me-south-1.amazonaws.com/blog/2024/08/471a1f2a-7903-4f4a-8868-f6da802dfae5.png)
![Frontend Development Roadmap](https://najaa-files.s3.me-south-1.amazonaws.com/blog/2024/08/f2088ab1-8b3a-4b6e-b0e0-aaf4e2c6e832.png)

# It's a learning journey

In the end, it is important to understand that failure during learning is special kind of failure that drives you forward. Don't be discouraged by it, if you fail while you learn new framework or language then you're learning from this failure and not wasting time. The more you learn and fail, the better a developer you'll become. Keep an open mind and keep learning.

# Final Words

New programmers might find it easier to skip basics and jump into using frameworks right from the beginning. This approach might not work for everyone and might help them develop bad practices. Therefore, it is better to start with the fundamentals of the stack you’re learning and work your way upwards, you’ll be surprised of how far you can get without using a framework or relying on one.
