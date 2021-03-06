---
layout: post
title: "Signing GPG Keys"
description: ""
category: technical
tags: [gpg, crypto]
---
{% include JB/setup %}

## Signing GPG Keys 

Signing another person's public keys means that you certifying and stating that you trust that person and their work. [BigLumber](http://biglumber.com/) is a site that allows people to sign each others public keys. You just create your account and upload your ASCII armoured public key. The method of using ASCII armored version to import keys is often preferred because the key comes directly from the user. The keyserver may contain a corrupt key or may be unavailable so the ASCII armored version is given preference. To create the ASCII armoured public key simply do:

`gpg --output key.asc --export -a $GPGKEY`

For authentication purposes [BigLumber](http://biglumber.com/) will send you an encrypted email on your registered email id. You decrypt the mail and follow the instructions and finally you are a member of the [BigLumber](http://biglumber.com/) fraternity. There are several sites that allow signing of public keys, [BigLumber](http://biglumber.com/) is just on of them.

In order to sign someones key you should know their key id, say it is KEYID

`export KEYID=XXXXXXXX`

Then receive this key from the keyserver where it has been uploaded:

`gpg --keyserver pgp.mit.edu --recv-keys $KEYID`

Then sign the key using:
 
`gpg --sign-key $KEYID`

And finally, upload it onto the server once again:

`gpg --keyserver pgp.mit.edu --send-key $KEYID`

Now, you have successfully signed the key and have established a circle of trust.

