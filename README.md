# troubleshooting-and-tutorials
helpful tips to how to troubleshoot common issues and how to do certain things

# RUNNING ANSIBLE PLAYBOOK FROM JENKINS
- Installing Ansible on Jenkins
- Installing Ansible plugin in Jenkins UI
- Creating Jenkinsfile from scratch.
- - Note: Ensure that Ansible runs against the Dev environment successfully.
 
Tutorial to guide through the step: 
  -  https://www.youtube.com/watch?v=PRpEbFZi7nI

Tutorial on configuring nginx and php on RHEL/CENTOS server: 
  -  https://www.linuxhelp.com/how-to-test-the-php-configuration-on-apache-and-nginx-web-servers-in-centos-7-6
  -  https://www.youtube.com/watch?v=gd1y6vFGW9w&t=2

Tutorial to install php 7.4
  -  https://computingforgeeks.com/how-to-install-php-7-4-on-centos-rhel-8/

Commands to dynamically set hostname, domain name and IP address to config files:
  -  server_IP {{ ip_address }};
  -  domain: {{ ansible_nodename }}
  -  hostname: {{ansible_default_ipv4.address}}

Tutorial to redirect www or http to non www and https and vice versa
  -  https://phoenixnap.com/kb/redirect-http-to-https-nginx

Tutorial to set up let's encrypt on Ubuntu with auto cert renewal
  -  https://www.digitalocean.com/community/tutorials/how-to-secure-nginx-with-let-s-encrypt-on-ubuntu-20-04

Tutorial to set up let's encrypt / certbot on Rhel server
  -  https://www.cyberithub.com/how-to-install-lets-encrypt-certbot-on-rhel-centos-8/

Tutorial to configure nginx as gateway for multiple servers
  -  https://www.technhit.in/configure-nginx-as-gateway-for-multiple-servers/
  > Note: Only the IP address of the reverse proxy server will be added to the DNS A record of the domain. The rest of the work happens inside the proxy server. Remember to update your hosts file to include the public IP address of the servers and their domains.

Tutorial to Install Apache, MySQL, PHP (LAMP) on CentOS/RHEL 7
  -  https://tecadmin.net/install-lamp-apache-mysql-and-php-on-centos-rhel-7/
  >  Remember that php-mysql is for ubuntu while php-mysqlnd is for redhat. Also, when you encounter an error, always try to read the log files of the server to get the actuall reason for the error. The file is usually in /var/log/nginx/error.log.

Tutorial on fixing proxy 502 bad gateway error rhel and maybe ubuntu. Also consider using public IP address for the proxy_pass if private IP still gives the connection to upstream refused error.
  -  https://stackoverflow.com/questions/49597942/load-balancer-on-nginx-give-502-bad-gateway
  -  https://stackoverflow.com/questions/23948527/13-permission-denied-while-connecting-to-upstreamnginx
  -  https://stackoverflow.com/questions/70111791/nginx-13-permission-denied-while-connecting-to-upstream
  -  https://serverfault.com/questions/819423/reverse-proxy-nginx-bad-gateway

Tutorial to enable your server to connect to a database over HTTP(Especially for RHEL server)
  -  https://stackoverflow.com/questions/41178774/connect-database-error-type-2002-permission-denied

Tutorial to print the actual database connection error which should help during debugging
  -  https://www.plus2net.com/php_tutorial/mysqli_connection.php

Tutorial to access the environment variables of the machine which ansible is running from / and also to access the Jenkins environment variables if you are runnimg ansible from jenkins
  - https://docs.ansible.com/ansible/latest/collections/ansible/builtin/env_lookup.html#examples
  - https://github.com/jenkinsci/ansible-plugin/blob/main/README.md
  - https://wiki.jenkins.io/display/JENKINS/Building+a+software+project

    - examples code:
    ```
    ---
    - hosts: test
      name: print workspace
      tasks:
        - name: get workspace
          debug:
            msg: "'{{ lookup('ansible.builtin.env', 'WORKSPACE')}}' is the workspace environment variable"
    ```
Tutorial on How To Install JFrog Artifactory on Ubuntu 20.04 LTS
  - https://computingforgeeks.com/how-to-install-jfrog-artifactory-on-ubuntu-linux/?expand_article=1

Create an EC2 Instance With EC2 User Data Script 
 - https://www.geeksforgeeks.org/create-an-ec2-instance-with-ec2-user-data-script-to-launch-website/

