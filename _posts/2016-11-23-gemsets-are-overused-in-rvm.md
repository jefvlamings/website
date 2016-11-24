---
layout: post
title:  "Gemsets are overused in RVM"
date:   2016-11-23 16:47:14
categories: rvm ruby
---

When you are introduced to RVM as a ruby version manager you are tempted
to use gemsets for every project. And while this is not a bad practice,
you are missing the point of gem management.

> Don't use gemsets to keep gems separate between different projects.
> This is why Bundler exists.

When you are using Bundler, you don't need a gemset for each project.
Bundler makes sure your ruby application will run with the correct
gem dependencies, no matter what other projects are using for the same
ruby version.

## Good use cases for gemsets
Having bundler doesn't take away the need for gemsets at all.

Good use cases are for example:

* Gem testing
* Gem version juggling

These use cases are well explained in the [RVM documentation](https://rvm.io/gemsets/basics)