# Docker Installation Guid#

## 1)	Docker Download and Install

  Fallow the instruction of below link for the docker installation -
  - https://docs.docker.com/engine/install/

 ## 2)	For the window setup WSL2

  Enable the WSL 2 feature on Windows. For detailed instructions, refer to the Microsoft documentation given below -
  - https://docs.microsoft.com/en-us/windows/wsl/install

## 3)	Destro Setup on the windows System

   **Follow the below instruction** – Recommended Ubuntu 20.04.4 LTS
  - https://docs.docker.com/desktop/windows/wsl/

## 4)	Docker Setup Details:

  - `Docker Folder:` It has the Docker file for all the containers except the main container that is Docker.developmet, it is on the root folder, to add any new container create the folder and add your Dockerfile and setting related files.
  - `etc Folder:` Configuration related settings like Apache vhost.conf or php.ini related setting will be here.
  - `Html Folder:` Main application code will be here and for the multiple application you can create add php application here and configure vhost in the /etc/vhost.conf file, Sample setup is already there.
  - `Mysql_data & mongo_data:` Used for the volume for the mysql and mongodb
  - `.env:` Common  configuration for the docker will be in env file
  - `Docker-compose.yml:` If need more container you can add the container here or if you need to remove unused container then also you can remove it from the yml file.

## 5)	Installation
  Open CMD/Terminal and execute the below command in the `<D://<folderName>/<folderName>/app` folder (app may be any folder the mandatory thing is that you should have the `docker-compose.yml` file in the same folder)

    $ docker-compose build # It will take some time to download all the images from docker hub
    $ Docker-compose up -d # It will up all the services listed in the yml file 

  To test use `http://app-local.com` or `http://localhost/`

## 6)	What you will get

  - Apache 2.4
  - PHP 7.4 – If you required 8 then you have to update the Dockerfile.development

      ```sh
      FROM webdevops/php-apache-dev:7.4
         To
      FROM webdevops/php-apache-dev:8.1       
      ```
      `Note:` It has almost all useful extension
 - 	Mysql 8
 -	Redis
 - 	Mongodb
## 7)	Important Points to be care:

  -	**Slow Application:** If you php application code is mounted in the docker container for the window then it will slow your website performance, so it is important that you put your all application code inside the container or best one is that it should be in the Linux environment.
  -	But don’t worry you can access directly by using
           `\\wsl$\Ubuntu-20.04\home\<username>\`
  -	To connect mysql database host will be the link name as in the file `docker-compose.yml`
   ```sh
  For Example Mysql Connection:
             Host: mysql   #not localhost
             Username: MYSQL_USER (as in env variable)
             Password: MYSQL_PASSWORD (as in env variable)
  ```
  **Same for the mongo and Redis**
