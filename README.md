# myrepooo

K8s, kubespray, kubeadm, Sidecar containers, Init containers, Static pods and purpose, Stateful Set,
Daemon set, Services types, Pod issue, restrict pod communication, Pod & PVC, Deployment rolling strategy
Diff branching strategies, git stash, git rebase
Helm charts, 


I have experienced on various DevOps tools or technologies and I have experience on AWS cloud and I have worked on various AWS services such as ECS instances, VPC, s3, buckets, relational databases, as well as I also got to work on route 53, which is the DNS service provided by AWS for routing. I have worked on load balancers as well and the listener rules that we need to configure in the load balancer. Now coming on to the identity and access management I have on it for, like creation of policy roles, right and users as well. And now coming to the container tools, I have worked on Docker and Kubernetes. So in Docker, we are required to write the Docker file. So in Docker file, we can write various commands and like you can create an image through it. And by using Kubernetes you can host your entire microservices infrastructure on Kubernetes. Apart from that, I also have experience on infrastructure as code tool, which is the TerraForm. So TerraForm is used to create a infrastructure on Cloud. Also, I've experienced on Sharon Python scripting, which can be used for automation purpose, as well as I have worked on, like monitoring and logging as well. So for monitoring, I have worked on Prometheus and Grafana. As well as in logging. I have worked on CloudWatch and Elasticsearch and Kibana tools as well. So these are the tools or technologies that I have mostly worked on as a DevOps engineer.


Kubernetes what happens that to like whenever you are, like creating any replica set, so it only ensures that a specified number of replicas of a Kubernetes pod are running at any given point of time, right? So let's see if a Kubernetes pod is failing or deleted. So the replica set replaces it to maintain the desired number of replicas, right? And it does not support any declarative updates, right or anything like that. But deployments are quite different. Right? In deployments, you can manage replica set and provide declarative updates to pod such as, like you can specify the number of replicas you can specify more so like settings like memory CPU, as well as the name of the container right and port on which it will be running. Apart from that you can also specify the image and its tag, right? You can refer some config map as well. So all these things are provided. By a deployment. So according to my knowledge, this is the difference between replica set and deployment.

Whenever we are like writing any kind of manifest file, so first of all, we need to, like define all the things like the API version, right. Apart from that, we need to specify the like kind of resource that we are going to create create, for example, deployment service, config map right. Also, we have to specify the labels and selectors right. And under the specification section, we have to specify things like container images, resource question limit, environment, variables, volumes, probes, right all these things you have to specify. Also, you need to make sure whatever you are referring inside that manifest file it already exists. Like, you might be mounting some volume, some persistent volume, so it should exist, or if you're entering some config map, right. So these things you need to take care of when you're writing a manifest file.

there could be like various reasons that why the pod is evicted. That first two reason could be the there could be constraints on the memory, right or CPU. The cluster might not be having enough CPU or memory to launch that certain part. Right? There might be other reasons as well. Such as there might be some day toleration right due to which the wall no pod is not getting scheduled on that certain worker node. Apart from that, the node might not be having enough space, right. Or it might be having some pod affinity or anti affinity right to source these are all the reasons that why that certain Kubernetes pod is not getting shedule on that worker node. 

https://medium.com/saas-infra/taints-and-tolerations-node-affinity-and-node-selector-explained-f329653c2bc6#:~:text=Node%20affinity%20provides%20more%20fine,scheduled%20with%20based%20on%20labels.

We can use the node affinity feature so what happens is that if you want to like deploy a certain Kubernetes pod on a certain node, right, so what happens is that many times in a cluster, some nodes are having better configurations like they are having a better CPU better memory, right? And there are some applications that are very resource extensive, right? So in this case, you can use the node affinity feature. So first of all, you need to set up a label on that certain node, and you need to mention that label inside the manifest file. So that pod will be shedule on that certain node only. So in this way, we can ensure this.

there is a way so there is a feature called known as the pod anti affinity. So in the pod anti affinity rule, it ensures that the Kubernetes pods of the same application are not sheduled on the same node. So this prevents multiple Kubernetes part of the same application from running on a single node.

there are like various kinds of points that we need to keep while writing the manifest file. First of all the resource requirements we should ask them, What is the resource requirement right. So, accordingly we have to define the resource requests and limits for the CPU and memory, right. And then we need to like define the Kubernetes services like how they want to expose the user interface, right. Right. Apart from that, the position storage needs to be taken care of right you need to configure the persistent volume claims for the database component to ensure that the data persist across all the pods. Apart from that, you need to make sure that you're managing the secrets properly, right. You can use the Kubernetes secrets or you can use some third party tool to inject the secrets into the Kubernetes pods that you can also do. One more important thing I would like to add is the health check, which is the readiness and liveness probes. So these probes are very important. They are used to monitor the health of the Kubernetes pod. Right? So let's say if it is becoming unhealthy, so it will like try to restart it and fix it right. And also, in order to make the application highly available, we can use the horizontal pod auto scaling as well. So these things I will do take care of while writing the Kubernetes manifest file.


replica set to just make sure that at any given point of time, the given number of replicas are maintained. Right. Let's say you have specified five replicas, so it will make sure that at all times five Kubernetes pods are there running, but horizontal pod auto scaling is different. It checks the utilization on the basis of CPU or memory. Let's say for example, the CPU utilization is above 80%. So the Horizontal Pod Autoscaler will add more number of Kubernetes pod in order to handle the incoming traffic and it will scale it down when the traffic has reduced. So this is a difference between the Horizontal Pod Autoscaler and the replica set.

Know see for load balancer we can use the ingress right load balancer is different. You can use the ingress resource you can define all the like path based routing inside the ingress resource right you can define all your backend services inside that ingress file, right? Let's say if a certain request is coming on a certain path. So that request will be routed to a certain Kubernetes port. Right. So that will load balancing you can do in the ingress file.

yes, there is an option. So what happens that black implementation specific means that like, it makes sure that the path matches right so it makes sure that the path is matching
it turns out that it was to that certain point.

service discovery, right? So Kubernetes provides service resources for defining set of ports and the means of accessing them. So in this way, we can use it or we can use some dynamic DNS as well. So if the endpoints you're referring to have DNS names, you can use.

