
# Docker 
---
_Required infrastructure_
- Ubuntu machine
- Permissions to our `docker-lab` repository in Artifactory 

_Required skills_
- Linux concepts
- Basic bash
- Basic git
 
## Intro
Docker is a tool that allows developers, sys-admins etc. to easily deploy their applications in a sandbox (called containers) to run on the host operating system i.e. Linux. The key benefit of Docker is that it allows users to package an application with all of its dependencies into a standardized unit for software development. Unlike virtual machines, containers do not have high overhead and hence enable more efficient usage of the underlying system and resources 
 

## Learning materials 
https://docker-curriculum.com/ 

https://www.youtube.com/watch?v=3c-iBn73dDE 

https://docs.docker.com/develop/develop-images/multistage-build/ - Optional 

 
## Keywords: 
- Container 
- Image 
- Registry 
- Repository 
- Tag 
- Dockerfile
- Docker cli vs dockerd 
- Docker volumes 
- - Bind mount vs named volumes 
- Docker networking 
- - Host 
- - Bridge 
- - None 
- Linux namespaces
- Optional: image layers 

## Commands
- docker run 
- - Options: env, port, mount, interactive, 
- docker image 
- - ls 
- - rm 
- - inspect 
- docker container 
- - ls
- - rm
- - inspect
- docker pull
- docker push
- docker build
- docker login

## Questions 

1. What is containerization? 
2. What is the difference between virtualization and containerization 
3. What Linux features are used in containerization?  
4. Why should I use docker ?  
5. How do you get the number of containers running, paused and stopped? 
6. How to delete a stopped container? () 
7. How to delete an image from the local storage system? 
8. What is docker volume – when you need to use it ?  
9. What is the difference between bind mount and named volumes? What is the pros and cons of each? 
10. Can I configure a docker container to restart when docker service starts ? If so how ?  

## Exercises 

### Exercise 1 – Basic commands 

1. Install docker in your machine - https://docs.docker.com/engine/install/ubuntu/ 
2. Pull the `ubuntu:20.04` image to your machine. 
3. Run a container of the image you just pulled. 
4. List all running containers.  
a. Where did it go?  
b. How can you keep the container running? 
6. Run a `ubuntu:20.04` container interactively, and name it `my-ubuntu` (what does inte 
7. Exit from the container. 
8. Now try running the same command again. What’s wrong? 
8. Run `docker container ls`. Where’s the old container? How can you view it? 
9. Delete the old container. 
10. Pull the `redis:latest` image. 
11. Push this image to our Artifactory registry under `docker-lab/<your-name>/redis:latest` 
12. List all images available in the local cache. 
13. Remove the redis:latest image 

### Exercise 2 – Mounts 
1. Run a `ubuntu:20.04` container, and mount your current directory to `/tmp/docker` in the container.   
a. List the files in the `/tmp/docker` inside the container to make sure you did it right. 
2. Create a volume named `my-vol`   
a. Run a `ubuntu:20.04` container and mount the `my-vol` volume to `/data` in the container    
b. Write some text to a file in this path   
c. Exit the container   
d. Run another container and mount this volume to `/config`, and check you have the file there. 


### Exercise 3 – Building images 
Clone the following repo: https://github.com/lachie83/croc-hunter 

1. Build the image from the Dockerfile, and name the image `croc-hunter:1.0` 
2. Create a Dockerfile and build an image that does the following: 
- Use ubuntu as parent image  
- Install dnsutils 
- Add a text file from your local folder 
- Cat the file when you run it   

## Further learning
- Multistage Dockerfiles 

- Lots of exercises - https://www.katacoda.com/loodse/courses/docker 

- Best practices - https://sysdig.com/blog/dockerfile-best-practices/ 

 