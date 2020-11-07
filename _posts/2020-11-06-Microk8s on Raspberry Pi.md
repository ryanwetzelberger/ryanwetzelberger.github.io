---
title: Setting up Microk8s on Raspberry Pi
---

I made 1 big goal for my lab.  I wanted to keep the power consumption low.  I could translate that into being more cloud forward, but I wanted to mess around with Raspberry Pi's.  

My next goal is to become more proficient with administering a k8s cluster.  So I started searching for recommendations and guides to install k8s on a set of Raspberry Pi's (I had 2 version 4 Raspberry Pi's).  [Microk8s](https://microk8s.io) kept rising to the top of the list with many installation guides to use. I stuck with [Canonical's Guide](https://ubuntu.com/tutorials/how-to-kubernetes-cluster-on-raspberry-pi#1-overview), since they made Microk8s and Canonical has a decent track record with making and maintaining Ubuntu.  

I read through the instructions first and this looked easy and straight forward.  Install Ubuntu 20.04 like you would install Raspbian on Rapberry Pi.  Then use snap to install Microk8s and start it up.  Well, there were a few gotchas.

At the time of this writing, 1.19 stable version would always fail with '127.0.0.1:16443 connection refused'.  Snap would rollback the install with nothing more than that response. I found a [github issue](https://github.com/ubuntu/microk8s/issues/1707) against Microk8s expressing this same issue.  Great!  Install the edge release and move on.

Next issue I faced was trying to get Microk8s to start.  Well, I found another issue, but this was a LOT easier to find.  Running `microk8s inspect` showed me that I had to enable [cgroups](https://microk8s.io/docs/install-alternatives#heading--arm).  Doing this changed has now allowed me to play with Microk8s.

I can add nodes into the cluster, and start having fun with Microk8s.  