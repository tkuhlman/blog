---
date: 2015-09-11T21:12:37-06:00
tags: [docker, workstation]
title: Docker for Messy Pets
type: post
---

The primary advantages of containers are realized when they are treated as the cattle of computing not pets. There are many
articles using that analogy to extol the advantages of containers as cattle or
[even as chickens](http://thenewstack.io/pets-and-cattle-symbolize-servers-so-what-does-that-make-containers-chickens/).
However I have been recently rebuilding my Ubuntu Desktop and found containers can at times be great for pets also, most particularly the messy ones.
<!--more-->

I embarked down this route because of my sense of system cleanliness; too many apps I run excrete their dependencies all over my nice newly
installed system. I run a variety of apps that are not available either in the primary repo nor as a PPA or at least not with the version I need. If
I am not careful I can soon find myself juggling gems, eggs, wheels and jars all at the same time. Language specific package managers and tools like
virtualenv and bundler all help some but none are complete enough to take away all management so I still end up following many tools and cleaning
up the mess they leave behind.

This is where Docker containers step in to save me. I simply need to build an image with the app and all its associated dependencies and wrap a
simple shell script around it. Now I can run my app while still maintaining a well organized system with no dependency hell, with no mess left behind
on my system. Instead of using various tools I now have one management tool to aid in running multiple versions or modifications of apps. In addition
I gain additional capabilities, most notably the ability to easily limit the resources an app can use.

On Ubuntu, apt handles both dependency installation and cleanup very well and coupled with the availability of many
[Personal Package Archives (ppa)](https://help.launchpad.net/Packaging/PPA) the additional overhead of creating a container is not
worth it for these well behaved apps. This is particularly true as using apt enables automatic notification of security updates.
Nevertheless there are many apps or at least versions of the app I am using that aren't available as a well behaved deb. These are the messy pets of
my workstation and I am much happier to have them in a container than to have them leaving a mess all over my desktop.

### Implementation Details

I have begun a [github repo](https://github.com/tkuhlman/containers) with Dockerfiles and shell scripts I use for containers on my desktop. I will keep
expanding this as I add more apps which I use in this way. Here are some considerations as you put your messy pets in containers:

- In the wrapper scripts use Docker volumes to setup the appropriate directories, ie `-v /home/me/myfiles:/root/myfiles`.
- GUI apps require some proper setup when running a container:
  - For X based apps first you must allow the app to connect to X then setup access to the display.
    - To allow access to X I generally run 'xhost local:' in the wrapper script. This has security
      implications and shouldn't be done on a shared system but for a system dedicated to a single user is reasonably safe.
    - To setup access to the display export the Display variable with `-e DISPLAY=$DISPLAY` and setup the volume with the x socket
      `-v /tmp/.X11-unix:/tmp/.X11-unix`.
  - For advanced graphics with DRI things are a bit more complicated as you need the drivers you install in the image to match what the host uses.
    After that I found you need to use the device flag for the Docker command to share in the dri device, ie `--device /dev/dri/card0:/dev/dri/card0`.
  - For pulseaudio, these flags to the Docker command work though possible could be distilled down to simpler steps:
      - `-v /dev/shm:/dev/shm`
      - `-v /etc/machine-id:/etc/machine-id`
      - `-v /run/user/$uid/pulse:/run/user/$uid/pulse`,
      - `-v /var/lib/dbus:/var/lib/dbus`,
      - `-v ~/.pulse:/home/$dockerUsername/.pulse`.
- Most docker images run apps as root within the container. Though this is generally fine it can be annoying for files in volume mounts to end up owned
  as root. To work around this you can create a simplified user in the image matching your uid/gid and run apps as that user. All that is needed in
  the images is an /etc/passwd entry, /etc/group entry and an appropriately owned home directory.
- Though this technique could work for any OS, it is most feasible where containers run natively. For those operating systems where containers are run in
a vm it is considerably more painful to run any desktop apps in containers. This is a good reason to run Linux on the desktop.
- The extra security of this approach was not my goal and I have not contemplated the implications much.
The app is far more isolated, but not perfectly so. Also an existing image
won't update and break but is also more difficult to update for application security fixes. In short first glance you gain some security but there
are more aspects that need consideration.
- This technique is less annoying if your local user can run docker without sudo.

### References

I am by no means the first to try this and in fact was able to find many tips on how to accomplish desktop apps in containers. Here are the primary pages
I used as sources:

- https://blog.jessfraz.com/post/docker-containers-on-the-desktop/
- http://gernotklingler.com/blog/howto-get-hardware-accelerated-opengl-support-docker/
- http://stackoverflow.com/questions/28985714/run-apps-using-audio-in-a-docker-container
- http://fabiorehm.com/blog/2014/09/11/running-gui-apps-with-docker/
