# Jenkins Server Setup

**https://www.geeksforgeeks.org/how-to-setup-jenkins-in-docker-container/**

**1. Create EC2 AWS > Save file .pem**

**2. Setting Inbound Rules**

![Inbound Rules](/assets/inbound-basic-ec2.PNG "Inbound Rules")

**3. SSH to EC2 instance**

**4. Install Docker**

sudo yum update -y   &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;# To update all packages

sudo amazon-linux-extras install docker        	&emsp;&emsp;# To install docker latest version

sudo service docker start  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;# To start docker service

sudo service docker status     &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;# To check status of docker service. If it's running or not.

sudo systemctl enable docker     &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;# To ensure that docker service start after each reboot 

sudo usermod -a -G docker ec2-user      &emsp;&emsp;&emsp;&ensp;# To add ec2-user to docker group

docker  -v  

**5. Pull the Jenkins image using docker**

docker pull jenkins/jenkins:latest       	&emsp;&emsp;# To pull the image of jenkins

docker images  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;# To see if image is downloaded or not

mkdir jenkins &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;#To make directory name jenkins 

docker run -d --name jenkins -p 8080:8080 -v $PWD/jenkins/ jenkins/jenkins      &emsp;&emsp;# To run a container name jenkins using jenkins image 

docker ps  

**6. Copy the Public IPv4 address of the EC2 instance**

*http://18.138.34.41:8080*

![URL Jenkins](/assets/url-jenkins.PNG "URL Jenkins")

![First Jenkins](/assets/first-jenkins.PNG "First Jenkins")
**7. Get first password Jenkins**

docker logs jenkins     &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;#To see logs of the container name jenkins

![Password Jenkins](/assets/pass-jenkins.jpg "Password Jenkins")

**8. Install all the plugins**

![Install plugins Jenkins](/assets/install-plugins.png "Install plugins")

**8. Create Admin account**

![Login Jenkins](/assets/login-admin.png "Login plugins")