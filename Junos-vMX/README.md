# vMX AWS Cloud Formation Templates
![AWS Logo](./images/AWS.png)

## Overview

This Repo contains Cloud Formation templates that remove all of the manual steps required to bring up vMX in an EC2 VPC.  Cloud Formation templates as analgous to Openstack HEAT templates.

These templates perform all of the required steps to launch a vMX instance in AWS as shown in the [vMX on AWS Getting Started Guide](https://www.juniper.net/documentation/en_US/vmx15.1f6/topics/concept/vmx-aws-overview.html) and more.

## Templates

These templates will create a vMX instance with one, two, or three data-plane interfaces (ge-0/0/x) in addition to the default management interfae (fxp0)

Two versions of the templates exist in the repo:

* Launch an instance in an exisitng VPC
	* An existing VPC will be required to launch the instance
	* You will be required to assign a Subnet to each interface that the template will create
	* All of the IP information will be autoamtically assigned to the interfaces 
* Create a new VPC and all resources will be created
	* A new VPC will be created as part of the stack
	* A Subnet per-interface will be created, including a dedicated subnet for the vMX management interface.
	* 

### Existing VPC's
For launching in an exising VPC you must make certain that the following resources (at a minimum) are already created:

* A VPC (of course)
* SSH Key
* At least one subnet (usually you would want one subnet per data plane interface)
* ENI interfaces for every interface you want to attach (You need a minimum of two)

### New VPC's
These templates will crete all of the required resources needed to get a vMX instance running and launch the instance in the newly created VPC.  Below are the elements that are created:

* A VPC (of course)
* Subnets (depending on the tempalte used, either 2, 3, or 4 will be created)
* ENI interfaces
* Elastic IP's if chosen to be applied.
* Internet Gateway (IGW) that will be assigned to ge-0/0/0 to be to leverage that interface as the internet default gateway for the VPC.





