---
layout: post
title:  "Invoking the power of Python"
published: true
categories: development python
---
[Invoke](http://www.pyinvoke.org/) is a task execution library, that brings the power of
[Rake](https://github.com/ruby/rake) to Python. Let's jump right into the juice.

# The setup

For this introduction, we will create a folder `invokepython` and use it as a playground for our exercise. I will
assume you are using Python3, if you are not this is maybe a good time to start migrating.

To get ready, run the following commands:
    $ mkdir invokepython
    $ cd invokepython
    $ pyvenv .
    $ source bin/activate
    $ pip install invoke
    $ touch tasks.py

The file `tasks.py` will contain our tasks definitions.

# The target 1.0

We want to create 2 tasks, one that will print hello world and another that will echo whatever gets input.

    $ inv -l
    Available tasks:

      echo         Echoes a message
      helloworld   Say hello world!


# The code

Sometimes the code explains itself better than any words. Take a look at this:

    from invoke import task

    @task
    def helloworld(ctx):
        """
        Say hello world!
        """
        print('Hello world!')

    @task
    def echo(ctx, msg):
        """
        Echoes a message
        """
        print(msg)

# Running tasks

    $ inv helloworld
    Hello world!
    $ inv echo message
    message
    $ inv echo 'this is a message'
    this is a message

# Matching parameters

Look what happens when the parameters input for the task does not match the definition

    $ inv echo
    'echo' did not receive all required positional arguments!
    $ inv echo this is a message
    No idea what 'is' is!

# Setting dependencies

Change your `tasks.py` to include a dependency in the `echo` task:

    @task(pre=(helloworld, ))
    def echo(ctx, msg):
        """
        Echoes a message
        """
        print(msg)

And now execute it:

    $ inv echo message
    Hello world!
    message

# Document parameters

Adding documentation for the parameters is simple:
    @task(help={'msg': 'message to be echoed'},
          pre=(helloworld, )
          )
    def echo(ctx, msg):
        """
        Echoes a message
        """
        print(msg)

To get access to the documentation:

    $ inv --help echo
    Usage: inv[oke] [--core-opts] echo [--options] [other tasks here ...]

    Docstring:
      Echoes a message

    Options:
      -m STRING, --msg=STRING   message to be echoed

As you see invoke automatically let's you use positional arguments, short option codes (-m) and the extended version
(--msg=STRING)
