---
date: 2016-04-16T21:06:14-06:00
tags: [docker, lxd]
title: Containers over VMs
type: post
---

I recently realized it has been over 6 months since I have used a VM on my workstation. Previously I
like many developers used VMs for various development tasks. The change hasn't be in my usage of
cloud based VMs, I continue to do that as needed and appropriate. The change is that I use containers. <!--more-->
I now use a mix of [Docker](https://www.docker.com/) and [LXD](https://linuxcontainers.org/lxd/) for dev and
test environments and everything else I used to frequently use VMs for on my workstation. I even use containers in some
[ways](/systems/desktop_docker/) that I haven't used VMs.

Realizing this change in my behavior is somewhat startling for me, after all VMs represented a paradigm
shift in the industry which certainly affected my workflow years ago. I previously found tools like
[Vagrant](/infrastructure/vagrant/) a very useful part of my workflow. Nevertheless the advantages to
using containers for tasks on my personal workstation have change my workflow.

Containers come with nearly all the workflow advantages that VMs do but also with additional advantages
beyond VMs:

 - Speed of execution - I have various aliases and scripts that launch containerized applications
   and speed of startup and execution is indistinguishable from native apps.
 - Lightweight - Not only are containers much faster than VMs they are light on resource usage so
   much so that you can have many running and not notice it. I actually use signficantly less memory on my
   machine than I did a year ago.
 - Easier to share - Though possible with VMs it is just simply quicker and easier to share Docker containers.
 - Quicker and simpler to build - The speed of startup and ease of sharing contribute to it being
   really easy to startup a new container makes some changes and save it off for further use. This allows me
   to nest usages, repeat test cases on different versions, etc.

The net effect is that for many uses containers just have less overhead than VMs but retain the primary advantages
that VMs brought to the industry. There are of course reasons to still use VMs on a personal workstation,
such as not running Linux as a primary OS and so lacking container support natively, doing development on the kernel,
or developing for an OS other than Linux. None of these are relevant for me so containers is the way forward on
my machines.