secrets are used to store sensitive values, like for example, your password for databases right or some secret token right for all these purposes, you can use secrets right? But config maps are used to store non sensitive values, right values like the port number, or the connection string, right or let's say some environment variable. So for all these purposes, we will use the config map.

we will use a blank first of all in the Kubernetes we will use an ingress controller. So the ingress controller we create our application load balancer in your cloud right once that application load balancer is created, you can define all the listener rules in it like right, but also on top of that there is one more component which is the route 53. So this is the DNS component so in the route 53 You can guess yes. Yes, yes, that is also possible. You can create a internal load balancer, right. And you can also map domains to it using a private hosted zone in the route 53 Right so in this case, your Kubernetes cluster will only be accessible if you are accessing it through either a VPN or some bastion host.

there are various ways like for example, like you can use the SSL certificate Yes. Yes, there are various security measures that are coming to my mind right now. First of all, I will launch the cluster in the like, private subnet right, all the worker nodes and everything will be launched in a private subnet. After that, I will give you like a very restricted access to the IAM policies to all the services right after that, like once we are setting up the cluster and like we can use the internal load balancer right. Apart from that you can use the like private hosted zones in route 53. Also, in order to like securely accessible the services, we will use the SSL certificate like we will create a SSL certificate in the certificate manager. Right and then we will attach that certificate to the load balancer so that the application is accessible over HTTPS right. Also I will enable the encryption on the databases. Right. And let's say there are other competence so on that also encryption will be enabled. After that, like I will also like implement VPN as well.

Like Jenkins, for CI CD, right apart from that TerraForm. I've also used in order to create resources on Cloud I also have experience on like monitoring as well, which is Prometheus and Grafana. As well as logging tools as well, such as Elasticsearch and cabana. So all these tools I've used also have organ bash scripting and Python scripting as well.

I have created all the infrastructure from scratch, like setting up the Jenkins server. Right. Also I have also created pipelines from scratch as well for implementing the CI CD process. Also, I have created the end to end infrastructure as well using TerraForm as well, like writing our own modules, right. Also I have written bash scripts and Python script as well for automation purpose as well. And implementing monitoring and logging as well. For collecting the logs and metrics. Given Kibana is actually a visualization tool. This shebang is actually righted on. It makes a shell script executable so it is used to specify like what interpreter we will be using like what kind of shell we will be using.

We also need to provide the executable functional permission. So once you have written the script, after that you have to like run the CH mod command in order to give the executable permission to that script. Then only you can run that script.

there is a certain folder right when you want to, like safeguarded So, in that case like you can implement the file permissions, right so you need to set some restricted permissions on that folder right. So you can make the route as the owner of that to a certain folder right. And after that you can give certain permissions like away or you can give only the read access, but not the like execution or like right access, right. So in this way we can do it also we can use.

we can use a sticky bit. So in sticky bit to what happens is that if it is set on a directory, it restricts the deletion. of files within that directory. After that, what happens that in shared directories where multiple users have write access, so setting the sticky bit can help maintain privacy and prevent the accidental deletion of that to certain directory. So we can use that as well.

let's say in your virtual machine that Docker container is running, which is also hosting your Python services. So first of all, we need to know on which port that there are certain Python services running right so once you get to know the port, you can open that port on the security group, right. And so once you hit the IP address, followed by the port number in the URL so you can access that certain service or the API that is running so in this way we can expose it.

in case of Kubernetes, you can use the ingress so in Ingress, you can implement that path based routing so let's say the user is hitting a certain part, right. So in that you can perform the routing. Or you can use the web server you can use the nginx web server. So in that you can use the like routing, right. So in that you can specify the like, redirection, let's say a certain path is hitting, then you can redirect the request to that to a certain service. So in this way, you can perform the routing


--------------------------------------------------------------------------------------------

I overall have an experience of 4.2 years with DevOps and cloud. And I actually work on various tools for build and release engineering, even automation and orchestration. currently I'm actually working as a DevOps engineer, where my primary responsibilities are building CICD pipelines and integrating multiple stages into the pipeline. So I deal with so many teams so we do write every pipeline for application. There are multiple stages like unit testing, static code analysis, and we do create images, publish images, and I'm even responsible for automation of infrastructure using Amazon Cloud using TerraForm. Apart from these, I do work on Ansible Python and shell scripting. So this is a brief intro about myself.

Day to day activities:

Once the CI CD pipeline is set up, what does the DevOps incident do on a day to day basis? Or once the Kubernetes cluster, or required infrastructure configuration is done? What keeps the DevOps engineers busy throughout the day? I will explain answers to these questions in this video. But before I explain the day to day activities, what keeps the DevOps engineers busy? 

