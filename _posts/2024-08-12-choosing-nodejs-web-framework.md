---
layout: post
title: "Choosing Node.js Web Framework"
date: 2024-08-12 20:00:00 +0300
categories: nodejs express nest fastify webframework
author: Anas Najaa
---

![Choosing Node.js Web Framework]({{site.cdn_url}}/blog/2024/08/0adf9d7c-8416-4742-a57e-c3b1c038689e.png)

# Frame of reference

During my journey as a developer, I've built many web applications using multiple Node.js frameworks. At the beginning, I was switching between frameworks frequently, picking a different framework for each project. It was a way to test the water and to see if the framework  was a goof fit for my coding style. In addition, one of my main factors I wanted to see how comfortable was it expand on it as the project grows. In this post, I would like to share some of my experience with 3 of these web frameworks.

# Does it matter?

Keep in mind that when you find a suitable web framework, you have to stick to it and use it to build everything. This is the only way for you to reap the benefits of the framework. It is ok in the beginning to keep switching and to try different ones, but there is time for exploration and there is time for exploitation. If you are a web developer who cares about deadlines, predictability, familiarity and keeping your stress levels under control, this is the correct line of thinking you should follow. 

# What if I can't chose?

If you are not a freelancer working independently, chances are that the decision of the web framework will be made for you beforehand by the technical lead. In this case, you have to adapt your coding style to match whatever the team is using. This article will still be useful for you to understand what value each framework brings to the table. 

## Hasty developers joining a team, take heed
At first, it might be tempting to question the design choices made by the technical lead, but you have to force yourself to follow the rules and go through the motion to progress smoothly within the team. When you fully understand the code base and why everything was built in a certain way, then you'll be able to make positive changes if needed.

# The top 3

I focused on 3 frameworks that I've used personally. Each framework provides a different value proposition, so this way you can decide which one is the best fit for your use case. I compared the frameworks in term of advantages, disadvantages and included a sample code of the most basic usage. I encourage any Node.js developer to build at least one project from A to Z with each one of these frameworks before deciding on the proffered framework.

**Note:** Please remember that as you mature and grow as a web developer, your understanding of the inner workings of Node.js, web servers, web protocols, networks and the web in general will grow. This will have an impact on your framework choice and you might develop a taste for a different framework, which is ok. Just keep in mind that it is a balancing act and in the end, they are just _tools_.

![Express.js]({{site.cdn_url}}/blog/2024/08/17f5303e-8fac-4db3-8726-1ad4d9fe740f.png)

## **[Express.js](https://github.com/expressjs/express) (64k stars)**

It is easily described as framework that doesn't get into your way. Extreme flexibility and ease of use, but you might get lost if you don't shape your project correctly.

### **Advantages:**

-   **Popularity:** Express.js is the most widely used Node.js framework, making it familiar to almost every Node.js developer.
-   **Vast Ecosystem:** It boasts a massive collection of extensions and middleware, enabling developers to easily expand its capabilities.
-   **Ease of Use:** Express.js is straightforward to learn and implement, with abundant community resources, including articles and video tutorials.

### **Cons:**

-   **Limited Scope:** Express.js only covers basic application needs, functioning primarily as a web server that handles app functions per URL. This leaves many aspects of application development for the developer to implement.
-   **A Little dated:** One of the negatives about Express is that it is not frequently updated, which might lead to performance and security red flags.

### **Sample Code:**

```javascript
const express = require("express");
const app = express();

app.get("/", (req, res) => {
	res.send("Hello World!");
});

app.listen(3000, () => {
	console.log("Server is running on port 3000");
});
```


![Fastify]({{site.cdn_url}}/blog/2024/08/4c074df3-c352-40de-bf83-0a02757414d1.png)

## **[Fastify](https://github.com/fastify/fastify) (31k stars)**
The underdog of the Node.js web frameworks. Fastify is considered one of the [fastest](https://fastify.dev/benchmarks/) Node.js frameworks out there. It provides a good middle ground between flexibility, simplicity and good developer experience. 

### **Advantages:**

-   **Simplicity:** Fastify is a lightweight and straightforward framework, closely adhering to Node.js and JavaScript standards.
-   **Shallow Learning Curve:** It's relatively easy to pick up and use, especially for teams already familiar with Node.js.
-   **Plugins:** While not as feature-rich as Nest.js, Fastify's official plugins cover many application needs effectively.

### **Cons:**

-   **Less Popular:** Being relatively new, Fastify is not as widely adopted as Express.js or Nest.js.
-   **Smaller Ecosystem:** Its ecosystem, while growing, is not as extensive as that of Express.js or Nest.js.

### **Sample Code:**

```javascript
const fastify = require("fastify")({ logger: true });

fastify.get("/", async (request, reply) => {
	return { hello: "world" };
});

fastify.listen(3000, (err) => {
	if (err) throw err;
	console.log("Server listening on port 3000");
});
```

![Nest.js]({{site.cdn_url}}/blog/2024/08/37c914e7-5321-406c-b403-1da163c01e4c.png)

## **[Nest.js](https://github.com/nestjs/nest) (66k stars)**
I like to describe Nest.js as the .NET framework of Node. Nest.js leverages TypeScript and OOP principles and has a modular architecture with strong support for dependency injection, which an amazing feature for large codebase. Nest.js is also Object-Oriented and relies on MVC design pattern which works very well for large teams.

### **Advantages:**

-   **Feature-Rich:** Nest.js offers more built-in features than any other framework, covering various application needs such as message queues and scheduled jobs.
-   **Popularity:** The framework enjoys high popularity and has a vibrant community.
-   **OOP:** It supports Object-Oriented Programming (OOP), which is beneficial for teams accustomed to this design style.
-   **Documentation:** Nest.js is well-documented, with a robust and active community ensuring continuous maintenance.


### **Cons:**

-   **Complexity:** The use of high-level abstractions can obscure standard Node.js conventions, leading to increased complexity.
-   **Learning Curve:** The framework introduces unique concepts like interceptors, guards, and modules, which require time to master.
-   **Highly Opinionated:** Nest.js has strong conventions, which may restrict flexibility in certain scenarios.

### **Sample Code:**

```typescript
import { Controller, Get } from "@nestjs/common";

@Controller("users")
export class UserController {
	@Get()
	findAll(): string {
		return "Hello World";
	}
}
```


## **Final thoughts**

-   **Choose Express.js** when you have an experienced architect who can manage the fine details of the project. 
-   **Choose Fastify** when your application consists of moderately sized components or microservices, and your team has strong JavaScript and Node.js expertise. Fastify is ideal for projects where adherence to Node.js standards and simplicity is crucial.
-   **Choose Nest.js** if you prefer to work in an OOP style, especially if your team has a solid background in Java or .NET or other strongly typed OOP languages. Nest.js is suitable for large monolithic applications that cannot be easily broken into autonomous components. It’s also a good choice when minimizing decision-making overhead and rapid initial delivery are priorities.
