# 8.1 Docker Swarm Overview
  - Docker swarm is a container orchestration tool, meaning that it allows the user to manage multiple containers deployed across multiple host machines.
  - It helps end-users in creating and deploying application in a cluster of Docker nodes (virtual or physical machines).
  - Each node of a Docker Swarm is a Docker daemon, and all Docker daemons interact using the Docker API. 
  - Each container within the Swarm can be deployed and accessed by nodes of the same cluster. 
  - Some other open source orchestration solutions are: <b>*Docker Swarm, Kubernetes, Apache Mesos, OPENSHIFT, Nomad etc.* </b>
<img src="https://user-images.githubusercontent.com/121426292/233589481-05a5282c-7186-41a6-bfa3-b4ec329a3948.png" width="300" height="250">

## 8.2 Container Orchestration tool's main responsibilities
   - Provisioning and deployment of containers
   - Redundancy and availability of containers
   - Cluster management
   - Scaling up or removing containers to spread application load evenly across host infrastructure
   - Movement of containers from one host to another if there is a shortage of resources in a host, or if a host dies
   - Allocation of resources between containers
   - External exposure of services running in a container with the outside world
   - Load balancing of service discovery between containers
   - Health monitoring of containers and hosts
   - Configuration of an application in relation to the containers running it

## 8.3 Docker Swarm: Architecture
   The Swarm architecture includes below components:
   1) <b>*Swarm*</b>: A set of nodes with at least one master node and several worker nodes that can be virtual or physical machines.
   2) <b>*Service*</b>:
      - The tasks defined by a swarm administrator that a manager or agent nodes must perform.
      - It also defines which container images the swarm should use and which commands the swarm will run in each container.
   3) <b>*Manager Node*</b>:
   4) <b>*Worker Node*</b>:

## 8.2 Docker Swarm: Key Terminologies
  - Docker container 
  - Docker daemon
  - Docker images 
  - Docker client 
  - Docker registry 
  
