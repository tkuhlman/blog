---
date: 2016-02-12T13:36:07-07:00
tags: [mojo, lxd, development]
title: Mojo Integration Tests with LXD
type: post
---

I have recently finished building an LXD image for doing integration tests of [Mojo](https://mojo.canonical.com).
I did this because I wanted to be able to reliably test the changes to Mojo that I was making. A repeatable,
standard environment that can run set of integration tests fits the bill.
<!--more-->

## Using a Container

There are a few key advantages I see to doing the integration tests in a container image like this:

 - Having a repeatable environment enables automation, sharing of the environment among developers, using
   the environment as a base standard and incremental improvement.
 - The image can be built to a standard, in this case it runs Ubuntu LTS with the latest distributed versions
   of Juju/Mojo and other tooling.
 - Isolation from the primary dev environment allows for easy cleanup, easier testing of various branches and tests
   more easily run in parallel.

## Integration Tests

Integration tests themselves I want running because some tests are just not practical to do via
unit tests. This is especially true for code that interacts with a lot of other programs such as Mojo.

In many cases integration tests bring an real world element unit tests don't. For example the Mojo unit tests
cover Juju interactions decently well using the expected Juju status output. However what if that
expected output changes? For example Juju output could change in a way that is harmless and not
noticed so everyone upgrades Juju, then later Mojo changes but the unit tests are all based on the
older output, integration tests will catch this before sending broken code to production.

On the other hand some tests, ie proper parsing of a manifest file, work better as a unit test. In other
situations it perhaps isn't so clear. Have integration tests as a tool in addition to unit tests gives Mojo
developers another way to validate code before merging.

## More Information

The image can also be used for development of Mojo specs, there is some information on that and more information on using the image in the
image [readme](http://bazaar.launchpad.net/~mojo-maintainers/mojo/trunk/view/head:/contrib/LXD/README.md).
I also made this [screen cast](https://youtu.be/Q8ll7OsTtMk) to introduce how I use the image today. I often watch
these screen casts at double speed and recommend you do for this one also.

Now that the base image is done all the Mojo developers can all incrementally add more tests and I look forward to seeing it expand.
