---
date: "2014-11-28T10:46:35-06:00"
title:  "Initial impressions of systemd"
type: "post"
tags:
  - Linux
  - systemd
---

A few years ago I was happy to see the movement away from the complicated and fragile system V style init scripts. This is something
that both Upstart and systemd accomplish well. Additionally the ability to start up services in parallel with more advanced ordering is quite useful.
Though in many ways I can work with either system I am glad that the Linux community is converging on just one option, I think this standardization
is a large benefit for the community as a whole.

I am switching from Upstart to systemd as the distros I use do so and given that I have mostly worked with Debian based systems lately my experience with
systemd is still rather basic but there are two things that I like about it compared to Upstart.

- The single command for everything, systemctl. Having one command makes it easier to explore the full functionality of systemd and also
  makes it so much easier to remember what tool to use for any particular daemon. The last few lines of logs on status is a nice feature also.
- The 'After=' option in systemd service files. In particular as pointed out in this [blog post](http://0pointer.de/blog/projects/systemd-for-admins-3.html)
  this option only affects ordering if both services are going to be started. This is especially helpful for my systems as often in our dev
  environment we stack all the services on one machine and so the startup order is important. On our full test and production clusters services are spread
  on different machines and the start up order is out of the hands of systemd. It is nice in both cases to use the same service definition and just have
  it work appropriately.

There are numerous other features of systemd which I am just beginning to discover in my usage. For instance I was excited to discover the simplicity of turning
on a serial console. I perhaps will find time explore the control group integration and some other security features such as private /tmp soon. I definitely need
to further investigate journald and how it can be useful as a core part of the systems I use. The great news here is that the man pages and the related documentation
around systemd is excellent. Simply exploring the documentation links on the projects [main page](http://www.freedesktop.org/wiki/Software/systemd/) have provided
me with a quick start and more in depth material than I have time to explore.
