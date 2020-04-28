# Docker-Compose-Project

Hi , I'm **Satyam Kumar**



I have successfully completed the **Docker**  (Part of devops) training under guidance of **Vimal Daga sir**.





# My project
I created project based on **Ghost** which is open source **blogging platform**.I created my project inside Docker container on **REDHAT-8 Enterprise Linux** but you can use any OS but few commands might not work properly. I'll also show you how to setup for create this project but before it i would like to give you quick introduction about ghost...........




# What is ghost and Why we need it ??

Ghost is a **NodeJS** module for creating Blogs something like WordPress. It's initial release was on **Octorber 2013**, and was **John O'Nolan**. Ghost is built using NodeJS, which means it is a lot faster then typical PHP server or WordPress.
It uses popular express that is it's server and for a database you can select between **SQLite** or **MySQL**. It also has a nice templating enginer called **Handlebars**. In order to word with ghost you just need to know **Markdown**, thats it, nothing else,and if you want to develop application or plugins then you need to know **JavaScript**.


# Steps you have to follow to setup Environment
1. First disble/stop **firewall** security in your operating system because it block some network stuffs. But remember that it is not good practice to disabling/stoping security, For stoping firewalld use command 
 - **systemctl stop firewalld**
2. Start your Docker
-  **systemctl start docker**
3. Add images of **MySQL** and **Ghost** in your **Docker**. For this....use commands given below
-  For MySQL  
  -  **docker pull mysql:5.7**
-  For Ghost
  -  **docker pull ghost:1-alpine**
  
  
