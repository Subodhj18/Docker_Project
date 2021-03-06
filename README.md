# Docker Project 
This is the final project using Docker to set-up a WebApp called Joomla. I will explain you the whole process that has been done for creating the WebApp .
## What's Joomla :-

Joomla is a free and open-source content management system (CMS) for publishing web content. It is built on a model–view–controller web application framework that can be used independently of the CMS. Joomla is written in PHP, uses object-oriented programming (OOP) techniques and software design patterns, stores data in a MySQL, MS SQL, or PostgreSQL database, and includes features such as page caching, RSS feeds, printable versions of pages, news flashes, blogs, search, and support for language internationalization.

## 1. Pre-configurations:
You should have an OS installed in your system. In that OS you should have to install Docker
Here I am using RedHat Enterprise Linux OS and I have installed Docker Community Edition in it.

## 2. Set-Up & Requirements:
Disable Filrewall: Disabling firewall is not a good choice but, whenever you try to run any network based service then the firewall may block it and the service won't work properly. So, you have to disable firewall for implementing network based services to system.
Use the following command to stop firewall systemctl stop firewalld
Use the following code to disable the firewall permanently until you start it systemctl disable firewalld
You can check the status of firewall by command systemctl status firewalld
Use the following command to start firewall systemctl start firewalld

## 3. Run Docker:
For moving towards the project we have to enable docker service in the system so that we can use it. To start docker, use command systemctl start docker You can use this command to enable docker permanently systemctl enable docker You can check the status of docker by command systemctl status docker To stop docker, use command systemctl stop docker

## 3. Downloading required images:
Pulling MySQL Image:
Use docker pull mysql:5.7 to download the mysql version 5.7 image to use as a database server.
Pulling Joomla Image:
Use docker pull joomla:3.9-php7.2-apache to download the Joomla Image in which php and apache server is already preconfigured.

To know more about MySQL Image go to this page: https://hub.docker.com/_/mysql
To know more about Joomla Image go to this page: https://hub.docker.com/_/joomla

## 4. Setting up MySQL:
Use the code given below and it will create a user with a database inside Your MySQL Server. docker run -it -e MYSQL_ROOT_PASSWORD=(password of your choice) -e MYSQL_USER=(username you have given) -e MYSQL_PASSWORD=(password you have given) -e MYSQL_DATABASE=(name of the database) --name joomladb mysql:5.7

You can see your database is created or not by using the client software known as MySQL Client Software yum install mysql

## 5. Docker-Compose:
Docker compose software can be configured by using command vim docker-compose.yml
Remember
The file name should always be docker-compose.yml.
For reference you can visit to the website: https://docs.docker.com/compose/install/

### Version:
I have used V3(version 3) for docker-compose because it's easy to compose than the other versions.

### Volumes set-up:
If you want to make your data permanent then you have to use docker valume. We make our data permanent because if we quit the container then all the data inside container will be destroyed. This means, due to any reason if our container gets terminated our data will not loose.
### Environment:
There are many images in Docker which needs some pre-defined environment variables to run. That's why we need to pass these variables.

### Dependencies:
For running Joomla it needs MySQL database server to store the files.

### Ports:
For running the WebApp we have to expose our container to a specific port. WebApp can only be accessible outside the system if we provide it a specific port.

## 6. Docker-compose up:
For docker compose up, use command docker-compose up to complete the setup.

## 7. Running Joomla WebApp:
Open the browser and type localhost:80 or localhost in the address bar and you will be able to see your Joomla WebApp.
Note:
If you want to use any other port then you have to mention it in your docker-compose file.
