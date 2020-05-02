# Docker Project
I don't want to install PHP on my local machine so this is the perfect use case for Docker! In this Quick Hit, I will describe how to create a containerized PHP + MySQL + PhPMyAdmin development environment using Docker Compose.

On a single tap, your whole environment gets 

I have build this infrastructure in RHEL 8. In this project, there will be 3 docker containers running 
1. MySQL : 5.7
2. PHP : 7.2
3. phpMyAdmin

phpMyAdmin was created so that users can interact with MySQL through a web interface.

## Getting Started
Get ready with the following stuff before diving into docker-compose.yml file.

```bash
.
├── docker-compose.yml
└── php
    └── index.php
```
## Installing Software
 - **Installing Docker:** 
 
    - Add the following link to your local repository
    
      ```bash
      https://download.docker.com/linux/centos/7/x86_64/stable/
      ```
    - run  ``` yum install docker-ce --nobest ``` to download and install docker community edition (NOTE: If your O.S is RHEL).
    
    - ```start``` the docker services using ``` systemctl start docker ``` command in terminal.
    
 - **Installing docker-compose:** 
    - Head to the [link](https://docs.docker.com/compose/install/). It will guide you to download and install docker-compose.
    
 - **Installing php:**
    - simply you can run this command ``` yum install php ``` in rhel 8 terminal.
    
## Running the docker-compose :

Docker-Compose allows you to build multi-container web applications. It's the perfect tool to set up a local development environment that replicates your production setup.

Create a directory and paste the given ``` docker-compose.yml ``` file into the directory. In the Terminal, head to the directory using ``` cd directory_name ``` and run:

``` docker-compose up -d ```

❗ Here `-d` is an option to run docker in background. You can omit it if not required. ❗

## Initial Setup :

## Connecting to the database remotely from host :

- Run the following and find the IP address of MySQL container:

  > docker inspect `CONTAINER ID of MySQL`
  
- Run the following to connect to the MySQL database :
  > mysql -h `IP of MySQL` -u `username of MySQLdb` -p`password of MySQLdb`
 
- If your MySQL is correctly working, you will be redirected to `MySQL shell` and you can run commands like `show databases;`, `show tables;`, etc.

![screenshot](https://github.com/Sumitkaroo/Docker/blob/master/images/4.JPG)

## Deploying PHP Webpages :

All the webpages of your web application you can import here `/php`.

 - Create another subdirectory where you have created `docker-compose.yml` file and named as `/php` which contains the following `index.php` file:
 
![screenshot](https://github.com/Sumitkaroo/Docker/blob/master/images/5.JPG)

![screenshot](https://github.com/Sumitkaroo/Docker/blob/master/images/6.JPG)

- For accessing Webpages

  - Go to browser and enter the link: `http://0.0.0.0:80` or `http:ip_address of PHP Container:80`.
To find the `ip_address` of container type `docker inspect docker_id` in terminal where you will find `ip_address` of the container. After entering `ip_address` with `port_number` in the browser you will be directed to `index.php` page.

![screenshot](https://github.com/Sumitkaroo/Docker/blob/master/images/7.JPG)

Notes:

- We use port-forwarding to connect to the inside of containers from our local machine.

- Our local directory, ./php, is mounted inside of the webserver container as /var/www/html/
    - The files within in our local folder will be served when we access the website inside of the container.

## phpMyAdmin

- phpMyAdmin was created so that users can interact with MySQL through a web interface. 

- Go to browser and enter the link: ```http://ip_address:80```. You need to enter ```ip_address``` of ```phpMyAdmin``` docker container. To do this enter `docker inspect docker_id` where you will find ip_address of container. After entering ip_address with port number in the browser you will be directed to `phpMyAdmin` page.

![screenshot](https://github.com/Sumitkaroo/Docker/blob/master/images/2.JPG)

![screenshot](https://github.com/Sumitkaroo/Docker/blob/master/images/1.JPG)

🛑 Note: It is highly recommended to edit the `docker-compose.yml` file and use your own personalised login and password. 🛑

- Finally, you will be redirected to the home page of phpMyAdmin as in the below image :

![screenshot](https://github.com/Sumitkaroo/Docker/blob/master/images/3.JPG)

🛑 Note: Changes which you made in mysql will reflect in phpmyadmin and vice versa. 🛑


## Author :

  > Sumit Karoo
  
  > Gmail: sumitkaroo6699@gmail.com
  
  > https://www.linkedin.com/in/sumit-karoo-268707185/

