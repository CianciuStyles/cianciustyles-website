---
title: AWS Technical Essentials
date: 2016-11-15 20:39:57
tags:
	- AWS
	- London
	- Seminars
---
Hello! My name is Stefano, and this is the first post I get to write on a blog, ever! I waited so long before sitting down and taking some time to create my personal blog and write this post for the usual "Who in the world would care about another programmer's blog?" and "I don't think I have anything interesting enough to be published online..." thoughts that I guess wander in the mind of someone about to do it, but I figured out it would be an encouraging and "unlocking" experience to just start with baby steps and see where this will go, so... here I am!

In this first post, I would like to talk about an Amazon Web Services seminar I got to attend last week in the beautiful Beaufort House in Aldgate, central London.
{% asset_img beaufort-house.jpg "Beaufort House in Aldgate" %}

It is called AWS Technical Essentials, as it is supposed to be a one-day overview and crash course on the most important services offered by the Amazon Web Services platform, mainly aimed at programmers and software engineers completely new to or with little experience with AWS. The course was divided into both theoretical presentations and hands-on labs, which I found very useful to immediately check and employ the knowledge I had just acquired by attending the former.

Some of the notes I took (by pen and paper!) include the following:
* [Availability zones (AZs)][1] comprise at least two regions, and are basically clusters of data centers
* Currently there are 14 regions and 35 availability zones
* Not all the regions have the same price
* The edge locations are some special cache locations where end users access AWS services
* MFA stands for [Multi Factor Authentication][2]
* [AMIs (Amazon Machine Images)][3] are templates for [EC2 (Elastic Compute Cloud)][4] instances
* [CloudFormation][5] is the way to go to create an EC2 template based on AMIs
* Once you reach a steady-state service, it is far more convenient to switch to [*reserved instances*][6] (which save up to 75% with respect to on-demand instances)
* Once you enable [versioning][7] in [S3 (Simple Storage Service)][8], there is no way to disable it (you can just freeze it)
* You can retrieve earlier versions of a file in S3 by deleting the *delete markers* on that particular file
* [Lifecycle rules][9] allow you to automatically move your files to a cheaper environment, based on time rules specified by you
* [EBS (Elastic Block Store)][10] is like an hard drive for EC2 instances. EBSs are persistent, i.e. they will live even after the EC2 instance to which it's attached  has been terminated
* **Everyone** is responsible for security
* The best thing is to build security together with your application, not adding it later on
* [Federating][11] users means to allow users from other services/locations to login and authenticate
* [Roles and groups][12] are not the same thing: groups are "containers" for accounts, while roles are the entities which actually receive authorizations and permissions
* There is only a layer of [IAM (Identity and Access Management)][13] groups, i.e. you can't create a group within a group
* If you don't specify a role for an EC2 instance while creating it, there's no way to do it afterwards, so you'll need to recreate it
* *Authentication* is gaining access to a service; *authorization* is being able to do stuff
* Identity provider is for federating users (a.k.a. Single Sign In)
* *Vertical escalation* means to give more CPU, RAM, disk, or any other resource to a single instance of a service; *horizontal escalation* means to spin up a new instance of the service and split the load
* *Durability* means "is my data going to be there?"; *availability* means "is my data available now?"
* [ELB (Elastic Load Balancing)][14], [CloudWatch][15] and [Auto Scaling][16] form an environment for dynamic growing/shrinking web applications
* Sticky sessions are requests which will end up always at the same server
* [User data][17] is a script which can be run just after the EC2 instance has been created
* [Launch Configurations][18] are similar to CloudFormation scripts, but include also auto scaling information
* [Trusted Advisor][19] is a service which can audit your instances and report about performance, costs, etc.
* Trusted Advisor cannot change settings on your behalf, you have to manually change them yourself

Wrapping up, I really enjoyed this brief but intense course, I think it gave me a nice overview on the de facto standard platform nowadays, and therefore very useful and interesting to know something about. I would like to thank again a lot [Ryan Little](https://www.linkedin.com/in/ryan-little-97347227) and [Arlen Vartazarian](https://www.linkedin.com/in/arlenvartazarian), which have been my patient and engaging instructors, and say that I hope to meet you again soon!

[1]: http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html#concepts-regions-availability-zones
[2]: https://en.wikipedia.org/wiki/Multi-factor_authentication
[3]: http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html
[4]: http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html
[5]: https://aws.amazon.com/cloudformation/
[6]: https://aws.amazon.com/ec2/pricing/reserved-instances/
[7]: http://docs.aws.amazon.com/AmazonS3/latest/dev/Versioning.html
[8]: http://docs.aws.amazon.com/AmazonS3/latest/dev/Welcome.html
[9]: http://docs.aws.amazon.com/AmazonS3/latest/dev/object-lifecycle-mgmt.html
[10]: http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html
[11]: http://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_oidc.html
[12]: http://docs.aws.amazon.com/IAM/latest/UserGuide/id.html
[13]: https://aws.amazon.com/documentation/iam/
[14]: https://aws.amazon.com/elasticloadbalancing/
[15]: https://aws.amazon.com/cloudwatch/
[16]: https://aws.amazon.com/autoscaling/
[17]: http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html
[18]: http://docs.aws.amazon.com/autoscaling/latest/userguide/LaunchConfiguration.html
[19]: https://aws.amazon.com/premiumsupport/trustedadvisor/