---
title: LetsEncrypt, Docker-Compose, and Containers
---

I have been working on a project to deploy [Nautobot](https://github.com/nautobot) to explore options with open source IPAM (Internet Protocol Address Management) systems.  Naturally, I wanted to take it further and deploy it in containers, while making it secure.  So I looked into deploying Nautobot in containers using docker-compose and securing the sessions using [LetsEncrypt](https://letsencrypt.org/).

To start, why containers?  Well, it is the latest trend application deployments.  Practice with it is always good.  Also, I wanted to take advantage of some of the resiliency microservice architectures (containers use the microservice architecture).  Finally, seeing how easy it is to update applications using containers means I would not be afraid to kick off an update, knowing that the ability to rollback is just as easy.

Docker-compose was my choice for deploying the containers since we only have one VM at the moment to deploy on.  The VM is backed up regularly, so I am not worried about data loss.  Also, this is still a proof of concept.  Deploying on Kubernetes would be a great next step if we lock into Nautobot.  Most of the work with building out everything on docker-compose can be transferred over to Kubernetes with minimal conversion effort.  But Kubernetes' strength comes from multi-node resiliency.  I love how fast I can deploy with docker-compose.

Now that the deployments are out of the way, lets talk about LetsEncrypt.  This service is great for quickly securing web traffic, and keeping it secured with auto update options.  Based on everything I have found with LetsEncrypt, there are 2 options for proving you own the domain you are trying to secure.  

Option 1 allows you to use a bot that will install a file on your server.  The bot tells LetsEncrypt servers to look for the file in the particular location for proof of authenticity.  Then, the bot gets the cert and your web server uses that certificate.  

Option 2 requires a token from a select group of dns providers.  The dns provider has to be the authority of DNS for the domain.  The bot will use that token to update certain dns entries that the LetsEncrypt servers use to verify authenticity.  Then, the bot gets the cert and your web server uses the received certificate.  

