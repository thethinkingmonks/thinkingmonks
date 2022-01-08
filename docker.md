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

# Run the docker container

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

# 3. Run an application

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
