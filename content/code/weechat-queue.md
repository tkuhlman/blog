---
date: 2016-02-01T21:39:58-07:00
tags: [projects]
title: Weechat Command Queues
type: post
---
I use [weechat](http://weechat.org) for much of the day and have issue regular repetitive commands periodically.
If you are in the same situation you may find the [queue plugin](https://weechat.org/scripts/source/queue.py.html/) I recently modified to be useful.
<!--more-->

The queue plugin simply allows you to build up a list of commands then run them all at once. My
[modification](https://github.com/weechat/scripts/pull/137/files) was to allow saving these across restarts of weechat.
That way I can build up a few queues I use regularily and just call them whenever needed.

For example when I start my day I just execute `/qu exec morning` to switch my away status, announce my availability in a couple of rooms, etc.
