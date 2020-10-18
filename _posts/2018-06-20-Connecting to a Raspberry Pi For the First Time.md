Recently, I wanted to start a few projects utilizing a Raspberry Pi. My philosophy when it comes to tech is automate as much as possible. Naturally, I wanted to automate deployments of my projects to the Raspberry Pi. However, I need to figure out how to easily connect to it the first time.

I am utilizing the Raspbian Operating System on my Raspberry Pi. It is the recommended OS for the Raspberry Pi, and it is based on Debian Linux. I am very familiar with Linux growing up outside of the world of Windows. One crucial package provides functionality for mDNS.

Multicast DNS is a great way to set up communication on a network with minimal setup. MacOS and Raspbian support mDNS out of the box. Windows requires an additional package. The easiest way to get mDNS on Windows is to install iTunes. Have you heard of Bonjour? It is included with iTunes. It is also using mDNS.

mDNS communicates on a known IP Address that is broadcasted on the local network. Anyone who is talking mDNS is also listening on that same address. This is done automatically, sharing hostnames and IP Addresses so others on the network know how to reach each other. I can plug my MacBook directly up to the Raspberry Pi via a patch cable. After both devices default to Link Local Addressing, I ping "raspberrypi.local" from my MacBook and success!

Pinging a device and seeing success feels great, but you will want to connect to it. Make sure to add a file named "ssh" to the root of the MicroSD Card after cloning the Raspbian image to the card.

mDNS simplifies initial connection to the Raspberry Pi. This has helped me to easily build automation to deploy projects with a base image of Raspbian.

References:

https://en.wikipedia.org/wiki/Multicast_DNS

https://raspberrypi.stackexchange.com/questions/58478/ssh-not-working-with-fresh-install

