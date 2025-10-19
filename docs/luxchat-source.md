---
layout: default
title: LuxChat Source Code
---

# LuxChat Source Code

The Luxchat Web Client and the iOS/Android apps seem to be based on older versions (classic? even older?) of [element.io](https://element.io/app).

[This Copyright page](https://www.luxchat.lu/app-copyright/) provides links to repos for the clients, but they only redirect to a release download page.

(Timo: I wrote them an email asking to fix this)

## Clients

Found this on the CIRCL Forgejo:

[Maybe Outdated Source?](https://helga.circl.lu/luxchat-agpl-source)

If the above is correct then the clients are probably based on element classic. (the latest clients are called element x)

- [Android](https://github.com/element-hq/element-ios)
- [iOS](https://github.com/element-hq/element-android)
- [Web](https://github.com/element-hq/element-web): https://webclient.luxchat.lu Looks almost exactly like the default web client 

## Servers

<img width="745" height="121" alt="image" src="https://github.com/user-attachments/assets/034dad28-c27c-4f40-99b0-6883cbe11f47" />

Look like they are running [release 1.120.2](https://github.com/element-hq/synapse/releases/tag/v1.120.2) of synapse.

Mostly written in python, which probably explains why they mention python in the hackathon announcement.

## Bots / Integrations

[Here's a repo](https://framagit.org/users/lxcode/projects) from CIX that hosts a bot and some user directory middleware
