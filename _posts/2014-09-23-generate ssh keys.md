---
layout: post
title: "SSH Keys"
description: ""
category: [technical]
tags: [ssh, security]
---
{% include JB/setup %}

## SSH 

SSH stands for Secure Shell. The SSH keys are nearly impossible to crack because they consist of a private and public key both of which are a long string of random characters. For extra protection one can also add a passphrase which means that anytime these keys are used, the user will be prompted for a passphrase. SSH keys enable one user on a machine to log onto another users account on the same machine. Alternatively, they also allow one user to remotely log onto a remote machine.

## Generating SSH keys

SSH keys can have various types of secure algorithms on which they are based. The algorithm being used these days is the RSA or Rivest Shamir Adleman algorithm. To generate the key pair, do:

`ssh-keygen -t rsa`

The entire process of generation of the keys is highly interactive and the user will be prompted for a lot of questions. This interaction is similar to the process of [generating GPG keys](www.sidgan.github.io/technical/2015/01/05/creating and revoking gpg keys/). You can set the location where your SSH keys will be stored and set the passphrase. Then you will be provided with the key fingerprint and the key's randomart image.

Now, the key has been generated and the keys can be placed on the server. This is done with the `ssh-copy-id` command.

`ssh-copy-id user@ipaddr`

Then the system will authenticate the host and add the IP address permanently into its system.

## Remote Login

SSH keys can be used to remotely login to a system as well. The secure shell protocol is most commonly used to securely log onto remote Linux and Unix-like systems as:

`ssh user@ip_addr`

It is the IP address to which you are trying to connect to. `user` indicates the username on the remote host, if the username on your current system and remote system is the same then the command gets modified slightly. There is no need to indicate the username then, so:

`ssh ip_addr`

Now you will be prompted for a password, this is necessary in order to authenticate the user. Then finally you have entered the remote location and can access all the files that your user is allowed.

To exit the session, type `exit`.

The remote location where you are trying to login should have its ssh server running. This is done on the remote location by `sudo service ssh start`




