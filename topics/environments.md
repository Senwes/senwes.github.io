---
layout: site
title: Environments
body_class: process
---

Currently the conventions are:

* **local** - your local machine
* **test** - the staging or QA build environment, where code is built, integrated and tested
* **qa and functional** - Where code is more thoroughly tested, possibly involving QA team and manual testers
* **uat** - a replica of production for staging. Built and tested code for product owner review, before release. Dependant services may also test against uat.
* **production** - what it says on the tin. Code released here is available to customers.
 