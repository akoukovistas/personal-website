---
layout: post
title:  "I don't trust software without versions"
date:   2025-06-16
categories: CustomerSuccess DevEx ProductDevelopment API
image: /assets/images/versions-blog.jpg
---

At [DevConfCZ](https://pretalx.devconf.info/devconf-cz-2025/talk/UTGBCF/), I attended a talk by Maja Massarini about the [Packit team's](https://packit.dev/) struggles with version 1.0 breaking changes. When she asked for feedback, one thought immediately came to mind: I don’t trust software without versions.

This might be my bias as mainly an API guy, but at the same time, isn't a configuration tool that triggers a process on a remote machine an API too? I think we've gotten too used to "API" meaning only REST and JSON — and forgotten that those same lessons apply to other types of interfaces too.

## Why Versions Matter

I feel like I've been hammering this point lately, but let's go quickly over a few reasons proper versioning matters.

### 1. Versions create stability
As a customer-integrator, I'm looking to use your product in my solution to solve a specific problem, shift some of the maintenance burden off my plate, and have less headaches overall. I need to be able to reliably plan for how long I will be able to use a specific version of your product, and also be able to plan, well in advance, when I would need to upgrade.

I have worked with an investment product which only offered the latest version of the software via an API, and had mandatory weekly updates. Having a critical integration break every week is a nightmare. Obviously, this is just one extreme example, but it highlights how destructive you can be, even without being an incompetent ninja developer.

### 2. They add context

Context is extremely important and versioning is a powerful way to provide it. This helps everyone in your org too! Your support team handling requests will benefit from it, developers applying patches and releasing updates will appreciate it, and even POs and other business stakeholders will be able to plan around versions.

### 3. They make you a better dev

Being "forced" to think about what you're releasing adds a lot of structure and context to your work and gets you closer to that ideal "we're putting a man on the moon" team alignment scenario without having to rely on spoon-fed company mantras.

With clearly defined versions, it's way easier to create proper deprecation strategies, version migration tools, migration guides and enable a smooth transition for both you and your users.

## Things people often get wrong about versions

Since I'm not advocating for "1984 software versions edition", or extreme bureaucracy, let me clarify some points while going over common pitfalls. In no specific order:

### 1. Your API version does not have to match your product version.

I can already hear you shouting at your screen "THERE'S NO PRODUCT WITHOUT A VERSION", and I would agree, that's mostly true. However, a product can often be a combination of different services, APIs, visual interfaces, etc working together. There's no point in syncing your SDK, REST API, portal and UI versions. I'm sure there are edge cases where everything needs to sync, but what benefit do you get out of bumping your API version just because you deployed a button redesign?

You can reasonably have v5.0.0 of your web application, v3.0.0 of your iOS app, v3.0.5 for Android, all using the v2.1.51 of your REST API, a GraphQL API which is on version 1.15.0 and offering an SDK for integrators which is currently on version 4.1.15.

### 2. Your versions have to mean something.

There's a few good standards on versioning, [pick one](https://semver.org/) and follow it. Have rules for it. I have been in too many repositories where the versions were tagged something like `initial_version`, `v1_staging`, `1.1.5`, `2.1.5`, `test_for_george`. Keep it consistent and meaningful, define what your notation means.

### 3. Major version changes should only happen when major and/or breaking changes get introduced.

As mentioned above, your versions have to mean something. Your actual strategy can vary, but for the love of Terry A. Davis, don’t bump to v3.0.0 just because you added a single route.

### 4. You don't have to support every version you release until the end of time.

Just because you're having clearly defined versions, it doesn't mean they all need to exist and be supported. You might have some crossover where an older and newer version of an API might exist at the same time (usually due to your deprecation strategy), but don't make it a perpetual thing unless there's a reason. It's completely fine to say that versions will only be supported for 3 years.

### 5. Deprecating a version is a significant event. People need to know well in advance.

In an ideal world, someone integrates with your product then forgets about it, aside from the odd minor version update, or other small piece of work. If you're going to deprecate something, or introduce breaking changes, make sure you notify your users well in advance.

In a company I worked at, we had to notify customers 2 years in advance before deprecating something. This roughly worked out to be something along these lines:
1. Announce that feature X will be deprecated in 2 years with release `x.y.z`.
2. Immediately introduce a notice that this is to be deprecated in the docs.
3. A year later, add deprecation warnings to the service itself.
4. Around this point, release migration guides and any necessary tools.
5. 6-8 months before the deprecation date, review the analytics and determine who is still using the (soon to be) deprecated feature. Reach out to them and support them.
6. Closer to the end of support date, release messages with stronger wording.
7. Notify your support teams, "soft-deprecate" the feature if possible, and keep an eye on adoption.
8. ???
9. Profit!


## So why don't I trust software without versions?

- They show a lack of care.
- I already have enough junk to deal with in my own system - I don’t need yours too.
- I’d rather work on something meaningful than scramble to fix things you broke.
- Debugging is way harder without version tags to narrow down the issue.

Versioning isn’t just for show. It’s a sign of care, stability, and professionalism — and it makes life easier for everyone involved.

### Are there exceptions?

Of course, not everything fits into a tidy versioning model for one reason or another. 

- I’ll “take the L,” as the kids say when it comes to things like Auth providers and payment gateways. At the same time, I expect them to be organised and professional about their whole SDLC.
- SaaS is a necessary evil and you often don't have a choice. As much as I would love to eliminate SaaS products from my dependencies, I have to be pragmatic about my tooling.
- Whatever Elon Musk buys next. After Twitter, he’s basically running the speedrun of how not to do API versioning - and yet it somehow still works. (Much to the frustration of anyone making a case for best practices.)

What’s your biggest software pet peeve? And how do you handle versioning where you work? I’d love to hear your thoughts.

Thanks for reading!

Please check out some of [my other posts](https://koukovistas.com/blog), or even my [YouTube Channel](https://www.youtube.com/@koukovistas)