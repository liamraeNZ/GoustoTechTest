GuostoTechTest

Prepared by Liam Rae-McLauchlan 31/05/2015

**Cloudformation Template**

Spins up an autoscaling group, with an ALB, SG, CloudWatch alarm and Launch Configuration Must have at least 2 subnets selected for high availability

**Cloudwatch Alarm**  

When CPU usage sits over 70% for 600seconds, it will trigger an SNS to send an email,   
and also trigger the ScaleUp policy of the Autoscaling group

**Ansible**

Ansible is installed during Cloudformation deploy, in the user data script.
It also pulls this repo down, for the playbooks and config.

From there, it installs the following packages:  
Apache  
Java JDK  
Tomcat8  

It then pulls down the WAR file into the Tomcat directory
