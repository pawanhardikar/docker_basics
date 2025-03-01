# Docker

Docker is a Virtualization software that packages applications with all dependencies, configuration, system tools in a container to help run the application on any system.

## Using Docker

Using Docker, it creates its own isolated environment.
We just have to run each container to use any particular services.
Because of this isolation, it is easier to run different versions of the same application without any conflicts.
Now the operations team doesn't need to set up anything except the Docker runtime to run the docker containers/artifacts on the server in order to run the application. The development team provides a docker container to the operations team that contains everything required to run the application.

Docker virtualizes the OS Application Layer where it installs other applications on top of it and it uses the Kernel of the host OS instead of creating its own OS Kernel like the VMs. Hence the size of docker images/packages is small compared to that of VMs.
Linux-based Docker images cannot run on Windows kernel. To overcome this, they came up with Docker Desktop.
Docker Desktop basically uses a hypervisor layer with a lightweight Linux distro, enabling us to run Linux-based docker images on Windows and MAC.

## When I Install Docker Desktop We Get the Following:

1. **Docker Engine:** It is a server with a long-running daemon process called Dockerd, and it is used to manage images and containers.
2. **Docker CLI:** To interact with Docker Server, it can be used to start, stop containers, and basically play with them.
3. **Docker GUI Client:** If the user is not comfortable with CLI, they can use the clean GUI Client to interact with the server to play with Docker.

## Docker Images vs Docker Containers

### Docker Images:

The docker image is nothing but an executable application artifact that is uploaded to the artifact repository. It contains everything that is required to run the application, such as the source code, the dependencies, the environment variables, the files, the file structure, directories, etc.

### Docker Containers:

The Docker image that is downloaded into the server or the local environment where we intend to run the application has to be run to use it. So Docker container is nothing but a running instance of an image.
We can run multiple containers from a single image.

## Commands to Use in Docker CLI:

- To check the list of images in the system: `docker images`
- To check if there are any running containers: `docker ps`

## Docker Registries:

A storage and distribution system for docker images.
There are official images available from applications like Redis, Mongo, Postgres, which we can use in our application by running these images as they are genuine and maintained by the software authors.
We can find these in Docker Hub, which is hosted by Docker itself and is the biggest Docker Registry currently.

As there will be new versions of any technologies, there will be new images created for each version. These are called image "tags."
If we want the latest version without any specific version, we can choose the image with the tag named "latest."

## How to Pull an Image from Docker Hub and Use it in Our System:

- Use the command: `docker pull {image_name}` (This will download the latest version of the image if the tag is not mentioned).
- If we need to pull a specific version, we need to use this command instead, where the tag is specified. This is the most common practice in most cases: `docker pull {image_name}:{tag}`

## How to Run Any Image that is Present in the System:

- Use the command: `docker run {image_name}` -> By running this image, the container starts, and we can check it using the `docker ps` command.
  - To make the container stop, we can use the `exit` command.
  - Running this command will block the terminal, so we cannot run any other commands in the same terminal. To overcome this, we can run the image in detached mode, so it runs in the background by simply using the `-d` attribute before the image name. (For EX: `docker run -d {image_name}`)
  - The terminal won't be blocked, but if we want to see the logs that can be used for debugging if the image is running correctly or not, we need the logs command: `docker logs {container_id}`
  - Container ID can be obtained by checking all the active containers in the system (`docker ps`).
  - To stop the container, we can use the command: `docker stop {container_id}`
  - inorder to start the container we can use the command: `docker start {container_id}` This can be done when I want to restart any previous stopped container. Or else we can normally use the command `docker run {image_name}` to start a new container.
  - Every time we start a container a random name is assigned to it, We can change the name according to our desire using the name flag (For EX: docker run --name Shri_Ganesha -d -p 9000:80 nginx:1.23) 
## Port Binding: Why is This Done?

In the above scenarios, we tried to run an image but we won't be able to access it as the application inside the container runs in an isolated Docker network and not in the host network. So we need to expose the container port to the local port. By binding that port to a port in the local machine, we will be able to access it.
This is done using the command: `docker run -d -p{host_port}:{container_port} {image_name}`

## Registry vs Repository

A registry is a service providing storage for different repositories. Ex. AWS ECR, Docker Hub
A repository is collection of related images with same name but different versions/tags.

## What is a Dockerfile?
Dockerfile is a text document that contains commands on how to assemble an image.
Docker then build an image reading those instructions.

Basic Structure of Dockerfile: 
	Dockerfiles start from a parent image or the "base image".
	Dockerfiles "must begin" with a FROM instruction. and end with "CMD" instruction.
	The CMD is the instruction that is to be exceuted when a Docker container starts.
	There can only be one "CMD" instruction in a Dockerfile
	
	


 


## Things to Explore Later:

- Hypervisor Layer
- Linux Distro
- What is Nginx and why is it used?
