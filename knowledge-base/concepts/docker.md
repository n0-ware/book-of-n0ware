# Docker

## Description
"Docker" generally refers to a compute solution known as a "container." Containers are an excellent choice for deploying infrastructure to to their lightweight and cross functionality via baked in dependencies. Containers in Docker are essentially `.tar` files that contain all the information the container needs to run. 

Containers are stored in "registries." Running `docker images` on a local system will return the information related to any containers on the system that `docker` knows about
- Repository (Name)
- Tag
- Image ID
- Created
- Size

## Installation
### Kali
```
sudo apt update
sudo apt install -y docker.io
sudo systemctl enable docker --now

## To add yourself to the docker group to use without sudo
sudo usermod -aG docker $USER
```

## AWS-ECR

Containers are stored on AWS in a service called [Elastic Container Registry (ECR)](https://aws.amazon.com/ecr/). These containers can be made available publicly or privately. 

Docker images can be obtained remotely via AWS with the command:
```
docker pull public.ecr.<CONTAINER_ADDRESS>:<tag>
```

Run and interact with a docker container with a similar command:
```
docker run -it public.ecr.<CONTAINER_ADDRESSS>:<TAG>
```

Once inside a container, you may interact with it based on the operating system it is running. 