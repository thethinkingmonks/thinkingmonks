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
FROM ubuntu:20.04

```

## Build the custom image
```shell
sudo docker build .
```
