# Docker Project : Two Tier Architecture

## Introduction
I have finished docker training under **IIEC-RISE 1.0** under the mentorship of **Vimal Daga Sir** and this is a final project 
about how we can use docker to implement **Multi Tier Architecture**.
In this particular example I have made a **Two Tier Architecture** having
  * 1. Web Tier : It is the Front end and can be accessed openly through the internet
                  Softwares used : Apache and PHP            
  * 2. Database Tier : A dynamic website requires a database support and it can be accessed through the web server only.
                  Software used : MySQL. 
I have built this in a **Single Server Architecture**

![Single_Server](https://www.codeproject.com/KB/applications/1262641/Single_Server_-_Two_Tier.png)

## Project Description

## 1. Pulling The Images:
For this project I have used mysql:latest and php:7.4-apache images from docker hub.To pull these images run
`docker pull mysql:latest` and `docker pull php:7.4-apache`

## 2. Launching The Containers:
Since our web server is dependent on the database server so we have to launch the database server first and for this run
`docker run -dit -e MYSQL_ROOT_PASSWORD =rootpass -e MYSQL_USER = user -e MYSQL_PASSWORD = password -e MYSQL_DATABASE = mybd -v mysql_st:/var/lib/mysql -p 6033:3306 --name mysql mysql:latest`after that launch the web server by running `docker run -dit -v php:/var/www/html -p 8080:80 --name php74 --link mysql php:7.4-apache`
Now both the servers are up.

## 3.Connectivity
Now the PHP to connect with the MySQL database we need to install the php extention pdo and pdo_mysql. Then inside php folder 
create an index.php file and run this code:
```
<?php

try{
        $con = new PDO("mysql:host=localhost:6033;dbname=mydb","user","password");
        echo "Connected";
}catch(PDOException $e){
        echo "error".$e->getMessage();
}

?>
        
```
After this if  we browse http://localhost:8080 the site will show Connected if the connection is made successfully and if not it will raise an exception.

## 4. docker-compose :
This whole architecture can be made in one command `docker-compose up` if we create the **Infrastructure as Code** using docker-compose.For this we first need to install docker-compose, it does not come installed with docker.
For installing docker-compose we can refer to this [page](https://docs.docker.com/compose/install/)

