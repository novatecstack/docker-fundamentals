# Docker Compose
  - Compose is a tool for defining and running multi-container Docker applications.
  - With Compose, you use a YAML file to configure your application’s services. Then, with a single command, you create and start all the services from your configuration.

## 7.1 The `docker-compose.yml` file explained
   - In `docker-compose.yml` file, we need to specify the version of the Compose file, at least one service, and optionally volumes and networks.
   - Structure of the compose file is as follows:
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
 
## 7.2 `docker-compose.yml` - *Services* Deep Dive
   1) Pulling an Image
   2) Building an Image
   3) Configuring the Network
   4) Setting Up the Volume

## 7.3 `docker-compose.yml` - *Environment Variables* in action
