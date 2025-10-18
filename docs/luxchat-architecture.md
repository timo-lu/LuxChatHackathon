# LuxChat Architecture

System architecture for LuxChat.

## Overview

[luxchat.lu/en/technical-details/](https://www.luxchat.lu/en/technical-details/) :
```
[...]
Luxchat4Gov and Luxchat for the general public and businesses are personalized applications,
which development is based on a “fork” of the Element FOSS application https://element.io/
[...]
```
<img width="1024" height="709" alt="image" src="https://github.com/user-attachments/assets/01b063d2-a0bd-4872-bfd5-58b9538aee67" />

[luxchat.lu/en/ecosystem/](https://www.luxchat.lu/en/ecosystem/) :
```
[...]

- Mandatory end-to-end encryption of messages;
- IT infrastructure hosted and operated in Luxembourg;
- Open communication between Luxchat service providers;
- No advertising in the Application;
- No monetization of user data.

Each service provider is free to provide a free or paid communication service for the general public and/or businesses, e.g. premium value-added service, with the aim of promoting innovation, creativity and the development of the ICT market.

Luxchat will provide the foundations for the development of new innovative services (free or paid) based on the trusted environment of the application and the national instant messaging ecosystem.
[...]
```
<img width="1920" height="860" alt="image" src="https://github.com/user-attachments/assets/a390bba0-22d7-4107-a301-f43b68acc91e" />


## Source

The Luxchat Web Client and the iOS/Android apps seem to be based on older versions (classic? even older?) of [element.io](https://element.io/app).

[This Copyright page](https://www.luxchat.lu/app-copyright/) provides links to repos for the clients, but they only redirect to a release download page.

(Timo: I wrote them an email asking to fix this)


### Clients

Found this on the CIRCL Forgejo:

[Maybe Outdated Source?](https://helga.circl.lu/luxchat-agpl-source)

If the above is correct then the clients are probably based on element classic. (the latest clients are called element x)

- [Android](https://github.com/element-hq/element-ios)
- [iOS](https://github.com/element-hq/element-android)
- [Web](https://github.com/element-hq/element-web): https://webclient.luxchat.lu Looks almost exactly like the web client 

### Servers

They probably run some version of [synapse](https://github.com/element-hq/synapse) to host the servers.
Mostly written in python, which probably explains why they mention python in the hackathon announcement.

### Bots / Integrations

[Here's a repo](https://framagit.org/users/lxcode/projects) from CIX that hosts a bot and some user directory middleware


