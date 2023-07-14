# Docker Compose 
  - Compose is a tool for defining and running multi-container Docker applications.
  - With Compose, you use a YAML file to configure your application’s services.
  - Then, with a single command, you create and start all the services from your configuration.
  - Here are the key steps :
    1) Define `Dockerfile` for your app’s environment.
    2) Define `docker-compose.yml` for the services that make up your app services.
    3) Run `docker-compose up` and Compose starts and runs your entire app.

## 7.1 Docker Compose Installation
   - On Amazon Linux 2 VM
     ```
     # Copy the appropriate docker-compose binary from GitHub:
     sudo curl -L https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m) \
     -o /usr/local/bin/docker-compose

     # To get the latest docker compose version 
     sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) \
     -o /usr/local/bin/docker-compose

     sudo mv /usr/local/bin/docker-compose /usr/bin/docker-compose
     
     # Update the permission of executable
     sudo chmod +x /usr/local/bin/docker-compose

     # Verify success
       docker-compose version
     ```
   - [On CentOS](https://docs.docker.com/compose/install/)
   - [On Ubuntu](https://docs.docker.com/compose/install/)
   - [On Windows](https://docs.docker.com/compose/install/)
   - [On Mac](https://docs.docker.com/compose/install/)
     
## 7.2 The `docker-compose.yml` file explained
   - In `docker-compose.yml` file, we need to specify the version of the Compose file, at least one service, and optionally volumes and networks.
   - Structure of the `docker-compose.yml` file is as follows:
     ```
      version: "3.x"
      services:
        ...
      volumes:
        ...
      networks:
        ...
     ```
   - Let's see what these elements actually are.
     1) <b>*Version*</b>:
     2) <b>*Services*</b>
        - Services refer to the container's configuration.
        - For example, let's take a dockerized web application consisting of a front end, a back end, and a database.
        - We'd likely split these components into three images, and define them as three different services in the configuration:
          ```
          services:
            frontend:
              image: custom-node-app
              ...
            backend:
              image: my-springboot-app
              ...
            db:
              image: postgres
              ...
          ```
     3) <b>*Volumes*</b>
        - Volumes are physical areas of disk space shared between the host and a container, or even between containers.
        - In other words, a volume is a shared directory in the host, visible from some or all containers.
     4) <b>*Networks*</b>
        - Networks define the communication rules between containers, and between a container and the host.
        - Common network zones will make the containers' services discoverable by each other.
 
## 7.3 `docker-compose.yml` - *Services* Deep Dive
   1) <b>Pulling an Image</b>
      ```
      # If you've already published image in the registry (DockerHub), refer to it with the IMAGE attribute
      services: 
      my-service:
        image: ubuntu:latest
        ...
      ```
   2) <b>Building an Image</b>
      ```
      # To build an image from the source code by reading its Dockerfile, use BUILD attribute
      services: 
      my-custom-app:
        build: /path/to/dockerfile/
        ...
      ```
      ```
      # You can also use the URL instead of path
      services: 
      my-custom-app:
        build: https://github.com/my-company/my-project.git
        ...
      ```
      ```
      # You can specify an image name in conjunction with the build attribute,
      # which will name the image once created, making it available for use by other services
      services: 
      my-custom-app:
        build: https://github.com/my-company/my-project.git
        image: my-project-image
        ...
      ```
      
   3) <b>Configuring the Network</b>
   4) <b>Setting Up the Volume</b>

## 7.4 `docker-compose.yml` - *Environment Variables* in action

## 7.5 Scale the Containerized App through the `docker-compose scale`

## 7.6 Docker Compose Commands
   - Deploy the application
     ```
     # Create and start the Containers, Networks, and the Volumes defined in the configuration
     docker-compose up

     # Run the application in the background as a daemon when launched with the -d option
     docker-compose up -d

     # Docker Build + Docker Run
     docker-compose up --build
     ```
   - Start the Application Containers
     ```
     # After the first time, you can simply use 'start' to start the services
     docker-compose start

     # If docker compose config file has a different name than the default one (docker-compose.yml), you can use -f or ––file flags to specify an alternate file name
     docker-compose -f custom-compose-file.yml start
     ```
   - Stop all the containers in an Application
     ```
     docker-compose stop
     ``` 
   - Scale the Application
     ```
     Syntax: docker-compose scale <service name> = <no of instances>
     Example: docker-compose scale redis-master=3
     ``` 
## 7.7 Real World Application
