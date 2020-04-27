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
~ docker pull mysql:latest 
~ docker pull php:7.4-apache



