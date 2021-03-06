---
date: "2015-03-11T21:36:35-06:00"
title: "Docker, what use it?"
type: "post"
tags:
  - docker
---

Anyone in the industry who hasn't yet read multiple blog posts on [Docker](https://www.docker.com/) is living under a rock. There is a lot of hype about Docker
and its potential. I also revel in the long term vision for containers and their potential impact on the industry. However until I have an awesome
infrastructure where I can deploy images into production my practical mindset drives me to cut through the hype and ask what
use is Docker for my work today?

As I have explored Docker here are the uses for it that I have encountered that bring practical value to my day to day work.
<!--more-->
## Development Environments
When it comes to starting up a quick environment to test out something you may or may not keep around, VMs are an undisputed improvement over bare metal and
containers are step above VMs. It is so quick and seamless to get a dedicated container for whatever the current need is I find myself doing more and more
work this way.

I heavily use [Vagrant](https://github.com/stackforge/monasca-vagrant) for my team's primary development environment. Vagrant is an awesome tool that I could
write many dedicated posts about. Why not Docker? There are a number of reasons we still Vagrant for development over Docker including that it is still
better able to replicate a real deploy of our software as well as simple momentum.

Beyond the momentum of existing solutions, the biggest problem with Docker for complex dev environments today is that many tools are built assuming a
different environment. Some tools want to setup a firewall or change sysctl settings and so end up having some difficulties with containers.
Despite these annoyances, as tools for containers improve I expect more and more the balance tipping in favor of Docker.
The quick startup, lighter resource utilization, easy versioning and other advantages of Docker containers are quite compelling especially for all new environments.

## Testing
The easy versioning and quick startup of containers make them ideal for testing. This is a key part of the primary vision of Docker, an image built
by development can be easily tested. Even with no production environment ready for Docker, containers have been useful for testing in a few scenarios
I have encountered.

### Integration Tests
It seems you always have more scenarios to test then available resources to test them on. Containers allow you to easily switch between different
configurations and software versions or to even have multiple running at one time. This is obtainable
using VMs also but it is much quicker to build, run and switch scenarios with containers.

One of my team members went further and integrated some pre-built containers into the standard tests run during the build. Better than trying to mock out
the entire database and various REST API services used by the code, he was able to run them in Docker containers with a known set of data. Not only is this easier
to setup then mocking out these interfaces it results in much more realistic tests.

### Load testing
When you want to run many clients but only have a few machines to do so for many applications your options are quite limited.
You can spin up bunches of machines with your favorite cloud provider, you can write a load test tool that simulates clients or attempt to mangle code, configuration
and startup scripts such that many client instances run. Quicker and easier than all of those options is to just start up a few hundred clients each running in a
new Docker container.

## Demos
The last practical use for Docker that comes to mind is one I am actively working on, a demo environment. A single command to start, a single download and you
have a complex system up and running that anyone can explore. VMs can fulfill this need also but Docker images are smaller and quicker to run as well as simpler to build
and update. This means the key quality of a demo, barrier to entry, is lower.
