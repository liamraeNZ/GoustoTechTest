# GuostoTechTest - Platform Engineer

Prepared by Liam Rae-McLauchlan 31/05/2017

## Cloudformation Template

Spins up an autoscaling group, with an ALB, SG, CloudWatch alarm and Launch Configuration  
for an EC2 instance, running standard Amazon Linux

*Paramaters*
Key Name - Key Pair
Instance Type - default: m1.small
Subnets - Must have at least 2 subnets selected for high availability
AllowedIP - CIDR range allowed to connect on port 22 or port 8080

## Cloudwatch Alarm 

When CPU usage sits over 70% for 600seconds, it will trigger an SNS to send an email,   
and also trigger the ScaleUp policy of the Autoscaling group

## Ansible

Ansible is installed during Cloudformation deploy, in the user data script.
It also pulls this repo down, for the playbooks and config.

From there, it installs the following packages:  
Apache  
Java JDK  
Tomcat8  

It then pulls down the WAR file into the Tomcat directory  
and restarts Tomcat, in order to deploy the site.


## Setup
Create stack using tomcat8-ansible.template  
Once the stack is deployed, it the userdata will trigger ansible run
Once the ALB healthcheck is healthy, the URL should be accessible  
http://<endpoint>:8080/clojure-collector-1.1.0-standalone/i
