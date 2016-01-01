---
date: 2016-01-01T12:20:22-07:00
tags: [projects, launchpad]
title: Launchpad Merge Proposal Helper Script
type: post
---

I've written a script to aid in merge proposals done with [Launchpad](https://launchpad.net/).
Simply run the command with the url of the merge proposal as the argument and the script will
<!--more--> spawn a shell with the working directory being the code with the uncommitted
merge. You can then diff the code, run tests or whatever else as needed.

When you exit the shell you will be prompted to merge, if you choose to do so a commit message will be
populated for you and opened in an editor so you can edit as you choose. This is also your 2nd
opportunity to bail if you need to. Assuming all is good save and the merge will be done.

The script leverages your installed credentials for bzr and will use
[launchpadlib](https://help.launchpad.net/API/launchpadlib) to authenticate
against the api on your first usage.

The script is at https://github.com/tkuhlman/scripts/blob/master/bin/mp

If you use [Launchpad](https://launchpad.net/) give it a try and let me know if it works or you have
any ideas to improve it.

I should note it is bzr specific at this point as the reviews I do are primarily on bzr but it could be
extended with git support as needed.