Let me tell you, there are two primary things. Unfortunately, very less is spoken about these things in the courses or on YouTube. But there are two primary things that everyone needs to understand whether you are planning to switch your career to DevOps, data engineering for industry, you need to understand software development lifecycle, and project management. Of course, you don't have to be expert in project management. But at least you need to understand how does a project function in an organization? How does task distribution task allocation, priority is managed between the tasks? Maybe a basic understanding of Scrum Kanban will definitely help you in understanding any technology or string much better. Similarly, if you understand software development lifecycle, and if you take DevOps as an example, if you understand how DevOps fits in the software development lifecycle or how DevOps helps in the software development lifecycle, you will understand DevOps much better. That's fine. Try to focus on these two things. Of course, in this video, I will explain you the day to day activities. But if you get understanding of software development, lifecycle, and basics of project management, your way of looking at the watch will change computing. Yeah, unfortunately, a lot of courses don't cover these things. But fortunately, we have a lot of content on these topics on our channel. I'll put the links in the description. Whenever you have free time. Try to explore DevOps role in SDLC and project management. How does a project manager manages a DevOps team? So let's go back to the topic that is the day to day activities, often DevOps. Things you might have the CI CD pipeline setup, but SDLC is not linear. software development lifecycle is always a cycle. If you take Android or iOS as an example, every three months, we have the new version of iOS, we have the new version of Android and we take that update. We upgrade to the new version. That means every three months, there is some activity. During these three months, the developers are adding new features, fixing the bugs, and these new features or the bugs that these engineers are fixing might result in the changes to your infrastructure might result changes to your configuration of your organization. And as a DevOps instead, you have to continuously adopt to this. Also, there can be new micro services that need to be introduced by your organization. And whenever there is a new micro service again it's a continuous process. You have to set up the infrastructure requirements for it. You have to write the C ICD pipelines, you might have to look into the Kubernetes cluster configuration for this micro service. This is just one part. Other part as a DevOps engineer, you have to continuously maintain the existing pipelines, or you might have to upgrade your existing clusters. Let's take example of Kubernetes clusters. You might have some 10 to 15 Kubernetes clusters in your organization. And you might have to continuously upgrade them to the new version. When there are patches when there are certain CDs vulnerabilities. You can move to automatic upgrades by the cloud providers. Or you can also manage by them, manage them by yourself. So this is another activity that keeps you busy. Along with that, there are always new tools, best practices. Let's say you are implementing the CI CD pipelines using Ansible Ansible or some scripts and you want to adopt flatly Argo CD. This is a project it's not one day of activity. Because organizations who are in microservice architecture, there can be 20 3050 microservices and implementing such changes to all of them at once is not possible. So what you will do, you will first try out a proof of concept to migrate from Ansible shell scripts or Python scripts to the Git ops architecture. And as you migrate, you know you will do the proof of concept with one microservice once a day successful. You might onboard 10 microservices, which are of less priority, then you will migrate the next 10 micro services with second lowest priority, then you will migrate the entire thing. And such projects takes months together it's not a single activity, single activity. I'll also give you one example, which I have worked in the past, probably that will also help you understand things much better. This is a real time task that I'm talking about. I work for a project where there are stateful set applications on the Kubernetes clusters. So we were using Eks and the stateful sets were running on the Eks cluster and the volumes, the persistent volumes which we were using, but using AFS the elastic file system on AWS. And, you know, first significant improvement, we wanted to move to the file system such as NetApp ONTAP. It's a very simple project. But if you look at the number of stateful sets that we had to evaluate what kind of performance improvements that Amazon Fs X for NetApp ONTAP will bring compared to the ESS so we have to validate each and everything. Perform the proof of concepts. First, prepare the architecture. Write down the pros and cons, what benefits the organization gets once the organization moves to Amazon MSX performance improvements deduplication advantages of continuous backups, snapshots, hacking proof that we have to take analysis of all of these things and migrate the 50 or 40 StatefulSet. We had this as an example. It took like more than four to five months to implement this entire project. Similarly, people might have on premise to cloud migration a lot of companies are still migrating to cloud and these projects takes years together. One more important day to day activity of DevOps instead is past optimization. I keep talking about cost optimization a lot. Right? I've seen videos on the channel in the AWS playlist. I have used serverless functions to implement the cloud cost optimization on AWS. Right so this is a continuous process. It's not a one time activity. You might manage cloud cost, you might optimize the cloud cost for one particular AWS resource today. later point of time, you have realized you're not doing that great with managing s3 buckets. You're wasting resources, you're missing the cost for your organization. Later, let's say the same thing happens with EBS. Then the same thing happens with let's say EMS for any particular AWS resource, you know it's a continuous activity that you have to perform as a DevOps engineer or security complaints. We have done such projects on the AWS zero to hero playlist, and also DevOps zero to hero playlist.
So these are some day to day activities, which keeps busy, which keeps you busy as a DevOps instead. There are upgrades, there are security patches, there are fixes. There is maintenance of your existing pipelines. There are features features. You don't write code probably for your application, but they can be feature enhancements for your CI CD pipelines. You might be using Jenkins probably might want to move to GitHub actions are within GitHub actions. You might be using certain plugins. You want to move away from that plugin and implement a new plugin, which is a feature, right? So there will be features that will be fixes that will be maintenance activities. You might have to support a lot of development teams. You will get tickets for all of these things. Cloud cost optimization, configuration, compliance, security, the tasks that you get as DevOps incidents are endless. And that's why I'm asking you to learn about software development lifecycle, and project management. 

As a DevOps engineering team, you might manage a lot of development teams. In some organizations, it's one to one map, but in some organizations, one DevOps team might manage four to five development teams. All of them try to create JIRA tickets or tickets for you. Then there is a particular project management process, which is called Agile or Scrum, where you sit and try to prioritize the backlog. You will try to say in the sprint plannings there is product owner project manager. You have the software engineers scrum master, which is all covered as part of the project management. Again, the link is in the description. Don't get confused, don't get worried. I have explained right from creating the JIRA board, which is just for purpose of understanding, but I have explained right from how the backlog refinement is done, how the sprints are created within the sprint, how the tasks are distributed between the team members. Try to watch those videos, links in the description. Right. So I hope you got a better picture as a DevOps engineer. It's not one time activity that you write C ICD pipeline or you write cluster along with that there will be features fixes maintenance activities, security, cost optimization endless.

===================================

K8s, kubespray, kubeadm, Sidecar containers, Init containers, Static pods and purpose, Stateful Set,
Daemon set, Services types, Pod issue, restrict pod communication, Pod & PVC, Deployment rolling strategy
Diff branching strategies, git stash, git rebase
Helm charts, 

--------------------------------------

Terraform:


Providers
Multi-Region
Multi Cloud
Variables and conditions 

Modules
Statefile  -> terraform show 
Remote backend 
provisioners
file Provisioner, remote-exec Provisioner, local-exec Provisioner
-----------------------------------------------------------------------------

KT session from real time CloudOps:

1. Allowing Role Access to RCA Notebook in Amazon Sagemaker:

   - Creating a policy in IAM via terraform to grant necessary permissions related to Sagemaker and assigned the appropriate ARN.
   - Converted JSON code to Terraform, incorporating the required changes in the policy resource.
   - Initiating a pull request (PR) in gitlab and seamlessly applied the Terraform changes after resolving any conflicts.

2. Bastion Server Connectivity:

   - Verifying connectivity from the bastion server to launch pad servers.
   - Conducting DNS lookups and checked security group (SG) settings in RDS for required ports.
   - Creating feature branch in GitHub and modified Terraform code (sg.tf) to include the necessary port (3306) for access.

