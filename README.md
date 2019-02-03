# Overview

## The Problem

In a nutshell: we believe the Internet of Things could be much more useful
if sensors, actuators, displays and other IoT "Things" could simply (and
securely) talk to each other on the local WiFi network. Without going through
some vendor's cloud, and certainly without invading the user's privacy.

Read more about [the problem](problem.md) we want to solve.

## The Architecture

There are three basic ideas:

1. Things on the local WiFi network emit new information (such a sensor values)
   through mDNS. Things also listen to mDNS messages from other Things, and
   potentially take action based on what they hear.

2. Things can find out more about other things, and interact with them based
   on metadata that each Thing publishes on the local network via HTTP.

3. Each Thing has its own a public/private key pair. The public key is published
   to the network, and the private key is kept secret. Outgoing mDNS messages
   are signed with the private key, and potentially encrypted with the
   intended recipient's public key.

This is simple, has low latency, takes very little network bandwidth or energy,
requires minimal setup, and provides confidentiality and authenticity where
needed.

Read more about [the architecture](architecture.md).

## Example Use Cases

* A touchscreen Thing tracks the inventory of all Things on the local network, and
  enables the user to interact with each Thing
* Unlocking the front door remotely and securely

## The specs

* [Secure Decentralized Ambient Synchronization](sdas/index.md)
* [Thing Metadata](metadata/index.md)

## Credits

Obviously, we stand on the shoulders of many great ideas. The peculiars for this:

* Peter Hoddie's [Decentralized Ambient Synchronization](http://blog.moddable.com/blog/das/),
  which proposes to use mDNS to publish IoT data with little latency or overhead.
* Johannes Ernst's [Light-Weight Digital Identity (LID)](https://en.wikipedia.org/wiki/Light-Weight_Identity),
  which used GPG key pairs behind URLs for human and machine internet identity management.
* [Mozilla's Web of Things](https://github.com/mozilla-iot/wot) specification, which,
  like others at the [W3C's Web of Things](https://www.w3.org/WoT/) effort, publishes rich
  metadata about IoT devices via HTTP.