How to save a file in vscode-remote SSH with a non-root user privileges
 - https://stackoverflow.com/questions/56291492/how-to-save-a-file-in-vscode-remote-ssh-with-a-non-root-user-privileges

RHEL/CENTOS Image
 - RHEL-8.2.0_HVM-20210907-x86_64-0-Hourly2-GP2

AWS User Data example
 - https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/user-data.html
  ```
#!/bin/bash
yum update -y
yum install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm -y
yum update -y
yum install -y nginx
systemctl start nginx
systemctl enable nginx
yum -y install wget  
yum install python3 -y
yum install chrony -y
yum install net-tools -y
yum install vim-enhanced -y
yum install telnet telnet-server -y
yum install htop -y
```

Redirect HTTP requests to HTTPS using an Application Load Balancer
 - https://repost.aws/knowledge-center/elb-redirect-http-to-https-using-alb#
 - https://www.youtube.com/watch?v=E5TkqBIB4fY

NGINX configuration to forward request on to AWS load balancers (ELS, ALB)
 - https://stackoverflow.com/questions/69957424/nginx-configuration-to-forward-request-on-to-alb

Amazon AWS EC2 - How to restrict traffic to be received only from Elastic Load Balancer or from Particular instances, even tho their IP addresses are dynamic
 - https://stackoverflow.com/questions/52421576/amazon-aws-ec2-how-to-restrict-traffic-to-be-received-only-from-elastic-load-b
 - https://stackoverflow.com/questions/49227466/aws-instance-only-allow-traffic-from-load-balancer
 - https://stackoverflow.com/questions/45416882/aws-security-group-include-another-security-group
 - https://docs.aws.amazon.com/vpc/latest/userguide/security-group-rules.html

How To Create a Self-Signed SSL Certificate for Apache on CentOS 8
 - https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-apache-on-centos-8

How To Create a Self-Signed SSL Certificate for Nginx on CentOS 7
 - https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-nginx-on-centos-7

How To Create a Self-Signed SSL Certificate for Nginx in Ubuntu 20.04
 - https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-nginx-in-ubuntu-20-04-1

How To Create a Self-Signed SSL Certificate for Apache in Ubuntu 20.04
 - https://www.digitalocean.com/community/tutorials/how-to-create-a-self-signed-ssl-certificate-for-apache-in-ubuntu-20-04

AWS Cloud Solution For 2 Company Websites Using A Reverse Proxy Technology 
 - https://github.com/JendyJasper/ACS-project-config
 - https://youtu.be/XhmIBMzss5M

Activating SSH Agent and setting it up for port forwarding
 - https://www.linode.com/docs/guides/using-ssh-agent/

Add a user as a sudo user. You should be able to run any sudo command if you are logged in as vboxuser. replace vboxuser according to your username
   ```
  run su root and enter your password
  run sudo su
  run adduser vboxuser sudo
  then run su vboxuser
  run sudo apt update
  run sudo apt upgrade
  ```

Install softwares using Python PIP command
 - https://stackoverflow.com/questions/62071515/bash-pip-command-not-found-when-using-pip-install

How to Install and Configure AWS CLI on Linux
 - https://devopscube.com/install-configure-aws-cli-linux/

How to troubleshoot github large files error
  -  https://stackoverflow.com/questions/20002557/how-to-remove-a-too-large-file-in-a-commit-when-my-branch-is-ahead-of-master-by
  -----
   ![image](https://github.com/JendyJasper/troubleshooting-and-tutorials/assets/29708657/916b5501-bf28-46a6-a290-dd9ea4ed5bf2)

AWS Architecture Icons and Drawings
 - https://aws.amazon.com/architecture/icons/

Find your dream job abroad or remote
 - https://www.honeypot.io/en/
 - https://vanhack.com/jobs

How to Build AWS VPC Using Terraform – Step By Step
 - https://javatodev.com/how-to-build-aws-vpc-using-terraform-step-by-step/

How to Install Elastic Stack on Ubuntu 22.04 LTS
 - https://www.digitalocean.com/community/tutorials/how-to-install-elasticsearch-logstash-and-kibana-elastic-stack-on-ubuntu-22-04

How to Install Prometheus and Grafana on Ubuntu?
 - https://antonputra.com/monitoring/install-prometheus-and-grafana-on-ubuntu/
