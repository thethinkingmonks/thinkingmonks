# Important Links
0001. Convert one programming language to another
www.ide.onelang.io

0002. Convert code to Image
https://carbon.now.sh


## 1. How to generate ssh in putty and use inside vm

### 1. Generate the public and private key

- click on *PuttyGen* program
- click *generate*
- save the public and private keys safely

### 2. copy the public key into virtual machine
```shell
vi ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```

### 3. Connect To Server With Private Key
- Enter the remote server Host Name or IP address under Session.
- Navigate to Connection > SSH > Auth.
- Click Browse... under Authentication parameters / Private key file for authentication.
- Locate the id\_rsa.ppk private key and click Open.
- Finally, click Open again to log into the remote server with key pair authentication.

## 2. Vim

### 2.1 Install Plugin
```shell
:PlugInstall
```

##  3. Doxygen Python Documentation Generator

## 3.1 Installation
```shell
sudo apt install -y doxygen
```

## 3.2 Generate documentation
```shell
doxygen -g
```
