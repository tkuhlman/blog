---
date: 2016-05-27T21:43:39-06:00
tags: [projects, golang, passwordsafe]
title: A Golang implementation of PasswordSafe V3, ready for Beta
type: post
---
The password database I have been implementing in go is ready for Beta! The DB is implemented using the [password safe](http://pwsafe.org/) version 3
database spec. Enough of the features for this are now working that
[0.3.0 release](https://github.com/tkuhlman/gopwsafe/releases/tag/0.3.0) is ready for others to test. <!--more-->

I have been using this code for months and would encourage anyone else needing a password DB to check it out now. I have particularly enjoyed the ability
to search across multiple open password dbs at one time. This was the primary itch I was scratching in taking up this project. Though that feature has been
implemented for months the gui it has been missing some basics such as a reminder to save after changes, the ability to change a DB password and to make a
new DB. These features are now all working.

It is still a beta release because there are many missing features and some known bugs. The primary bug right now is that closing an open DB doesn't work
without closing the entire program. The [project readme](https://github.com/tkuhlman/gopwsafe) has a good running list of missing features in the Roadmap
section. Primarily these are features that take advantage of have multiple DBs open at once, such as the ability to move records from one DB to another.
Lastly the gtk gui could use countless tweaks to clean it up.

If you test it out have any feedback or find any bugs use the [project issues](https://github.com/tkuhlman/gopwsafe/issues) section to notify me.
