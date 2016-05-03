---
date: 2016-05-02T21:07:28-06:00
tags: [docker, workstation]
title: Docker for Messy Pets - Updates
type: post
---

About 8 months ago I posted about how I run some
[applications in containers](http://backgroundprocess.com/systems/desktop_docker/)
so that they stay nicely contained. I have refined and changed a few things about how I do this
recently and so felt it was time for an update.<!--more--> I do maintain a
[git repo](https://github.com/tkuhlman/containers) that will always have the latest I am using but
here is the summary:

- At some point pulseaudio broke for me, possibly after an OS or Docker upgrade. I didn't track
  down the cause but rather just decided to setup tcp based pulse audio. This is more initial
  setup but should be more stable and is simpler in the startup scripts. Audio works great this
  way and the container can play audio but not run configuration commands like pacmd.
  To setup:
  - Turn on tcp for pulseaudio, in `/etc/pulse/default.pa` add a line like `load-module
    module-native-protocol-tcp` and restart pulseaudio, `pulseaudio -k`.
  - If you are running ufw like me you need a rule like,
    `ufw allow in on docker0 to my-docker-ip proto tcp port 4713` with the appropriate Docker ip.
    This allows Docker containers to reach pulse on port 4713 but should keep everything else out.
  - Then in the container startup scripts I have some lines like these used for Docker options:

>     -v ~/.config/pulse/cookie:/run/pulse/cookie
>     -e PULSE_SERVER=tcp:$(ifconfig docker0| awk '/inet addr/{print substr($2,6)}'):4713
>     -e PULSE_COOKIE=/run/pulse/cookie

- Turns out you don't need `xhost local:` in your scripts if I you are sharing `/tmp/.X11-unix`
  and have $DISPLAY set. I'm not sure how I missed this 8 months ago but it is nice to avoid that.
- There is a lot to love about Docker but like many CLI interfaces it could use some work.
  I mostly start containers with scripts but I also have a couple of aliases for some common other
  tasks:
  - To show current containers both running and not, `alias dps='docker ps -a --format "table
    {{.Names}}\t{{.Status}}\t{{.Image}}"'`
  - To run a command in the container with a terminal, which I often use like `dexec container
    bash`. The alias is `alias dexec='docker exec -t -i'`

Recently I posted about how I use
[containers rather than VMs](http://backgroundprocess.com/infrastructure/containers-over-vms/) but
those use cases are just the beginning. As I add applications
to my workstation I can now be conservative on what I install and what install sources I trust on
my workstation and instead use a container to keep unknown software confined.
