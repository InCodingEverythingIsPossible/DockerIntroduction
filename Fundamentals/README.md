# Docker Introduction


## Docker setup
## -------------------------------------------------
1. Enable virtualization on processor in bios
2. Enable Windows system features
   - Virtual Machine Platform
   - Windows Subsystem for Linux
3. Enter powershell to set default version of wsl
   - Command `wsl --set-default-version 2`
4. Install ubuntu
   - Enter microsoft store
   - Download ubuntu for example Ubuntu 22.04.05 LTS
   - After installation launch Ubuntu
   - Create first user and check if it's works
5. Install docker
   - Install docker from official website of docker
   - During installation checkmark "Install required Windows components for WSL 2"
   - Change assigned resources in C:\Users\{Your_account}\.wslconfig
   - Microsoft tutorial [wsl_config_tutorial](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#configure-global-options-with-wslconfig)


## Useful links
## -------------------------------------------------

### Docker base images
Base images to use inside DockerFile -> [hub_docker](https://hub.docker.com/)  
For example Node version 23 alpine  
Code: `FROM node:23-alpine`

<br>

## Basic commands
## -------------------------------------------------

### Login to docker from ubuntu cli
Docker Desktop must be turn on
Command: `docker login`

### Create container from image
Sample: `docker create {image_name}`  
Command: `docker create {image_name}`

### Start container
Parameter -a watch for output from command without this it will return the container_id    
even if container will have some output for you  
Sample: `docker start -a 9217198`  
Command: `docker start -a {container_id}`

### Create and run container from an image
It does 2 commands in background (create container and start container)  
The only difference is that it returns the output by default and not the container id
Sample: `docker run hello-world`
Command: `docker run {image_name}`

### Create and run container from an image with overriding default commands
!!! Once a container has been created, we cannot substitute the command  
Sample: `docker run busybox ls`  
Command: `docker run {image_name} {command}`

### Retrieve logs from container
Sample: `docker logs 921719831`  
Command: `docker logs {container_id}`

### List all running containers
Command: `docker ps`

### List all containers which were ever created
Command: `docker ps --all`

### Stop running container
Tries to stop the container nicely for 10 seconds, after 10 seconds it kills the container  
Sample: `docker stop afhj329181`  
Command: `docker stop {container_id}`

### Kill running container
Sample: `docker kill afhj329181`  
Command: `docker kill {container_id}`

### Delete all stopped containers
Command: `docker system prune`

### Creation of a container containing the redis database
Redis is open source non-relational database  
Command: `docker run redis`

### Execute an additional command on a running container
Redis-cli give possibility to interact with redis database  
Sample: `docker exec -it f697b66f9abb redis-cli`  
Command: `docker exec -it {container_id} {command}`

### Creation of variable inside redis-cli in the redis database
Sample: `set myvalue 5`  
Command: `set {name} {value}`  
Sample: `get myvalue`  
Command: `get {name}`

### Enter to the cli of the container
Sample: `docker exec -it ca031542ee8b sh`  
Command: `docker exec -it {container_id} sh`

### Creation of docker file (create, build and run)
Creation of an image root directory   
Sample: `mkdir redis-image`  
Command: `mkdir {directory_name}`

Enter to an image root directory  
Sample: `cd redis-image`  
Command: `cd {directory_name`

Open VisualStudio in current directory  
Command: `code .`

Create DockerFile, look in Fundamentals catalog for sample  

Build a image from all files in the current directory  
Command: `docker build .`

Run created image  
Sample: `docker run 329183219`  
Command: `docker run {container_id`

### Tagging image with your own name
**!!! Naming convention below**  
Sample: `docker build -t incodingeverythingispossible/redis:latest .`  
Command: `docker build -t {your_docker_id}/{repo_name}:{version} {source_directory_of_files_to_build_image}`

### Running image with your tag name
Sample: `docker run incodingeverythingispossible/redis`  
Command: `docker run {your_docker_id}/{repo_name}`

### Running image in the background
Sample: `docker run -d incodingeverythingispossible/redis`  
Command: `docker run -d {your_docker_id}/{repo_name}`

### Tag built image with your own name
Sample: `docker tag 9dsajk app1`  
Command: `docker tag {container_id} {your_image_name}`

### Docker run with Port Mapping
Sample: `docker run -p 8080:8080 sdha821`  
Command: `docker run -p {route_incoming_request}:{to_port_on_container} {image_id}`

### Run containers
It runs docker yaml file in current directory  
Command: `docker-compose up`

### Rebuild and run containers
It rebuilds and run docker yaml file in current directory  
Command: `docker-compose up --build`

### Launch containers in background
Command: `docker-compose up -d`

### Stop containers
Command: `docker-compose down`

### Check status of containers
Look for all containers which are defined in docker-compose.yml  
Command `docker-compose ps`