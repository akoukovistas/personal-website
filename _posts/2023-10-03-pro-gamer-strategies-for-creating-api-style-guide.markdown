---
layout: post
title:  "Pro gamer strategies for creating an API style guide."
date:   2023-10-03
categories: API Design DevEx
---

As mentioned in my previous posts, having a standard to work towards/with is very important. Today, we will review some key points enabling you to create such a standard. As with everything, we start with a pen, paper, and a drawing board. Tooling is vital to maintain the standard and enable teams to work more efficiently. Still, it’s more important to establish a standard and understand its reasons before jumping into tooling.

There are three key points you need to keep in mind before you set out on your standardization adventure:

1. **You are creating a product API, not a case study of best practices.** Theory often does not care about standard conventions; your audience is human developers, not a book.
2. **Consistency is more important than an over-optimized API.** Be realistic about your expectations and ability to refactor.
3. **Developers are very opinionated.** It’s unlikely all of them will agree on a standard. Try and realize what’s best for your product and its use cases and go with that.

Whether you’re doing an API-first approach or standardizing an existing set of APIs, it is imperative to remember that an API is not simply the URL and the responses. Your API is the URL, the paths, the parameters, your models, the model hierarchy, the return types, the requests, the responses, the authentication, the headers, the language used, the error messages, the filtering, the pagination, even your documentation; in short, as with any piece of software, you are responsible for every single visual and operational detail of your API.

One of the first things you must establish is what the API is doing. For who? How? What are the primary use cases and interactions for a given type of user? Are you serving content for a marketing site? Is the post content your main “product”? Are you serving videos? Is it an API meant to be integrated within CI/CD pipelines? What’s the primary language? Only you can answer that.

Once you have realized the purpose of your API, then you can start making decisions about the design of the API based on that. There are many subcategories you can focus on and many intricacies to standardize, but this is the way I have been thinking about my API design. My style guide has seven categories: Design, Security, Developer Experience, Authentication, Type-specific Standards, Documentation, and a Strategy Playbook.

Let’s go through each category briefly so I can explain why I categorize my style guide like that and what sorts of things could fall into each category. As you can see, I value things that could easily be within “design” a lot, so they are getting their own categories. You don’t have to go to that length.

### Design

Under design, I include anything related to the API’s looks and feels. Starting with a recap of your mission statement for the API is beneficial. Make sure it is clear what kinds of APIs the style guide is meant to be used with. Is it REST only? Set standards about the language used, the path structure, the naming conventions, how errors are presented to the user, how the requests and responses should look, decide on a pagination type, and document some key behaviors.

The main point you’re trying to convey under design is: “This is how our API looks and feels. If you are using our API, expect to find these traits. If you are building our API, you must comply with this.”

### Security

Given how disastrous security breaches can be, especially with high-profile services, security should be standalone within the guide. If you have DevSecOps in your organization, perfect, work with them; if you don’t, good luck. OWASP’s API Security is a good starting point, but you should probably copy the key points and add any additional ones suitable for your software.

For example, I always add “NO SECURITY THROUGH OBSCURITY.” Many within the tech industry seem to forget that simply making something junky on purpose doesn’t mean you’re more secure; it might take longer until someone finds out. Another point you might want to add is how you handle sensitive information within logs, responses, and debugging assistance.

### Developer Experience

While DevEx is a significant part of your design, I put anything that makes the API less misanthropic under this section. Instead of “cluttering” the design with what we aim to achieve with the design decisions, I separate key elements and elaborate on them. We want someone reading this section to understand what we are doing to make our API nicer and more accessible. You cannot easily translate this section into some tooling configuration, so it’s an excellent chance to engage with your developers.

Set the scene and discuss aspects a developer might need to consider initially. Help them design with the user in mind. Are we supporting events and webhooks? Should our APIs have a retry mechanism? How do we communicate this, and why? How do we help users experiencing errors with the API?

### Authentication

One thing I’ve encountered while working with APIs, either as a designer or integrator, is that unless you are very strict with your authentication, people will get cute and end up in a perpetual fail state when nothing works as intended.

From the beginning, decide on the types of authentication you are supporting and outline precisely how the authentication flow works. Talk about your authentication scopes and access management. Your authentication has to be consistent. It’s more than acceptable to support multiple authentication types simultaneously, but you should do it consciously and always offer one consistent one.

### Type-specific Standards

This section is more or less self-explanatory, but this is where you set your standards for specific information types. For example, all DateTime fields will follow X format, all of our IDs are strings, and Potato types will only be linked by reference to a PotatoType and never referred to by their name.

Luckily, this is also one of the most straightforward sections of the style guide to check automatically with a linter.

### Documentation

I don’t want to contribute further to the ever-living meme that developers hate documentation. However, it is sad that many people still don’t understand the value of good documentation. You can read my previous post about why documentation is important.

This section aims to inform the developer working on the API about acceptable documentation and the minimum documentation requirements before their API is production-ready. Ultimately, allow them to contribute to the product’s documentation.

Usually, I set a hard requirement for developers to provide an OpenAPI JSON and a set of steps to authenticate with the service for each API developed. In addition, I give information on how they can contribute to the documentation with links, resources, contacts, and examples. Linking to the documentation itself here is also a good idea.

### Strategy Playbook

This section is where you can outline things affecting the API that are not parts of the API itself. It is where your deprecation strategy, release management practices, review processes, and other strategic operations can exist. Realistically, this is only a requirement in larger projects and organizations, and often, those will already have established processes elsewhere or require more granularity as to the type of strategy. However, having them in some shape or form is imperative, and the developers must be aware of them.

There are many intricacies and moving parts to consider before adopting any standards for your organization. Review your APIs, products, and product plans before officially adopting anything. While a small subset of people can lead this standardization project, make it open to a broad audience within the organization. Collecting feedback and producing something organic that your developers, product owners, and other stakeholders are happy with is essential. It doesn’t mean you should listen to and humor every opinion, but people often want to be included, and they want to feel valued. Consider that there are many high-skilled individuals within an organization, and their input can make your plan even better.

In one of the following posts, I will discuss how to perform API reviews and give some tips that helped me evangelize the importance of a good DevEx while working with multiple product teams of various compositions and tech stacks.

Thanks for reading, and as always, I look forward to your comments and feedback! And if you would like to discuss your organization’s API standardization, my DMs are always open ;)
