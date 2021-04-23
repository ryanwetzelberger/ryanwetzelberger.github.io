---
title: Learning Python Part 1
---

I have been doing and learning many cool things at work.  However, I have been having a hard time adding a new blog post because each thing I learned has been building on top of something else.  So this post will be taking a different approach.  I will make this blog post a series of posts regarding different things I have learned about Python.  I hope to document stages of my advancement with the language.

Before I get into my Python learnings, I have to describe the problem I am trying to address.

My current project can be summed up as building automation around a brown field network environment with hundreds of network devices and varying standards through years of implementation.  Finally, the older implmentations were never brought into compliance.  All of the network devices have different Operating Systems, configurations and standards that I have to build an automation pipeline for.  Sound familiar?  This is my challenge, it has been interesting.

I looked at network automation frameworks and came across 2 leading tools: (Ansible)[https://www.ansible.com] and (Nornir)[https://nornir.readthedocs.io/en/latest/].  Not going into great detail for this discussion (might come in another post), we went with Nornir.  I learned a little Python before coming to the NetOps team.  I loved that I could use the tooling I already know how to use with Python!  Also, it I saw limitations with the growth of the project and being limited to yaml files.  I know Ansible is extensible and has a huge community behind it.  Coming from Python, it felt limiting.

I got my team sold on Nornir.  Nornir has a great inventory system, manages my connnections to the network devices, and can be extensible through a plugin system (introduced in 3.0).  Also, it uses common, open source projects defining tasks.  Already coming from Python, it made the most sense to me to use because it was just another Python Library.  

While building out the automation project with Nornir, I have looked at many Python projects to see how they are organized, and what are some common practices and coding styles between each project.  It has helped me with learning a lot about Python and code project management, and I will be documenting it in future parts.  Please look forward to future posts!