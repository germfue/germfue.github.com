---
layout: post
title:  "Jekyll diary: Bootstrapping"
published: true
tags: 
 - blog
 - jekyll
priority: 0.8
---

I tend to forget how to bootstrap my Jekyll environment. These are the basic steps I follow to use Jekyll locally.

# Install system dependencies
Fedora does not include in the default installation neither the ruby interpreter nor the packages needed to build your own gems. Installing them is quite straight forward:

    $ sudo dnf install ruby ruby-devel redhat-rpm-config

* ruby: the ruby interpreter
* ruby-devel: development files, needed for native gems
* redhat-rpm-config: this package is needed in order to avoid the following compilation error: `error:/usr/lib/rpm/redhat/redhat-hardened-cc1: No such file or directory `

# Install Jekyll and Bundler
Install Jekyll and all its dependencies for the user executing it:

    $ gem install jekyll bundler

# Build your blog

Use bundler to install all the dependencies for the blog. For that, execute this in the blog root folder:

    $ bundle install

Once you are done with the dependencies, build your blog:

    $ bundle exec jekyll build

# Server your blog locally

To serve the blog, it is as simple as

    $ bundle exec jekyll serve

Now open your browser and type in the URL being displayed in the console, typically `http://localhost:4000` and enjoy your blog.
