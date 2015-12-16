---
date: 2015-12-12T20:43:55-07:00
tags: [development]
title: Development Best Practices for Systems Administrators
type: post
draft: true
---

The days where systems administrators can avoid development are long gone. Just as developers
leverage cloud infrastructure and tooling to deploy services, sys admins develop code to automate
their infrastructure and to fill the gaps that they are uniquely positioned to see.
<!--more-->
The heart of devops is operators and developers coming together as their roles now overlap. In that vein this
post is really about what Sys Admins can learn from developers, really about what I am learning from developers.
The best development practices are really the same for both sys admins and devs, some just come more
naturally to one group or another, so here are some best practices I think come less naturally to operators.

## Best Practices

- Simplify
  - Make it simple to use. Sysadmins are badasses at the CLI and forget not everyone is.
  - Standardize - Choose sane defaults, don't be afraid to limit choice and flexibility so the code steers people towards good practices, or at least standard practices.
  - YAGNI - reference - http://martinfowler.com/bliki/Yagni.html
    - In particular this quote "Yagni only applies to capabilities built into the software to support a presumptive feature, it does not apply to effort to make the software easier to modify."
- good separation of concern and good code structure.
  - Turns out the basics of code are easy. 5 year olds can grasp the concepts of branches and loops, most of code is dealing with the complexity
    of having a lot of branches and loops. That is why the common code constructs (classes, inheritance, types/interfaces) exist.
  Techniques like layers of abstraction and encapsulation are key to good complexity management. The difference between
  good system design and bad is often how well the complexity management is done.
- Better automated testing. Devs need to do better testing in general I find sysadmins test scripts
  manually really well but don't automate the testing as well. The manual testing is great that first
  time but the automated testing really helps for any future edits. Code is alive there will be future work done on any sufficiently sized chunk of code.
  - Repeatability is the name of the game hear.
  - automating tests force you think about how your code is used and organized often leading to a better result.
  - Automated testing does have its limits, in particular unit testing is limited in how useful it can be especially for code that interacts with other
    systems a lot. This is the type of code sysadmins write most often. It is so difficult and fragile to mock out code that does network, I/O, db I/O and
    more network I/O that often it isn't worth the effort. This doesn't mean don't automate the tests but rather make sure the use cases are covered with
    automated integration tests. I am big fan of using containers with some pre-built test environments to more easily automate integration testing.
- Document it. Maybe this is one both devs and sys admins could do better at. When you just wrote it you know what it does but everyone appreciates good
  documentation, ideally built-in. The closer to the code the better as it is the most likely to stay up to date as things evolve and is the easiest for
  users to find.

Finally one best practice that does come naturally to sysadmins but is critical is to use and run your own code in a real environment.
The importance of this could be a post in and of itself, perhaps someday I will write that. This is one enormous advantage sys admins have
over devs who haven't begun to embrace aspects of operations and only run the code in their dev environmet. It is the reason for much of the
code sysadmins write, as by running things you discover the true problems that need fixing. For all those reasons it is a best practice to hold onto.
