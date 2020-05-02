# Docker Project
I have build this infrastructure in RHEL 8. In this project, there will be 3 docker containers running 
1. MySQL : 5.7
2. PHP : 7.2
3. PHPMyAdmin

phpMyAdmin was created so that users can interact with MySQL through a web interface.

## Getting Started
Get ready with the following stuff before diving into docker-compose.yml file.

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
Create a directory and paste the given ``` docker-compose.yml ``` file into the directory. In the Terminal, head to the directory using ``` cd directory_name ``` and run:

``` docker-compose up -d ```

❗ Here `-d` is an option to run docker in background. You can omit it if not required. ❗

## Initial Setup :

- Go to browser and enter the link: ```http://ip_address:80```. You need to enter ```ip_address``` of ```PHPMyAdmin``` docker container. To do this enter `docker inspect docker_id` where you will find ip_address of container. After entering ip_address with port number in the browser you will be directed to PHPMyAdmin page.

![screenshot](https://github.com/Sumitkaroo/Docker/blob/master/images/2.JPG)

![screenshot](https://github.com/Sumitkaroo/Docker/blob/master/images/1.JPG)

🛑 Note: The above screenshot consisting login credentials is just a sample. It is highly recommended to edit the `docker-compose.yml` file and use your own personalised login and password. 🛑
