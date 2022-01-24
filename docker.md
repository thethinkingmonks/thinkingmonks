# 1. Installation of docker

## Install docker
```shell
sudo apt install -y docker.io
```

## Check the docker version
```shell
docker --version
```

## Pull hello-world image
```shell
sudo docker run hello-world
```
 
# 2. Build Custom Image

## Create a file named "Dockerfile" with below content

```dockerfile
# Base Image
FROM ubuntu:20.04

# Security Update
RUN apt update

# vim
RUN apt install -y vim
```

## Build the custom image
```shell
sudo docker build .
```

# 3. Run the docker container

## Build the custom image and tag the image
```shell
sudo docker build --tag ubuntu:latest .
```

## Run the docker container
```shell
sudo docker run ubuntu
```

## Add the echo command in the Dockerfile
```dockerfile
# Base Image
FROM ubuntu:20.04

# Security Update
RUN apt update

# vim
RUN apt install -y vim

# Echo Command
CMD ["echo", "Hi Thinking Monks"]
```

## View the list of running containers
```shell
sudo docker ps
```

## Run the container in interactive mode
```shell
sudo docker -it ubuntu 
```

# 4. Run an application

## Create a python application with below content

```python
from time import sleep

for i in range(10):
    print("Thinking Monks {}".format(i+1))
    sleep(5)
```

## Create a file named "Dockerfile" with below content

```dockerfile
# Base Image
FROM ubuntu:20.04

# Security Update
RUN apt update

# vim
RUN apt install -y vim

# Echo Command
CMD ["echo", "Hi Thinking Monks"]

# python3
RUN apt install -y python3

# copy application
COPY app.py /app/app.py

# run application
CMD ["python3", "/app/app.py"]
```

## Build the custom image and tag the image
```shell
sudo docker build --tag ubuntu:latest .
```

## Run the docker container
```shell
sudo docker run ubuntu
```

## Run the container in interactive mode
```shell
sudo docker run -it ubuntu
```
# 5. Docker Volume

## Build the custom image and tag the image
```shell
sudo docker build --tag ubuntu:latest .
```
## Run the container in interactive mode with volume
```shell
sudo docker run -it --volume data:/app ubuntu
```

# 6. Docker-compose 
## Installation of docker-compose 

```shell
sudo curl -L "https://github.com/docker/compose/releases/download/v2.2.3/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose
sudo chmod +x /usr/bin/docker-compose
sudo docker-compose --version
```

## Docker-Compose file for server app
```yaml
version: "3.9"
services:
  server:
    build: .
    ports:
      - "3000:3000"
    expose:
      - 3000
    volumes:
      - server_data:/app
volumes:
  server_data:
```
