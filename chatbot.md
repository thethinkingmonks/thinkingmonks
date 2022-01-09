# 1. Installations

## Create Virtual Environment
```shell
cd ~
apt install -y python3-pip
python -m venv chatbot
source ~/chatbot/bin/activate
```

## Install and Download SpaCy Model
```shell
source ~/chatbot/bin/activate
pip install pip setuptools wheel
pip install --timeout=10000 spacy
python -m spacy download en_core_web_trf
```

