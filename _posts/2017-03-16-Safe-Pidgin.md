---
layout: post
title:  "Use Pidgin safely with Docker"
published: true
tags: 
 - docker
priority: 0.8
---
I use Pidgin for IRC but given its trajectory of vulnerabilities I never feel really comfortable with it. For this reason, I decided to use it with Docker.

# The Dockerfile

    FROM ubuntu:latest

    # disable interactive debconf mode
    RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

    # update base system
    RUN apt-get -y update

    # install apt-utils to avoid further errors while package install
    RUN apt-get -y install apt-utils

    # install pidgin
    RUN apt-get install -y pidgin

    # set timezone and locale
    RUN ln -fs /usr/share/zoneinfo/Europe/Berlin /etc/localtime
    RUN dpkg-reconfigure -f noninteractive tzdata
    RUN locale-gen en_US.UTF-8
    RUN dpkg-reconfigure -f noninteractive locales
    RUN /usr/sbin/update-locale LANG=en_US.UTF-8

    ENV LC_ALL en_US.UTF-8
    ENV LANG en_US.UTF-8
    ENV LANGUAGE en_US.UTF-8

    RUN useradd -m upidgin
    USER upidgin

    ENTRYPOINT ["pidgin"]

# The explanation

## FROM image:tag

First of all, we will start the docker image from the latest Ubuntu available. I personally like to use Ubuntu for docker images but this would work with Debian too.

    FROM ubuntu:latest

## Debconf configuration

By default, debconf will assume you are working with a console (interactive mode). This will save you quite some errors while installing packages

    # disable interactive debconf mode
    RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

## Update the system

It is better to update all the packages before we start doing changes:

    # update base system
    RUN apt-get -y update

## apt-utils, or how to avoid errors while installing new packages

Interesting enough, updating worked out perfectly but installing new packages triggers errors due to this package being missing. 

    # install apt-utils to avoid further errors while package install
    RUN apt-get -y install apt-utils

## Finally... installing Pidgin!

Just this line is worth the whole post ;)

    # install pidgin
    RUN apt-get install -y pidgin

## When Now means different things...

Setting the timezone and locale requires more steps than you probably though. I keep these lines in my pocket for every Dockerfile:

    # set timezone and locale
    RUN ln -fs /usr/share/zoneinfo/Europe/Berlin /etc/localtime
    RUN dpkg-reconfigure -f noninteractive tzdata
    RUN locale-gen en_US.UTF-8
    RUN dpkg-reconfigure -f noninteractive locales
    RUN /usr/sbin/update-locale LANG=en_US.UTF-8

    ENV LC_ALL en_US.UTF-8
    ENV LANG en_US.UTF-8
    ENV LANGUAGE en_US.UTF-8

## Out of my root!

We will definitely want to run Pidgin under a non-root account:

    RUN useradd -m upidgin
    USER upidgin

## One more step... and done!

We want to have a default command to run in this image. Ready to go!

    ENTRYPOINT ["pidgin"]

# How to run it

These commands assume that your dockerfile is placed on the current directory.

First you need to build it:

    $ docker build -t pidgin .

And then run it:

    $ docker run -d --device /dev/snd --name pidgin -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY pidgin

Let's review the options:

    -d: detach. You do not want to keep the console waiting till you are done chatting
    --device /dev/snd: Add a host device to the container
    --name pidgin: Name of the container
    -v /tmp/.X11-unix:/tmp/.X11-unix: Expose the host folder /tmp/.X11-unix to the container. You will need this if you want Pidgin UI to communicate with your X11 server
    -e DISPLAY=unix$DISPLAY: Expose your DISPLAY environment variable to the container 
