---
date: 2016-01-16T20:44:55-07:00
tags: [development]
title: Development Best Practices for Systems Administrators
type: post
---

The days where systems administrators do no development are gone. Just as developers
leverage cloud infrastructure and tooling to deploy services, sysadmins develop code to automate
their infrastructure and to fill the feature gaps that they are uniquely positioned to see.
<!--more-->
Though best development practices are the same for both sysadmins and devs, some are more
natural to one group or another. The heart of devops is operators and developers coming together and in many ways this
post is really about what sysadmins can learn from developers. Here are some best practices I think come less naturally to operators.

## Best Practices

### Simplify
**Interface**

Make your project simple to use. Sysadmins are badasses at the CLI and forget not everyone is. Also make sure to keep the interface consistent.

**Standardize**

Choose sane defaults, don't be afraid to limit choice and flexibility so the code steers people toward good and/or standard practices.
Choice can be good at times but more often than not is a bit stifling. One difference between a usable project and a great one is often in appropriate
defaults and simplicity of configuration.

**Code Structure**

Turns out the basics of code are easy, children can grasp the concepts of branches and loops. Most code is dealing with the complexity
of having so many branches and loops. That is why the common code constructs (classes, inheritance, types/interfaces) exist.
Layers of abstraction, separation of concern and encapsulation are amount the keys to good complexity management. The difference between
good design and bad is how well the complexity management is done.

There are many code techniques to deal with complexity and this is a great example of where sysadmins can learn a lot from devs. I'll not delve
into actual techniques but rather here are some principles to keep in mind while coding:

- [Reducing code complexity](http://sysadvent.blogspot.com/2015/12/day-22-simplicity-in-complex-systems.html) by thinking about where the code can shrink
  or hide the complexity. Shrink complexity by building code constructs that break the complexity up. Hide it by building complexity into
  methods or objects, hiding it from the rest of the system.
- Keep your code organized. One principle to avoid sprawling code is, [YAGNI](http://martinfowler.com/bliki/Yagni.html), only write to what you
  actually need now. Sysadmins run systems and so have great insight into what is needed making this best practice relatively easy. However there
  is one caution with YAGNI. To quote Martin Fowler "Yagni only applies to capabilities built into the software to support a presumptive feature, it does
  not apply to effort to make the software easier to modify." In short YAGNI is not an excuse for unorganized code. Organize your code and revisit the
  organization to keep it organized as it grows and more features are added.

### Document

Document your code! Maybe this is one both devs and sysadmins could do better at.

Document as you are writing the code. After having just written the code you know what it does and there is no better time to clearly express that.
The code's lifecycle is just beginning, the project will be used and modified by yourself and others and good documentation helps immensely with
these further steps.

The closer to the code the documentation is the better. It is most likely to stay up date if the documentation is close to the code as well as being the
easiest to find. Also being close to the code gives you an automatic context allowing the documentation to be more succinct.
Most languages have built-in tools for documenting well and publishing the docs in a standard way, use these tools.

In addition to helping with the further lifecycle of your project the act of documenting is a tool for discovering unnecessarily complexity.
When documenting you have to force yourself to think like someone unfamiliar with the project which is an important mindset to adopt periodically.
This is especially true when writing the overview section of your docs which links project components together into a whole that users will interact with.
I often find documenting reveals big wins where just a bit more code results in a large improvements.

### Test

**Automated Testing**

I find sysadmins often test manually really well but don't automate the testing as well. The manual testing is great that first
time but the automated testing provides repeatability. The repeatability is key for proving functionality and for any future changes, which
for most projects are bound to happen.

Automated testing does have its limits, in particular unit testing is limited in how useful it can be for code that interacts with other
systems. This is the type of code sysadmins write most often. It is difficult and fragile to mock out code that does network I/O, a system call, db I/O and
more network I/O. This doesn't mean skip automated tests but rather ensure the use cases are covered with
automated integration tests. A great use of containers is to create pre-built test environments for automate integration testing.

**Real World Usage**

Use and run your own code in a real environment. It is through running code in a real environment that you discover the true
problems that need fixing. Indeed the motivation for much of the code sysadmins write comes from running real environments. Even though this seems
obvious to sysadmins it is a key best practices that is so important it needs to be mentioned.
