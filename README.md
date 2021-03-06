# Etherpad Lite image for Docker

This is a fork of https://github.com/tvelocity/dockerfiles/etherpad-lite, which
installs Etherpad from the current Git repository instead of the latest release.

Bug fixes are frequent, but releases sparse.

# Original description

This is a docker image for [Etherpad Lite](http://etherpad.org/) collaborative
text editor. The Dockerfile for this image has been inspired by the
[official Wordpress](https://registry.hub.docker.com/_/wordpress/) Dockerfile and
[johbo's etherpad-lite](https://registry.hub.docker.com/u/johbo/etherpad-lite/)
image.

This image uses an mysql container for the backend for the pads.

## About Etherpad Lite

> *From the official website:*

Etherpad allows you to edit documents collaboratively in real-time, much like a live multi-player editor that runs in your browser. Write articles, press releases, to-do lists, etc. together with your friends, fellow students or colleagues, all working on the same document at the same time.

![alt text](http://i.imgur.com/zYrGkg3.gif "Etherpad in action on PrimaryPad")

All instances provide access to all data through a well-documented API and supports import/export to many major data exchange formats. And if the built-in feature set isn't enough for you, there's tons of plugins that allow you to customize your instance to suit your needs.

You don't need to set up a server and install Etherpad in order to use it. Just pick one of publicly available instances that friendly people from everywhere around the world have set up. Alternatively, you can set up your own instance by following our installation guide

## Quickstart

First you need a running mysql container, for example:

```bash
$ docker run -d -e MYSQL_ROOT_PASSWORD=password --name ep_mysql mysql
```

Finally you can start an instance of Etherpad Lite:

```bash
$ docker run -d --link=ep_mysql:mysql indiehosters/etherpad
```

This will create an etherpad database to the mysql container, if it does not
already exist. You can now access Etherpad Lite from http://localhost:9001/
