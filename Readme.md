# Cloudformation Template
**VPC with Public and Private Subnets (with private subnets routed to NAT instances)**

A good baseline Infrastructure for nested stacks

## Features
**Two Public Subnets** 

* Placed into 1st and 2nd availability zones
* Doesn't matter the region, gets list of zones and uses them

**Two Private Subnets**

* Placed into 1st and 2nd availabity zones
* Ditto

**An Internet Gateway**

**Two NAT EC2 instances**

* Instead of NAT gateway 
* great for a test environment as you are not incurring cost for NAT Gateways
* Not good for production, because NAT instances are not scalable
* Note: this uses a standard Amazon 2 linux, NAT instances should use a unique AMI build using only the nessary libraries and yum packages
* Unfortunately, AWS no longer supports NAT instances, some exist in the market, but for my purposes since this is only for test, it is good enough

**A Bastion Host / Controller**

**Other features**

* Parameter asking for existing PEM Key 
* Parameter to assign VPC Name
* Parameter assigning Environment variables (Dev, Test, Prod)
* Parameter to get availability zones
* This feature is awesome, instead of having to manually get a list of the latest valid AMI IDs for each of the regions, then listing those AMI IDs in a mappings part of the template, this template simply queries for the latest image to list to use as an AMI ID.
	* See the following list for details [https://aws.amazon.com/blogs/compute/query-for-the-latest-amazon-linux-ami-ids-using-aws-systems-manager-parameter-store/](https://aws.amazon.com/blogs/compute/query-for-the-latest-amazon-linux-ami-ids-using-aws-systems-manager-parameter-store/)
* outputs to provide resource details
* exports to provide information necessary for layered stacks