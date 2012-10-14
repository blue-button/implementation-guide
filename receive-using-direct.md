---
layout: default
title: Receiving Health Data Using the Direct Protocol
---

# Receiving Health Data Using the Direct Protocol

Two sentences on this concept and how it relates to developers.

## Workflow

Patient has transmitted their health data to Direct Address that is tied to your application. Application does wonderful things with it.

## Technical

You need to setup a HISP.
You need to make your certificate publicly accessible.
You need to register with a "whitelist" provider.
You need to then give addresses to your users.
Now when you receive messages to those addresses, you do something special with it on-behalf of your user.
Your system will know what type of file it is by doing ZZZ.

If you receive a message that is directed to an unknown address, reject it.

## Privacy & Security


## FAQ

1. How do I get a certificate for my application?
2. How do I get listed in the trusted whitelist?