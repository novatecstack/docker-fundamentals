# 8.1 Docker Swarm Overview

<img src="https://user-images.githubusercontent.com/121426292/233589481-05a5282c-7186-41a6-bfa3-b4ec329a3948.png" width="300" height="250">

  - Docker swarm is a container orchestration tool, meaning that it allows the user to manage multiple containers deployed across multiple host machines.
  - It helps end-users in creating and deploying application in a cluster of Docker nodes (virtual or physical machines).
  - Each node of a Docker Swarm is a Docker daemon, and all Docker daemons interact using the Docker API. 
  - Each container within the Swarm can be deployed and accessed by nodes of the same cluster. 
  - Some other open source orchestration solutions are: <b>*Docker Swarm, Kubernetes, Apache Mesos, OPENSHIFT, Nomad etc.* </b>
  - Current versions of Docker include swarm mode for natively managing a cluster of Docker Engines called a swarm
  - Use the Docker CLI to create a swarm, deploy application services to a swarm, and manage swarm behavior

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
   2) <b>*Service*</b>
      - The tasks defined by a swarm administrator that a manager or agent nodes must perform.
      - It also defines which container images the swarm should use and which commands the swarm will run in each container.
   3) <b>*Manager Node*</b>
      - The primary function of Manager node is to assign tasks to Worker nodes in the swarm.
      - It also help to carry out some of the managerial tasks.
   4) <b>*Worker Node*</b>
      - Worker nodes run tasks distributed by the manager node in the swarm.
      - Each worker node runs an agent that reports back to the master node about the state of the tasks assigned to it, so the manager node can keep track of services and tasks running in the swarm.
      - By default, all manager nodes are also worker nodes and are capable of executing tasks when they have the resources available to do so.
   5) <b>*Leader Node*</b>
      - When a cluster is formed, the <b>*Raft Consensus Algorithm*</b> is used to assign one of the node as the <b>*Leader node*</b>.
      - The leader node makes all of the swarm management and task orchestration decisions for the swarm.
      - If the leader node becomes unavailable due to an outage or failure, a new leader node can be elected using the Raft consensus algorithm.

## 8.4 Setting up the Docker Swarm cluster - Installation & Config
   - For this lab, I will create 3 VM Instance in AWS/Azure/GCP - 1 Manager and other 2 Worker nodes. Make sure that all the VMs are in the same region and same virtual network
   1) Install Docker on all the nodes and make sure the docker daemon is running.
   2) Networks Specifications
     You need the following ports open to traffic to and from each Docker host participating on an overlay network:
     1) TCP port 2377 for cluster management communications
     2) TCP and UDP port 7946 for communication among nodes
     3) UDP port 4789 for overlay network traffic
   3) docker swarm init --advertise-addr <manager_ip>
