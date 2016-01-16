# Elm Scaffold

A simple Elm, Html, CSS, and JS application scaffold

==========

Simplify the Elm client development setup. The principle usefullness of this repository is its makefile, which collects some basic commands you might want. This ```README``` will tell you about these commands, in brief.

## Setup

When you've cloned this repository, and you have ```elm```, ```node```, and ```npm``` make sure you start by running:

```sh
elm package install
```

This will download elm-core, and walk you through the process of initializing an ```elm-package.json``` for your project. After that you should also run ```make dev-dependencies``` which will download ```http-server``` and ```livereload```, which are both used in this development workflow. If you incur any additional development dependecies, consider recording them in under the ```dev-dependencies``` rule in the ```makefile``.  

By default, this makefile builds to, and serves, a directory called ```output```. This can be configured in the makefile, if you like.

## Make Serve

At the beginning of a development session, run ```make serve```. This starts an http server based at the directory ```output``` on port 8080. It also starts a livereload server on the default port – this server will reload localhost:8080 whenever a file in the ```output``` directory changes. Finally, it attempts to resolve and compile all elm modules referenced from Main.elm. If you have other dependencies that are important for a build process, you may consider including them in the ```serve``` rule. If these processes spawn a server, further consider adding an appropriate kill switch to the ```stop``` rule, and cleaning any compiled output. Note that, by default, the makefile infixes all compiled files so that they match the wildcard ```*-compiled*```.

## Make

The invocation ```make``` runs ```elm make``` on Main.elm. 

## Make Stop

The ```make stop``` rule terminates all background processes related to the development process, including http- and livereload servers, and should also kill any auxilliary processes, like minification and stylesheet compilation processes. It also deletes all compiled files from the output directory.