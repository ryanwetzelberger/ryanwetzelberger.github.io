---
title: AWS and Elastic Load Balancing
---
Note: I have been clearing looking through some drafts of blogs and came across this one.  This is rather old, but still has some decent content in it.

I just started studying for the AWS Certified Developer Associate Certification.  I used A Cloud Guru's material when studying for my AWS Solutions Architect Associate Certification. Because of the success I had using their material, I am using them for the Developer Associate Certification.  One of the topics covered is Elastic Load Balancing (ELB) and the different types of ELB's that AWS offers.

Today, there are 3 different types of ELB's: Classic, Application, and Network.  Classic is the original ELB that the Elastic Compute Cloud (EC2), operating at the connection and request levels.  Application Load Balancer (ALB) is marketed to be best suited for HTTP/HTTPS traffic.  Network ELB's are best suited for high performance traffic needs operating at the Layer 4 of the OSI Model.  When learning about the 3 types of ELB's, I asked "when would I use the Classic ELB over the ALB?"

Classic ELB's are documented to still be used for any instances built as EC2 Classics, meaning not built in an AWS Virtual Private Cloud (VPC).  I VPC has lots of benefits and is the recommended to build out new EC2 infrastructure in the AWS Cloud.  If the ELB is not load balancing between EC2 Classic Instances, AWS recommends usage of the ALB.  Is there any other reasons to use Classic ELB's over ALB's?

Cost is always a driving factor.  ELB's and ALB's have different cost structures.  Looking at the pricing page for ELB's, Classic ELB's are priced based on run time per hour and the amount of data in GB processed by the ELB.  ALB's are priced based on run time per hour and Load Balancer Capacity Units (LCU).  Looking further into their documentation, LCU's are a unit of measurement based on 4 dimensions: new connections, active connections, bandwidth, and rule evaluations.  AWS will then charge based on the higher used dimension.

What does this mean?  Know your traffic, and do your homework.  Analyze the traffic that is supposed to hit your ELB and work out the cost based on the criteria of the Classic ELB and the ALB.  You might find that the Classic ELB is cheaper.

ELB's are very powerful, providing the ability to scale your application resiliency to traffic load variation or high traffic throughput.  Even though ELB's are powerful, they will add to your overall infrastructure costs.  Do your homework so you know what the up front cost will be before the monthly AWS bill hits your email.