3. EBS Volume Creation and Mounting on /apps:

   - Created and formatted an EBS volume using Terraform, incorporating modifications in aws_ebs_volume.tf and aws_volume_attachment.tf.
   - Executed commands like df -h and lsblk to confirm volume creation and mounting.
   - mkfs -t xfs /dev/nvme5n1 = to format a new and raw disk volume with xfs file system
     mount /dev/nvme5n1 /apps  = temporary mounting. It will vanish after reboot
   - Ensured persistence across reboots by updating /etc/fstab with the required mount information.

4. User Creation Using Ansible:

   - Configured user creation using Ansible, updating files like users.yml and users-vars.yml.
   - Modified key files including authorized_keys, id_rsa, and id_rsa.pub
   - vim /etc/ssh/sshd_config = to allow groups and user to ssh
   - Adjusted sshd_config to grant permissions for group ID and restarted the sshd service.

5. Ec2 creation using Terraform: 

   - Creating the below terraform files as per the requirement
     iam-roles.tf, iam-trust-policy-documents.tf, iam-policies.tf, iam-instance-profiles.tf & ec2-instances.tf
	 
6. Monitoring CPU Utilization of a Server using DataDog:

   - Accessed DataDog and navigated to Integrations -> Agent -> Amazon Linux.
   - Provided commands to be executed on the EC2 instance for starting the DataDog agent.
   - Demonstrated how to check the status of the DataDog agent using systemctl commands.
 
       systemctl start datadog-agent
       systemctl status datadog-agent
   - Configured DataDog alerts by selecting Monitors -> Manage -> choosing CPU -> defining metrics -> editing hostname
     By following the above steps, we can set the alarm for monitor CPU utilization from DD.

7. IAM User Creation via terraform:

   - First, trained us to write the terraform code for iam-users.tf, iam-policies.tf, iam-policy-documents.tf (converting json to terraform code).
   - After creating users & policies, created iam-groups.tf, iam-group-policy-attachments.tf and iam-group-membership.tf (Attaching policy to a group first then adding the same group to the User). 
   - After saving and commiting the code, created a Pull Request in order to apply in Terraform.

8. Password reset and User ID creation:

   - For User ID creation, first created Group ->   groupadd -g <groupID> <groupname>
   - Adding user to the group, useradd -g <groupID> -c "<useremailID>" <username>
         grep <username> /etc/passwd
   - Resetting the password need not to be expired for the particular user ID by using chage Linux command.

         history | grep chage
         chage -I -1 -m 0 -M 99999 -E -1 <Username>
		 
9. Increasing EBS Volume from Terraform:

    - Need to increase size from 45 to 50 GB in /var. In terraform code, modified the size 45 to 50 in ebs-volumes.tf. After that, creating a PR and applying in terraform after approval.
    - In order to updating the changes in AWS console, used this command -> sudo xfs_growfs -d /var
	
10. IAM Role creation in Terraform:

    - Initiated the process in Github Desktop by creating a new branch using the ticket number.
    - Demonstrated the creation of Terraform code for iam-roles.tf, iam-policies.tf, and iam-policy-documents.tf. This included the conversion of JSON to Terraform code.
    - Guided through the steps of saving and committing the code in the branch.
    - Showcased the creation of a Pull Request in Github, which is crucial for applying changes in Terraform.



Handling L1 & L2 JIRA tickets in CloudOps:-
 
1. Scheduling Carma Maintenance and EOM build for Monitoring via DataDog. 
2. Cloning the account in Github and creating role, policies and trust relationship policies from Visual Studio Console and sending the PR from github to Manager for approval.
3. Editing the security group and S3 bucket policies from console.
4. Managing SVN (SubVersion) Repository and extracting logs.
5. Editing and deleting AMI’s and EBS Volumes through Visual Studio Console and applying through Terraform.
6. Updating the secret keys in the repository level and assigning the value in Github.
7. Installing DataDog agent on ec2 instances.
8. Creating ECR repositories and adding the repo in Github under various accounts.
9. Deleting Ec2 instances along with ASG’s, ELB’s and ECS Clusters as per the requirement through Visual Studio Console and applying through Terraform.
10. Creating S3 bucket, IAM role and Cloudwatch groups and exporting the log files to S3 using AWS Lamda.
11. Adding/Modifying IAM policies in Terraform code as per the requirement.
12. Modifying the Python script in the Lamda function for the logs to be saved in the directories based on the Client’s requirement.
13. Creating new user ID in the Cloud bastion by using ansible script and emailing the Private keys to the user.

===============================================================================================================

Ansible: (COnfiguration & Automation/Management tool)  - IAC 

Introduction - explain with diagram (Master/Slave) - Periodic table 

Diff between Terraform and Ansible 

Win -> Win = RDC Remote Desktop connection 
Win -> Lin = Putty 
Lin -> Lin = SSh 

Various tools available -> Chef and Puppet 

Push Mechanism -> COntrol and Managed node 

Pull mechanism -> chef & puppet 
 
 
Ansible documentation -> Prerequisites _> Python 2 or 3 

Userdata:
	
#! /bin/bash
yum install python-pip -y 

4 servers 

------------------------

connect 1 master - 
vi <keyname.pem>    copy paste pem file
chmod 400 *
connect to slave from master 

Pageant purpose 

If pem file is lost, how to connect to machine? 

ec2-instance stop -> Take AMI image -> create another ec2 using same AMI -> after launching terminate existing ec2 

Ansible topics:

ADHOC commands 
playbook
Grouping 
Vault
Roles


sudo pip install ansible 

ansible --version 

slave machines IP address -> Inventory files /etc/ansible/hosts  

configuration files -> /etc/ansible/ansible.cfg 

creating both files manually

vi slaves.txt -> copying Private IP add of all slave machines 

ansible config file download 

wget paste link 

 
Inventory files = slaves.txt
configuration file = ansible.cfg

Adhoc commands:

ansible all -i slaves.txt -m ping 

ansible all -i slaves.txt -a "uname -a"

yum install httpd
service httpd start
copy index.html

