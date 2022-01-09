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
python -m spacy download en_core_web_lg
pip install --timeout=10000 https://github.com/explosion/spacy-models/releases/download/en_core_web_sm-3.2.0/en_core_web_sm-3.2.0.tar.gz
pip install --timeout=10000 https://github.com/explosion/spacy-models/releases/download/en_core_web_md-3.2.0/en_core_web_md-3.2.0.tar.gz
pip install --timeout=10000 https://github.com/explosion/spacy-models/releases/download/en_core_web_lg-3.2.0/en_core_web_lg-3.2.0.tar.gz
```

