# 1. Installation

## 1.1 Installation of Python

For Ubuntu

```shell
sudo apt install -y python
```

For Centos

```shell
sudo yum install -y python
```

## 1.2 Installation of Anaconda

Go to link https://www.anaconda.com/products/individual#linux and download the appropriate installer

```shell
wget https://repo.anaconda.com/archive/Anaconda3-2021.11-Linux-x86_64.sh
bash Anaconda3-2021.11-Linux-x86_64.sh
```

## 1.3 Create virtual environment using anaconda

```shell
conda create --name ml
```

## 1.4 Installation of Scikit Learn

```shell
conda list scikit-learn
conda install conda-forge scikit-learn
pip install scikit-learn
```

## 1.5 Installation of Jupyter Notebook

Install the classic Jupyter Notebook with:
```shell
pip install notebook
```

To run the notebook:
```shell
jupyter notebook
```

## 1.6 Installation of JupyterLab

Install JupyterLab with pip:
```shell
pip install jupyterlab
```

Once installed, launch JupyterLab with:
```shell
jupyter-lab
```

## 1.7 Installation JupyterLab using Docker

DockerFile details

```Dockerfile
FROM jupyter/all-spark-notebook

USER root

## Install all the required packages as root user
RUN apt update
RUN apt install -y vim
RUN apt install -y trash-cli
RUN apt install -y iputils-ping
RUN apt install -y net-tools

USER 1000

# Jupyter Lab Extensions
RUN pip install jupyterlab_theme_solarized_dark
RUN pip install jupyterlab-system-monitor
```

Docker Compose yaml file
```yaml
version: "3.9"
services:
  jupyter:
    container_name: "jupyter"
    build:
      context: ./jupyter
    ports:
      - "10000:8888"
      - "10100:10100"
      - '8889:8889'
    expose:
      - 10000
      - 10100
      - 8889
    user: root
    logging:
      options:
        max-size: 10m
        max-file: "3"
    environment:
      - GRANT_SUDO=yes
      - NB_USER=thinkingmonks
      - NB_UID=1000
      - NB_GID=1000
      - CHOWN_HOME=yes
    volumes:
      - ./work:/home/thinkingmonks/work
```

## 1.8 Attach the conda environment to jupyter notebook
```shell
python -m ipykernel install --user --name=ml
```