-a = action/argument 

vi index.html -> Hello World 

States: 
install = present
uninstall = absent
start = started
stop = stopped
restart = restarted 


ansible all -i slaves.txt -m yum -a "name=httpd state=present" -b 

-b = become root user 

ansible all -i slaves.txt -m service -a "name=httpd state=started" -b

ansible all -i slaves.txt -m copy -a "src=/home/ec2-user/index.html dest=/var/www/html/index.html" -b  



Ansible Modules -> yaml for Playbook

VSC -> install Ansible extension 

modules -> yum, service, copy 

basic.yaml 

- hosts: all
  remote_user: ec2-user
  become: yes
  tasks:
  - name: install the latest version of Apache
    yum:
     name: httpd
     state: latest
  - name: Start service httpd
    service:
     name: httpd
     state: started
  - name: Copy index.html
    copy:
     src: /home/ec2-user/index.html
     dest: /var/www/html/index.html
     mode: '777'
  
  
  
ansible-playbook -i slaves.txt basic.yaml 


Loop: loop.yaml 

php, mysql, unzip,

- hosts: all
  remote_user: ec2-user
  become: yes
  tasks:
  -name: Install the packages
   yum:
	name: "{{ item }}"
	state: present 
	loop:
	 - php
	 - java
	 - unzip
	 
ansible-playbook -i slaves.txt loop.yaml 

green (unchanged/already installed), yellow (changed), red (Failed)

Ansible is mutable and idempotent 

https://wiki.jenkins-ci.org/JENKINS/Installing-Jenkins-on-Red-Hat-distributions.html

Grouping: 

vi slaves.txt

[group]
1
[gang]
2
3

ansible group -i slaves.txt -m ping 

- hosts: group
  remote_user: ec2-user
  become: yes
  tasks:
  - name: install the latest version of Apache
    yum:
     name: httpd
     state: latest
  - name: Start service httpd
    service:
     name: httpd
     state: started
  - name: Copy index.html
    copy:
     src: /home/ec2-user/index.html
     dest: /var/www/html/index.html
     mode: '777'
	 
httpd will be installed only in Slave 1 (group)


jenkins.yaml

- hosts: jenkins 
  remote_user: ec2-user
  become: yes
  tasks:
  -name: Add repo jenkins
   yum_repository:
    name: jenkins
    description: jen yum repo 
    baseurl: http://pkg.jenkins.io/redhat-stable
	gpgkey : http://pkg.jenkins.io/redhat-stable/jenkins.io.key
  -name: install latest version of java and jenkins	
	yum:
	name: "{{ item }}"
	state: present 
	loop:
	 - java
	 - jenkins 
  - name: Start service jenkins, if not started
    service:
     name: jenkins 
     state: started
	
ansible-playbook -i slaves.txt jenkins.yaml 

hitting 1 IP , jenkins will start 

Changing port number via Playbook :- 

cd /etc/sysconfig -> vi jenkins
sudo vi jenkins -. changing port number 

ansible module to edit file 

jenkins.yaml

- hosts: jenkins 
  remote_user: ec2-user
  become: yes
  vars:
	ports: 9090
  tasks:
  -name: Add repo jenkins
   yum_repository:
    name: jenkins
    description: jen yum repo 
    baseurl: http://pkg.jenkins.io/redhat-stable
	gpgkey : http://pkg.jenkins.io/redhat-stable/jenkins.io.key
  -name: install latest version of java and jenkins	
	yum:
	name: "{{ item }}"
	state: present 
	loop:
	 - java
	 - jenkins 
  - name: Start service jenkins, if not started
    service:
     name: jenkins 
     state: started
  - name: changing jenkins port number
    lineinfile:
     path: /etc/sysconfig/jenkins 
     regexp: '^JENKINS_PORT='
     line: JENKINS_PORT={{ ports }}
	 
rm -f jenkins.yaml

vi jenkins.yaml -> paste above 

checking in slave machine -> /etc/sysconfig/jenkins, 
port number will be changed

if hitting slave mach with 9090, jenkins wont start, needs to restart


Handler-> jenkins to be restart 

- hosts: jenkins 
  remote_user: ec2-user
  become: yes
  vars:
	ports: 9090
  tasks:
  -name: Add repo jenkins
   yum_repository:
    name: jenkins
    description: jen yum repo 
    baseurl: http://pkg.jenkins.io/redhat-stable
	gpgkey : http://pkg.jenkins.io/redhat-stable/jenkins.io.key
  -name: install latest version of java and jenkins	
	yum:
	name: "{{ item }}"
	state: present 
	loop:
	 - java
	 - jenkins 
  - name: changing jenkins port number
    lineinfile:
     path: /etc/sysconfig/jenkins 
     regexp: '^JENKINS_PORT='
     line: JENKINS_PORT={{ ports }}
    notify: restart jenkins 
  - name: Start service jenkins, if not started
    service:
     name: jenkins 
     state: started
  handlers:
  - name: restart jenkins
    service:
     name: jenkins 
     state: restarted
	 
In master mach, rm -f jenkins.yaml

vi jenkins.yaml -> paste above

ansible-playbook -i slaves.txt jenkins.yaml 


ansible-playbook -i slaves.txt jenkins.yaml -e "ports=7799"


Vault:

vault.yaml

username: Admin
password: Admin123

pass.yaml

- hosts: all  
  remote_user: ec2-user
  become: yes
  vars_files:
    vault-pass.yaml
  tasks:
  - name: trying out echo command
    debug:
	  msg: "Hello my user name is {{ username }} & password is {{ password }}"
	

Run from Master machine 

ansible-playbook -i slaves.txt pass.yaml --syntax-check 

ansible-playbook -i slaves.txt pass.yaml

Encrypt vault file: 

ansible-vault encrypt vault.yaml

cat vault.yaml 

ansible-playbook -i slaves.txt pass.yaml --ask-vault-password 

ansible-vault view vault.yaml 

ansible-vault decrypt vault.yaml 

cat vault.yaml 

Roles:

ansible-galaxy init apache

ls -lrt -> cd apache 

sudo yum install tree -y 

tree apache/ 

from basic.yaml ->

