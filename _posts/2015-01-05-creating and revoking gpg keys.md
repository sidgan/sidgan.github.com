---
layout: post
title: "Creating and Revoking GPG keys"
description: ""
category: [technical]
tags: [gpg, crypto]
---
{% include JB/setup %}

## GPG Keys 
OpenGP standards define the semantics for secure information exchange. GPG is the software that follows OpenPG standards. GPG is an acronym for GNU Privacy Guard.

Alice and Bob are the foo-bar, the spam-eggs of the world of computer security. Symmetric key cryptography takes place by two different methods. The first in which there are two keys, both same, and the second in which both keys are different. GPG helps in symmetric key cryptography. 

Assuming Alice and Bob to be two people who want to communicate and send messages to each other. Both will possess their own private and public keys. The public keys are known to all, hence their name public keys. The private keys are known only to the user and under all circumstances must be kept secured. For communication, Alice will sign a message with Bob's public key and send the complete packet to Bob. Now the only key that can decipher Alice's message is Bob's private key, which he possesses, so Bob will easily decipher it. 

For digitally signing messages, Alice will sign using her own private key and send the message, to check the authenticity of the user, the receiving party can use Alice's public key to make sure that it is indeed her. 



## Creating keys
Ubuntu comes pre-installed with GPG, but it can be installed via the apt-get command as: 
<p>
<code>
sudo apt-get install gpg`
</code>
</p>

After the software is installed, generate the keys using: 
<p>
<code>
gpg --gen-key
</code>
</p>

Now a series of questions are presented on the terminal, the software is extremely interactive and easy to use. It asks for options regarding the number of bits for the keys, the real name, email-address and finally the passphrase. The passphrase is a security shield that is used to unlock the private key. Everytime the private key is needed, the terminal will prompt for the passphrase and only then can the private key be unlocked for use. 

After generating the key, export it and set its key-id as the default in the `.bashrc` file. Now anytime you need to use the key, you do not need to input its key-id. 
<p>
<code>
export GPGKEY=XXXXXXXX
</code>
</p>
<p>
<code>
sudo emacs ~/.bashrc
</code>
</p>

## Uploading to Server 

Communication is possible when the public keys can be found and used by other developers. To facilitate this public keys are uploaded to the keyserver. MIT provides a keyserver amongst many others.
<p>
<code>
gpg --output mykey.asc --export -a $GPGKEY
</code>
</p>
<p>
<code>
gpg --send-keys --keyserver keyserver.ubuntu.com XXXXXXXX
</code>
</p>

## Revoking keys

Several conditions may occur which lead to the requirement of a new secret key. These include the key getting compromised, the private key becoming known to another party, the passphrase becoming known to another party or the user forgetting the passphrase.
 
In any condition, when the key or the passphrase gets compromised it is necessary to revoke the key. This is so that no one uses the compromised key to send messages because now these can be deciphered by the intruder party. 

After revoking it is preferred that the new key is signed by another developer. The revocation certificate must be kept safe, if an intruder gets hold of this revocation certificate, they may revoke all the keys of that developer. 

<code>
gpg --output revoke.asc --gen-revoke $GPGKEY
</code>
