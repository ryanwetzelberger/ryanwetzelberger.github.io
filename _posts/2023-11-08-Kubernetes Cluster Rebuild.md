---
title: Kubernetes Cluster Rebuild
---

So you acquired the Certified Kubernetes Administrator Certification.  Congratulations!  The certification is great to get to know the fundamental building blocks of Kubernetes.  But developers don't want to use kubectl to apply configuration changes.  So how do you apply the knowledge learned from the certification to running production workloads on a Kubernetes cluster?

This question drove me to rebuild my home lab Kubernetes cluster.  On the original build, I loved to tinker around with Kubernetes objects, deploy a test app here, another one there.  However this is not what is considered a scalable solution to run workloads on.  Time to power up the cluster!

My hardware setup:

- 3 Raspberry Pi 4 4GB RAM, 256GB SD Cards
- 2 Gateway Eero
- 1 Eero Extender
- 1 Juniper EX2200C Switch

Odd setup, right?  The Eeros are what I am using to supply wifi for my house.  They are cheap for the features and specs that they provide.  Eero also pioneered home wifi mesh networks.  They don't provide many ethernet ports to plug into, and I wanted a wired network for the Raspberry Pi's to avoid packet failure.  Insert Juniper EX2200C switch here.  Now the raspberry pi's are connected into a wired network to avoid as much interference has possible, and I can access the Raspberry Pi's through my home wifi!

Now it was time to look into the Operating System to install on each of the Raspberry Pi's.  I wanted something that was easy to set up and security was top priority.  Also, if the Operating System comes with Kubernetes installed out of the box, that is a BIG win.  One Operating System jumped to the top, and it was one that I was familiar with.  Enter [Talos Linux](https://www.talos.dev/).

Talos Linux markets themselves as the "Kubernetes Operating System".  The Operating System is minimal, and locked down.  The only way to make changes to the system is by interfacing with it through an API using mutual TLS encryption.  This felt like Kubernetes, which I am on board with.  So I wiped the SD cards and burned the Talos Linux image onto them.  

Lesson Learned:  When bringing up the Kubernetes side of the install, I wanted to use Calico CNI instead of the default Flannel.  The configs for Talos Linux included a commented line to configure Calico instead, so I uncommented it and tried to bring up the Kubernetes cluster.  Something was wrong with that specific version, and some of the pods did not come up.  Changing the version that Calico was using immediately fixed the issue.  There were a few documented issues within Github against that version.  Although I could not find a correlation between my issue and the ones authoring the issue, something seemed to be linked and a newer version came up without a problem.  

Now we have a Kubernetes cluster up.  What's next?  I felt like these questions or tasks needed to be addressed that would help streamline any developer's experience:

- I want to have my cluster reflect the GitOps model.  What tool will I use to accomplish that?
- How do I reach my apps outside of my cluster?  
- How do I secure those connections (certificate encryption)?
- How do I automatically update name records for my apps?
- If I am  leveraging any Cloud provider, how do I manage that configuration?

More to come...