copy task in main.yml ->  give src : index.html (only file name)

cd apache/files 

vi index.html -> Hello world

roles.yaml:

- hosts: all  
  remote_user: ec2-user
  become: yes
  roles:
	- apache 
	
ansible-playbook -i slaves.txt roles.yaml

=========

Deployment -> httpd
Deployment -> tomcat 

1. yum update
2. java installation
3. tomcat download
4. Unzip tomcat 
5. Start tomcat 
6. tomcat port number changed
7. Java deployment 

tomcat.yaml:

- hosts: all  
  remote_user: ec2-user
  become: yes
  tasks:
   - name: Upgrade all packages
     yum:
	  name: '*'
	  state: latest 
   - name: Installing Java 
     yum:
	  name: java-1.8.0-openjdk
	  state: present
   - name: download tomcat 
     get url:
       url: https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.83/bin/apache-tomcat-9.0.83.tar.gz
       dest: /opt
       mode: '777'
   - name: Extract tar file 
     unarchive:
	   src: /opt/apache-tomcat-9.0.83.tar.gz
	   dest: /opt 
	   remote_src: yes 
	   mode: '777'
	   
	   
ansible-playbook-i slaves.txt tomcat.yaml

connect from master to slave machine -> ssh ec2-user@slaveIP

cd /opt/
ls -lrt -> u can see the extract file 


- hosts: all  
  remote_user: ec2-user
  become: yes
  tasks:
   - name: Upgrade all packages
     yum:
	  name: '*'
	  state: latest 
   - name: Installing Java 
     yum:
	  name: java-1.8.0-openjdk
	  state: present
   - name: download tomcat 
     get url:
       url: https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.83/bin/apache-tomcat-9.0.83.tar.gz
       dest: /opt
       mode: '777'
   - name: Extract tar file 
     unarchive:
	   src: /opt/apache-tomcat-9.0.83.tar.gz
	   dest: /opt 
	   remote_src: yes 
	   mode: '777'
   - name: Starting tomcat
     ansible.builtin.shell: nohup /opt/apache-tomcat-9.0.83/bin/startup.sh & 
	



In master mach, rm -f tomcat.yaml 

ansible-playbook-i slaves.txt tomcat.yaml
	
hit slave IP address:8080 tomcat will be installed 

ssh ec2-user@slavemach

cd /opt/apache-tomcat-9.0.83/

cd conf/

vi server.xml -> COnnector port 8080-> 8888

logout

from master mach, scp ec2-user@slaveprivateIP:/opt/apache-tomcat-9.0.83/conf/server.xml .

ls
vi server.xml -> edit connector port as "{{tomcat_port}}"

template module 

mv server.xml server.xml.j2 


- hosts: all  
  remote_user: ec2-user
  become: yes
  vars:
    tomcat_port: 7788 
  tasks:
   - name: Upgrade all packages
     yum:
	  name: '*'
	  state: latest 
   - name: Installing Java 
     yum:
	  name: java-1.8.0-openjdk
	  state: present
   - name: download tomcat 
     get url:
       url: https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.83/bin/apache-tomcat-9.0.83.tar.gz
       dest: /opt
       mode: '777'
   - name: Extract tar file 
     unarchive:
	   src: /opt/apache-tomcat-9.0.83.tar.gz
	   dest: /opt 
	   remote_src: yes 
	   mode: '777'
   - name: Changimg server.xml port no
     template:
	   src: /home/ec2-user/server.xml.j2 
	   dest: /opt/apache-tomcat-9.0.83/conf/server.xml
	   mode: '777'
   - name: Stopping tomcat
     shell: nohup /opt/apache-tomcat-9.0.83/bin/shutdown.sh & 
   - name: Starting tomcat
     shell: nohup /opt/apache-tomcat-9.0.83/bin/startup.sh & 
	 
rm -f tomcat.yaml

vi tomcat.yaml 

ansible-playbook -i slaves.txt tomcat.yaml 

hit slaveip:7788 

ansible-playbook -i slaves.txt tomcat.yaml -e "tomcat_port=9090"


ssh slaveIP
cd /opt/apache
cd bin/
cd ..

sample war file for tomcat 9

wget link 

- hosts: all  
  remote_user: ec2-user
  become: yes
  vars:
    tomcat_port: 7788 
  tasks:
   - name: Upgrade all packages
     yum:
	  name: '*'
	  state: latest 
   - name: Installing Java 
     yum:
	  name: java-1.8.0-openjdk
	  state: present
   - name: download tomcat 
     get url:
       url: https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.83/bin/apache-tomcat-9.0.83.tar.gz
       dest: /opt
       mode: '777'
   - name: Extract tar file 
     unarchive:
	   src: /opt/apache-tomcat-9.0.83.tar.gz
	   dest: /opt 
	   remote_src: yes 
	   mode: '777'
   - name: Changimg server.xml port no
     template:
	   src: /home/ec2-user/server.xml.j2 
	   dest: /opt/apache-tomcat-9.0.83/conf/server.xml
	   mode: '777'
   - name: Stopping tomcat
     shell: nohup /opt/apache-tomcat-9.0.83/bin/shutdown.sh & 
   - name: Starting tomcat
     shell: nohup /opt/apache-tomcat-9.0.83/bin/startup.sh & 
   - name: Copy files 
    copy:
     src: /home/ec2-user/sample.war 
     dest: /opt/apache-tomcat-9.0.83/webapps
     mode: '777'	 
	 
rm -f tomcat.yaml
vi tomcat.yaml

ansible-playbook -i slaves.txt tomcat.yaml -e "tomcat_port=9999"

hit slaveip:9999/sample 

===============================================================================================

AWS

Security group:

A security group acts as a virtual firewall to control incoming and outgoing traffic. 
Inbound rules control the incoming traffic, and outbound rules control the outgoing traffic
 When we launch an instance, we can specify one or more security groups else it uses the default security group
We can modify the rules for a security group at any time. New and modified rules are automatically applied. 
When we launch an instance in a VPC, we must specify a security group that's created for that VPC. After launching an instance, we can change its security groups. 
Security groups are associated with network interfaces ( point of interconnection between a computer and a private or public network).


