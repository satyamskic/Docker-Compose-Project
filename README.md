# Docker-Compose-Project

Hi , I'm **Satyam Kumar**



I have successfully completed the **Docker Training**  (Part of devops) under guidance of **Vimal Daga sir**.





# My project
I created project based on **Ghost** which is open source **blogging platform**.I created my project inside Docker container on **REDHAT-8 Enterprise Linux** but you can use any OS but few commands might not work properly. I'll also show you how to setup for create this project but before it i would like to give you quick introduction about ghost...........




# What is ghost and Why we need it ??

Ghost is a **NodeJS** module for creating Blogs something like WordPress. It's initial release was on **Octorber 2013**, and was **John O'Nolan**. Ghost is built using NodeJS, which means it is a lot faster then typical PHP server or WordPress.
It uses popular express that is it's server and for a database you can select between **SQLite** or **MySQL**. It also has a nice templating enginer called **Handlebars**. In order to word with ghost you just need to know **Markdown**, thats it, nothing else,and if you want to develop application or plugins then you need to know **JavaScript**.


# Steps you have to follow to setup Environment
1. First disble/stop **firewall** security in your operating system because it block some network stuffs. But remember that it is not good practice to disabling/stoping security, For stoping firewalld use command 
     - `systemctl stop firewalld`
2. Start your Docker
     -  `systemctl start docker`
3. Add images of **MySQL** and **Ghost** in your **Docker**. For this....use these commands given below
      -  `docker pull mysql:5.7`
      -  `docker pull ghost:1-alpine`
4. After this, you need to use these images. How can we these images, let's discuss.........

# How to use mysql image
**What is MySQL?**
- MySQL is the world's most popular open source database. With its proven performance, reliability and ease-of-use, MySQL has become the leading database choice for web-based applications, covering the entire range from personal projects and websites, via e-commerce and information services, all the way to high profile web properties including Facebook, Twitter, YouTube, Yahoo! and many more.

For more information and related downloads for MySQL Server and other MySQL products, please visit www.mysql.com.

**Start a mysql server instance**
Starting a MySQL instance is simple:
- ``$ docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag``
### Environment Variables
When you start the mysql image, you can adjust the configuration of the MySQL instance by passing one or more environment variables on the docker run command line. Do note that none of the variables below will have any effect if you start the container with a data directory that already contains a database: any pre-existing database will always be left untouched on container startup.
**MYSQL_ROOT_PASSWORD**
- This variable is mandatory and specifies the password that will be set for the MySQL root superuser account. In the above example, it was set to my-secret-pw.

**MYSQL_DATABASE**
- This variable is optional and allows you to specify the name of a database to be created on image startup. If a user/password was supplied (see below) then that user will be granted superuser access (corresponding to GRANT ALL) to this database.

**MYSQL_USER, MYSQL_PASSWORD**
- These variables are optional, used in conjunction to create a new user and to set that user's password. This user will be granted superuser permissions (see above) for the database specified by the MYSQL_DATABASE variable. Both variables are required for a user to be created.

Do note that there is no need to use this mechanism to create the root superuser, that user gets created by default with the password specified by the MYSQL_ROOT_PASSWORD variable.

**MYSQL_ALLOW_EMPTY_PASSWORD**
- This is an optional variable. Set to yes to allow the container to be started with a blank password for the root user. NOTE: Setting this variable to yes is not recommended unless you really know what you are doing, since this will leave your MySQL instance completely unprotected, allowing anyone to gain complete superuser access.

**MYSQL_RANDOM_ROOT_PASSWORD**
- This is an optional variable. Set to yes to generate a random initial password for the root user (using pwgen). The generated root password will be printed to stdout (GENERATED ROOT PASSWORD: .....).

**MYSQL_ONETIME_PASSWORD**
Sets root (not the user specified in MYSQL_USER!) user as expired once init is complete, forcing a password change on first login. NOTE: This feature is supported on MySQL 5.6+ only. Using this option on MySQL 5.5 will throw an appropriate error during initialization.

### General syntax of MySQL
- `docker run -it -e MYSQL_ROOT_PASSWORD=(any password you like) -e MYSQL_USER=(any user name) -e MYSQL_PASSWORD=(any password(recommended not to use root password) -e MYSQL_DATABASE=(any database name) --name dbos(give any container name) mysql:5.7`
##### Note:- 
1. you need MySQL client to login inside MySQL database then you can install it by using yum/dnf command
- `dnf install mysql`
2. For cheaking your IP of MySQL use this command
- `docker inspect mysql | grep IP`                 
3. Use this command to login inside database
- `mysql -h **Ip_Of_MySQl** -u **ghost** -p**redhat**`     
### MySQL Volume
It is always good practice to creating volume of MySQL because it store the data permanent(persistent). If any case you deleted container but you won't loose your databases. 
Create a data directory on a suitable volume on your host system, e.g. /my/own/datadir.

