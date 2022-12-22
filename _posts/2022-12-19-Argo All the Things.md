---
title: Argo All the Things
---

"Kubernetes is the next Operating System!"

I have seen that statement in a few places.  Although I don't agree with the statement, I understand why people are saying it.  Kubernetes provides an easy model to deploy and schedule resources for applications.  Also, there are loads of tools to make it easier to deploy apps the way you would like to deploy them.  

I love managing everything, including my apps, through git.  You can easily look at your git repository and determine what is deployed and how it is configured.  This methodology has been named Git Ops, and there are a few tools that help with detecting changes to git and keeping your Kubernetes cluster in sync.  One tool that provides this functionality is [Argo CD](https://argoproj.github.io/cd/).  

Argo CD is very flexible, defining app deployments through yaml.  At the surface, I have heard of a concept with Argo CD named "App of Apps".  Argo CD has the power to manage applications and keep it in sync with git.  Argo CD can even manage itself.  This functionality sounds promising, and I knew I had to dig deep to uncover it's secrets.  

I found this [blog](https://www.arthurkoziel.com/setting-up-argocd-with-helm/) by Arthur Koziel to help me understand Argo CD with Helm.  His blog was to the point and covered the topic at the appropriate level needed to start getting exposure to Argo CD, Helm, and the concept of "App of Apps".

Even though Arthur does a great job breaking things down, I want to summarize a little here for my own understanding.  

First trick to getting started with Argo CD is deploying it.  The easiest way is to deploy it using Helm.  Helm is a templating tool for Kubernetes manifests.  Arthur recommended running these commands after putting together some basic yaml for configuration of Argo CD:

```
helm repo add argo-cd https://argoproj.github.io/argo-helm
helm dep update charts/argo-cd/
```

The first command adds the repository containing Argo's Charts (the company, not the tool) to your Helm app so it can interact with charts related to Argo CD.  The second command downloads 2 components:

* A tar file of the Argo CD Helm Chart.  We don't need to upload this to git, so we added a gitignore file to ignore this file.
* A lock file that enforces dependencies and versioning of the main app along with it's dependencies.

After setting all of these files up, we can then use Helm to install Argo CD by running:

```
helm install argo-cd charts/argo-cd/
```

Now we can start configuring the root app that will help to track apps deploying to the k8s cluster.  After configuring a chart for the root app, we apply it with this: 

```
helm template apps/ | kubectl apply -f -
```

To install new apps, we add a template to the chart using the argoproject API configuration in the yaml, and viola!  The new app will appear in the cluster after an update to the repository.

If we are managing Argo CD through Argo CD, we will need to tell Helm that it doesn't need to manage Argo CD as an app anymore.  We can run this command:

```
kubectl delete secret -l owner=helm,name=argo-cd
```

This was a great introduction to Argo CD and Helm.  Next things to look into are:

* Configuring Kubernetes Namespaces using Argo CD.
* Modifying configuration for deployed apps.
* Learn how to support kustomize and helm charts in the same Argo CD deployment.

All of my code for this blog is located [here](https://github.com/ryanwetzelberger/kubernetes).  This repository is bound to change after posting this blog post.  