A public IP address is a public address assigned to your network by your internet service provider (ISP) 
and is used to provide access over the internet. A private IP address, on the other hand, is one that is 
assigned to your device directly by your network router.

An Elastic IP address is a static, public IPv4 address designed for dynamic cloud computing. 
You can associate an Elastic IP address with any instance or network interface in any VPC in your account.

A virtual private cloud (VPC) is a virtual network dedicated to your AWS account. 
It is logically isolated from other virtual networks in the AWS Cloud. 
You can specify an IP address range for the VPC, add subnets, add gateways, and associate security groups.

A subnet is a range of IP addresses in your VPC.
A public subnet is a subnet that is associated with a route table that has a route to an Internet gateway. 
This connects the VPC to the Internet and to other AWS services. 
A private subnet is a subnet that is associated with a route table that doesn't have a route to an internet gateway.


NAT gateway is a Network Address Translation (NAT) service. You can use a NAT gateway so that instances 
in a private subnet can connect to services outside your VPC 
but external services cannot initiate a connection with those instances.

An internet gateway is a horizontally scaled, redundant, and highly available VPC component that allows communication 
between your VPC and the internet. It supports IPv4 and IPv6 traffic.
An internet gateway enables resources in your public subnets (such as EC2 instances) to connect to 
the internet if the resource has a public IPv4 address or an IPv6 address. 

IgW allows both inbound and outbound access to the internet whereas the NAT Gateway only allows outbound access. 
Thus, IgW allows instances with public IPs to access the internet whereas NAT Gateway allows instances with private IPs to access internet.

VPC - It is a Virtual Private Cloud which is used to create virtual network for any organization in aws

CIDR - It is classsless Inter Domain Routing. Internet protocol allocation methodology

Subnet - A range netting under vpc. 

Route Table - Set of rules and regulations for network

IGW - Internet Gateway. It makes vpc available to internet

NAT - Network Address Translator. For enabling private instance in internet. 


S3 : Simple Storage Service
Object - Image, doc, audio, video 
Bucket - kind of folder - 100 default -> upload object
 Link (accessible everywhere)
Bucket Key versoning - Back up 
Encryption - cost effective
 
Create Bucket -> bucket name -> Region -> Block Public Access to be checked
-> Bucket versioning -> done
Upload file -> done
File = Object URL 
-> Permissions 

Ec2: 
AMI - back up of servers - Disaster Recovery

RDS : Relational Database Service 
RDS -> Standard create -> MySQL -> Version 8.0.27
-> Free Tier -> Master Username password -> Storage and type 
-> Multi AZ -> VPC & Subnet ->  create

Endpoint & Port number 

VPC: 
NAT -> Public subnet instance to communicate with Priv subnet instance -> Attach NAT gateway to Private RT
Elastic IP -> Static IP 
IGW -> provides internet to VPC -> attach to Public RT 
RT -> Subnet associations 

Elastic LB:

Classic LB -> traditional LB 
Application LB -> http, https - 7th OSI App layer 
Network LB 
Gateway LB

CLB -> name-> give SG -> configure health check -> 
ping path, Response timeout -> add ec2 inst -> 
 
Out of service, In service 
DNS name 

ALB -> create Target group -> create target1 & target2
health check path -> /sample/index.html 

create ALB -> both instances should be diff subnets
Listeners -> edit rules 

Route53:

Manage DNS name and IP address 
Hosted zone -> SOA and name server record 
unique domain name 

SNS & Cloudwatch: 
SNS -> create topic -> email option select end point 
subscription created
Cloudwatch -> In alarm -> set alarm
log group -> create log group name 

SQS Lamda:

create IAM Role
Lamda -> create function -> name -> select python 3.9 code
-> select iam role -> 
Add trigger-> select SQS 

AWS Lambda is a serverless service run code for virtually any type of application or backend
 service without provisioning or managing servers
 
NACLs operate at the subnet level and control traffic in and out of a VPC, 
while Security Groups operate at the instance level and control traffic to and from individual EC2 instances

WAF is a web application firewall that helps protect web applications from attacks
by allowing you to configure rules that allow, block, or monitor (count) web requests based on conditions that you define.

------------
Automated Build and release process by integrating Jenkins with GIT.
• Deploying and maintaining production environment using AWS EC2 instances and ECS with Docker.
• Performed AWS Cloud administration managing EC2 instances, S3, SES and SNS services.
• Managed Docker orchestration and Docker containerization using Kubernetes.
• Used SonarQube Monitoring tools extensively for alerts/alarms on production servers.
• Creating Ansible Playbooks to Deploy VM and install the Components as per requirements.
• Worked in managing the Nexus & Artifactory repositories for the maven artifacts & dependencies.
• Implementing new projects builds framework using Jenkins & maven as build framework.
• Used Shell scripts to automate the deployment process.
• Identify, troubleshoot and resolve issues related to the build and deploy process.

Compose is a tool for defining and running multi-container Docker applications. With Compose, you use a YAML file to configure
 your application's services. Then, with a single command, you create and start all the services from your configuration.
 
=====================================================================

VPC:

- virtual private cloud (VPC) is a virtual network dedicated to your AWS account.
- logically isolated from other virtual networks in the AWS Cloud.
- You can specify an IP address range for the VPC, add subnets, add gateways, and associate security groups.

10 web servers (Public subnet)   10 DB servers (Private subnets)

subnet - range of IP addresses in your VPC which can be allocated through CIDR.

Public subnet is a subnet that is associated with a route table that has a route to an Internet gateway. 
This connects the VPC to the Internet and to other AWS services. 
This is typically used for resources that need to be publicly accessible, 
such as web servers, load balancers, and other publicly accessible services.

Private subnet is a subnet that is associated with a route table that doesn't have a route to an internet gateway.
Resources in a private subnet can access the internet, but only via a NAT Gateway or a bastion host in a public subnet. 
This is typically used for resources that do not need to be publicly accessible, 
such as databases, application servers, and other internal services.

CIDR - Classless Inter-Domain Routing is an IP address allocation method that improves data routing efficiency on the internet.

Request coming to VPC from the Subnets can be routed via Route table ( Wifi Router concept)