Start your mysql container like this:

  - `$ docker run --name some-mysql -v **/my/own/datadir:/var/lib/mysql** -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag`

The **-v /my/own/datadir:/var/lib/mysql** part of the command mounts the **/my/own/datadir** directory from the underlying host system as **/var/lib/mysql** inside the container, where MySQL by default will write its data files.

# USe of ghost image
**What is ghost**

Ghost is a free and open source blogging platform written in JavaScript and distributed under the MIT License, designed to simplify the process of online publishing for individual bloggers as well as online publications.

wikipedia.org/wiki/Ghost_(blogging_platform)

### Configuration

All Ghost configuration parameters can be specified via environment variables. See the **https://ghost.org/docs/concepts/config/#section-running-ghost-with-config-env-variables** for details about what configuration is allowed and how to convert a nested configuration key into the appropriate environment variable name:

### Note
To know more about ghost please visit site given below

**https://hub.docker.com/_/ghost**


# Docker compose up
```
If you want that whenever you want Ghost service locally then you have to write all code again and again, In case of crash or stop working service due to any cause then you have to again write full command or code and again launch service . But this problam can be solved very easily. We can launched both MySQL as well as ghost by one click................... for this , you have to create a file named as *docker-compose.yml* and write your code inside it and run this file by using this command 
```
   - `docker-compose up`  
  
  
  
  Looked this images carefully..................................
  
  ![]( https://github.com/satyamskic/Docker-Compose-Project/blob/master/3.png)
 
### Note
You can create and edit this file using vim editor. For that use `vim docker-compose.yml` . Remember the file name should always be docker-compose.yml.

**To varify that your services running or not, open new window terminal and type command given below**
   
    - docker ps






Looked this images carefully..................................
![](https://github.com/satyamskic/Docker-Compose-Project/blob/master/4.png)



**To access ghost service cheak your IP address of your base OS and go to browser and type *IP_OF_BaseOS:PORT.No* and access your service**
1. Cheak your IP by this command
  
     - `ifconfig enp0s3`
2. Go to browser( like google crome or firefox ) and access

Looked this images carefully..................................

   ![](https://github.com/satyamskic/Docker-Compose-Project/blob/master/6.png)
   

3. It will show like this

Looked this images carefully..................................

   ![](https://github.com/satyamskic/Docker-Compose-Project/blob/master/7.png)
   
   
   ![](https://github.com/satyamskic/Docker-Compose-Project/blob/master/8.png)
   
   
   ![](https://github.com/satyamskic/Docker-Compose-Project/blob/master/9.png)
 






## How to write docker-compose.yml file 

![](https://github.com/satyamskic/Docker-Compose-Project/blob/master/1.png)


**version:**
  - In each version the style and syntax are different. I used version 3.1 cause it's easy to compose than other versions and you have to mention it within sigle cote

**services:**
 
  - In docker-compose.yml file we have to write all services which we want to run by one click only.

**container name:**
  
  - I choose dbos and ghost as name of containers. You can choose your desire name . Docker-compose automatically the name for the containers using our defined container name.

**image and restart:**
  
  - Image and restart these two key is used to specify which image we want to use and due to any reason if any of the container stops docker-compose will again restart it.

**volumes:**
  
  - In docker as soon as we terminate an container our whole data inside that container destroyed. But if we want to make our data permanent then we have to use docker volume. Using the last volumes key we at first created two volumes. We know that MySQL and ghost stores their data inside which folder. We simply make those folders permanent by mounting these volumes. That means due to any reason if our container terminated our data will not loose.

**environment:**
  
  - There are many images in Docker which needs some pre-defined environment variables to run. That's why we need to pass these variables.
Before launch the servies behind the scence, docker-compose runs first script you pass inside environment varriable then it starts our services.

**ports**
  
  - When we go to browser any try to access our service(like ghost) which is running inside our container, then by default it works at port number 2368 but client or You can't access the directly because service is running inside container. So you can do one thing, whenever client or you go to port no 8080 (you can choose any port no between 1 to 65000 ) so 8080 -> 2368 ( 8080 connect to 2368 ) .Port number use when multiple programs runs over same IP address. the best way to understand port is to think of the postal system.







### HOPE IT IS HELPFUL

# THANK YOU








  
