---
title: "Codenames"
date: 2022-02-15
draft: false
icon: codenames
description: "A Java Swing implementation of the popular game Codenames."
internalUrl: /projects/codenames/
weight: 30
---

{{< alert "github" >}}
Check out the code on [Github](https://github.com/cartiervu/Type-Racer)! The ~~[hosted service](codenames.link)~~ is down because it was costing money to maintain :smiling_face_with_tear:.
{{< /alert >}}

A Java Swing implementation of the popular game Codenames.

![Demo of the game](https://raw.githubusercontent.com/bvu12/Codenames/master/README_images/Codenames.gif)

## Learning objectives

This project was originally a school assignment to create a Java Swing application - I figured why not try to host this online. This endeavor turned out to be not as simple as I initially thought, and I ended up utilizing the tools below to make it happen (and reading through A LOT of documentation).

## Technologies used

| Technology                             | Description                                                                                                   |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------- |
| [Webswing](https://www.webswing.org/)  | a web server that allows you to run any Java Swing application inside your web browser, using only pure HTML5 |
| [NGINX](https://www.nginx.com/)        | a reverse proxy that points internet requests to the local WebSwing application                               |
| [AWS EC2](https://aws.amazon.com/ec2/) | the server that hosts the above two services                                                                  |