Route Table - Set of rules and regulations for network.

contains a set of rules, called routes, that determine where network traffic from your subnet or gateway is directed. 

Public RT = attach IgW
Private RT = attach NAT 

Internet gateway (IGW) used to allows communication between your VPC and the internet. It supports IPv4 and IPv6 traffic.
An internet gateway enables resources in your public subnets (such as EC2 instances) to connect to 
the internet if the resource has a public IPv4 address or an IPv6 address.

NAT gateway is a Network Address Translation (NAT) service. You can use a NAT gateway so that instances 
in a private subnet can connect to services outside your VPC 
but external services cannot initiate a connection with those instances.

================================================

24/7 = 05/03/2018  to	16/05/2021  3 years 2 months    -> Digital interaction specialist 

Acesoft Labs = 19/05/2021  to 	16/11/2022  1 year 6 months   -> Content Analyst 

AH Infotech = 16/11/2022  to present (Feb 19 2024)   1 year 3 months  -> DevOps engineer 


Total Exp : 5 years 11 months 
rel exp: 4 years 2 months 
======================================
Self Intro:
Roles and Responsibilties
Day to day activities 

refer abhishek video 
==================================================

SDLC & Project management, JIRA 

Every 3 months we have new activities, devops eng to adapt to these changes 
setup infrastructure
write CICD pipelines
Look K8s cluster configuration for microservices
continously maintain exisiting cicd pipeline
upgrading exisiting k8s cluster coz of vulnerabilities

Work for project has Stateful  
======================================================

Implementing automation tools and frameworks for automatic code deployment which is CICD

Design, deploy, and manage Kubernetes clusters for container orchestration.
Configure and maintain Kubernetes resources such as pods, deployments, services, and ingresses.
Implement best practices for Kubernetes security, scalability, and high availability.

Integrate Kubernetes into CI/CD pipelines for automated deployment and scaling of containerized applications.
Develop and maintain CI/CD scripts and configurations for building, testing, and deploying Docker images to Kubernetes clusters.

Design, implement, and maintain CI/CD pipelines using Jenkins for automated build, test, and deployment processes.
Define pipeline stages for building, testing, code analysis, artifact generation, and deployment to different environments.

Implement Infrastructure as Code (IaC) principles using tools like Terraform or AWS CloudFormation to provision and 
manage Kubernetes infrastructure.
Define Kubernetes resources and configurations using declarative YAML or JSON files.

EC2, VPC, EBS, SNS, RDS, EBS, Cloud Watch, Cloud Trail, CloudFormation 
Auto scaling, Cloud Front, AWS lambda, IAM, S3, R53 etc.

================================================================================================

Good afternoon. My name is Siva Prasad. Currently Im working with AH Infotech, bangalore as a Devops engg and 
I overall have an experience of 4.2 years with DevOps and cloud.
Coming to my experience, i have worked with several services like Terraform, Kubernetes, Docker, Jenkins, Ansible, GIT along with AWS. 
Also, I work on various tools for build and release engineering, even automation and orchestration.
My primary responsibilities are building CICD pipelines and integrating multiple stages into the pipeline. 
So I deal with so many teams so we do write every pipeline for application. 
There are multiple stages like unit testing, static code analysis, and we do create images, publish images, and 
I'm even responsible for automation of infrastructure for Amazon Cloud using TerraForm. 
So this is a brief intro about myself.

=============================================================================================================

DevOps Advance tools to learn:
-------------------------------
Cloud : AWS,Azure,GCP.
IAC : Terraform, CloudFormation, Pulumi, Azure Template 
Container Orchastration : K8s

 K8s Topics:
    Installion
	Architecture
	Various Pods 
	     Service
		 Ingress & IngressController
		 deployment
		 statefulset
		 deamonSet
		 ConfigMap
		 Secret
		 namespace
		 PV,PVC
		 StorageClass
		 RBAC
		 ServiceAccount
		 HPA
		 PodAntiaffinty & PodAffinity
		 NodeAffinty
		 Traint & Toleration
		 resource limitations
		 liveness probe & readness probe
	Kubernetes backup
	Kubernetes upgrade 
    Managed Kubernetes 
	   EKS,AKS,GKE
	   
 
----------------
Important topics:
     Azure DevOps
	 Powershell
	 python script
	 Datadog
	 NewRelic
	 Kafka
	 
SRE :
  Terraform
  Monioring tools : matrics 
                    Traceable 
					Log monitoring 
					Telemtrics
  Devops tools git, github, maven, jenkins,nexus, sonarqube,tomcat/web logic , k8s,docker 
					
DevSecOps
   security addon here
   
   vault
   IAM/AD
   trivy
   sonarQube
   SAST
   DAST
   Each tool security best practices follow 
   
-------------------------------------------------------
AWS Most immportant topics:
-------------------------
 EC2
 VPC
 IAM
 S3
 EKS
 ECR
 CloudWatch
 CloudFormation
 CloudFront
 Rout53
 ELB
 Autoscale
 Lambda
 SNS
 SQS
 CloudTrail
 Cloud9
 SageMaker
 AWS Devops tools:
     codeCommit
	 CodePipeline
	 CodeBuild
	 CodeDeploy
 KMS
 

Terraform Topics:
     Installation
     Lifeline Commands 
	 Datatypes
	 Data Source
     modules	 
	 Provisioner
	 Workspace
	 terraform state
	 terraform registry
	 backend
	 hasicop vault
	 
 Project info : 
 Client : Sony 
 project name :   Scuba
 Description: application about sony media & enternment music 
 project loaction : USA
 Env tools : Linux ubuntu/redhat, Git , Github , AWS, Terraform, jira, Datadog, Gitops : Argocd , Github Actions, python language, Ansible,
             AWS : EC2, S3, VPC, EKS, ECR, SageMaker, Cloud9, IAM, 
 Project period: 6 months
 Team size : 4
 Roles & Responsibility:
    > jira
	> IAM
	> K8s
	> Git , github,github actions
	> Shell scripting 
	> python activity
	> AWS 
---------------------------------------------------------------
AWS 
----
   EC2 
   S3
   VPC
   ELB
   Autoscale
   

