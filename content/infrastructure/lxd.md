---
date: 2015-10-14T11:04:37-06:00
tags: [docker, lxd]
title: Initial impressions of lxd
type: post
---

In the last couple of weeks I have been taking a bit of time here and there to explore [LXD](http://www.ubuntu.com/cloud/tools/lxd).
LXD is a tool for managing system containers. As both LXD and Docker deal with containers in many ways there is quite a
bit of overlap but LXD is aiming for full isolated system containers where Docker is more focused on application containers. You can even run
Docker within an LXD image. I find it helpful to think of LXD as a replacement for virtual machines.
<!--more-->

### LXD Features

LXD is built upon [LXC](https://linuxcontainers.org/) which is impressively mature when compared to most of the container ecosystem. There are some
lacking features with LXC as pointed out at [by the project lead](https://www.stgraber.org/2015/04/21/lxd-getting-started/).
LXC could benefit with some things that Docker brought to the table and LXD fills these gaps:

- Container images and an easy way to share them.
- Simpler, easier to approach tools.

In addition to these features LXD is bringing to the table some new things, specifically:

- Secure containers by default.
- Checkpoint/restore support to enable live migration

### What about Docker
Thinking of LXD as a VM helps to clarify where it fits in a system workflow, it isn't the entire picture. I have often thought of Docker containers
as a new style of highly specialized VMs. In fact many of the use cases where I have used Docker I have treated my container in many ways like a VM.
Though Docker is more focused on application containers and LXD on system containers there remains overlap between the two.

Simple tools and most importantly easy to share and build upon images are primary reasons Docker became so popular.
This is what makes it easy to get started with Docker. Do you want to run Jenkins? With one command you can download the official image and have it running.
The ease of sharing images and building upon others is also what enables the emerging container devops deployment model. This model brings enough
advantages that has the potential to change how devops is done in the next few years.

LXD is making some good progress with image sharing but it doesn't go far enough to compete with Docker in this regard. Most notably the lack of a
public official repo with images you can build upon is missing from LXD.

Though LXC is quite mature Docker has the lead as an app that wraps (or formerly wraps) LXC. With LXD it is still cumbersome to do some tasks, for
example a volume mount. Additionally there are little annoyances like the terminal columns/rows being set wrong when running bash in a container.
I expect much of this to be fixed as things mature but it is a sign that this is a new project.

LXD does implement better default security in unprivileged containers, a nice feature to have. However Docker also continues to
improve in this area. LXD is also implementing live migration which I believe Docker is further behind on. This mostly seems to fit with the general
philosophy of a VM like system container versus application container.

### App container or System container
In order to really think about when to use LXD and when to use Docker and how they overlap you have to explore the differences and use cases for
app container versus system containers. System containers act more like a VM with multiple processes and an init daemon. Applications containers
are leaner with no init and most often only a single service running though they aren't limited to a single process.

Today most deployed applications aren't in any container and many companies are working on fundamentals of devops not implementing a container
based devops workflow. This migration is one area where system containers really shine, they are much easier to move an existing workflow and
applications to. In an application container without init suddenly something as basic as how you start your application changes.

On the other hand a large porting of the advantages with containers are how they enable easier micro-services management and a new workflow. The
ability to not care how an image is built and to easily test the exact image that is deployed then to manage as a flexible pod with a tool like Kubernetes
are all advantages enabled by application containers.

There are some use cases that won't move to the new workflow. For example I don't think I will ever again use a vm for development,
using a container brings the superiority of containers as well retaining the VM advantages of having a repeatable isolated dev environment. Given
the variety of tools used in development this is much better to do in a system container rather than an app container.

Having all of the mature system tools at your disposal is one argument in favor of system containers. Many times saving devops time by having the
standard tools available beats the efficiency gain of a smaller image. In some cases I can easily see the initial move to containers be to a system
container with all the standard tools and later a move to a more tightly built application container.

Regarding tooling it seems to me that container management tools should support both. They may have
their initial leanings simply as a way to focus development but ultimately I think system or app container is something to be decided by the use case
not by the tooling.
