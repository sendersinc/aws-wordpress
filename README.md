# aws-wordpress
Terraform Ansible Script to deploy a EC2 LAMP Wordpress instance


This project is to launch a Wordpress Instance on Ubuntu LAMP Server.

**Scripts are under terraform directory**

The task is deployed under two phases,

   1) Deploy the EC2 instance  : Using Terraform  (Terraform v0.11.3 )(Launches Ubuntu Server using ami-66506c1c)
   2) Deploy the WordPress on LAMP : Using Ansible (Ansible v2.3.1.0)



**(I) STAGE 1  Deploy EC2 instance**

  (A) **AWS instance keys to authenticate should be added under ~/terraform/keys**
        Add keys under keys directory. Name should be admin_key admin_key.pub
  
  (B) Terraform provisions the following services under AWS
      (a) A security group for Wordpress instance to allow port 80 and 22 traffic
      (b) A EC2 Instance (Ubuntu 16.04.2 LTS \n \) with Public & Private IP addresses Using AMI **ami-66506c1c**
      (c) Associate a key to the provisioned EC2 for getting ssh access. User by default will be "ubuntu" Keys are          saved under 'keys' directory
      (d) Once the deployment is done, using 'local-exec' terraform updates Ansible hosts file with new EC2 
          instan

**(II) STAGE 2 Deploy LAMP & Wordpress on EC2**
    
   (A) Ansible access to EC2 instance using 'ubuntu' user and deploys Apache, Mysql & PHP first
   (B) Downloads and install Wordpress


TO DEPLOY :


*1) ENSURE KEYS ARE ADDED AS MENTIONED IN POINT I.A*

2) RUN terraform plan to see the computing path

3) RUN terraform apply, and the process will run and if successfully finished, you can see output similar to below:

-------------------------------------------------------
aws_instance.wordpress_server (local-exec): ==============================================
aws_instance.wordpress_server (local-exec): ----------------------------------------------
aws_instance.wordpress_server (local-exec): Use http://x.x.x.x to load and configure your
aws_instance.wordpress_server (local-exec): 	WordPress Instance
aws_instance.wordpress_server (local-exec): ----------------------------------------------
aws_instance.wordpress_server (local-exec): ===============================================
aws_instance.wordpress_server: Creation complete (ID-0160d3a8843518a4a)
--------------------------------------------------------
