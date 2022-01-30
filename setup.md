# 1. FTP Setup
## Reference Link
```link
https://linuxize.com/post/how-to-setup-ftp-server-with-vsftpd-on-ubuntu-20-04/
```

## Install FTP
```shell
sudo apt update
sudo apt install -y vsftpd
```

## Configure VSFTPD
```shell
sudo vim /etc/vsftpd.conf
```

## Change the config of vsftpd
```txt
listen=NO
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
rsa_private_key_file=/etc/ssl/private/vsftpd.pem
ssl_enable=YES
user_sub_token=$USER
local_root=/home/$USER/ftp
pasv_min_port=30000
pasv_max_port=31000
userlist_enable=YES
userlist_file=/etc/vsftpd.user_list
userlist_deny=NO
force_local_logins_ssl=NO
force_local_data_ssl=NO
allow_writeable_chroot=YES
```

## create the user
```shell
mkdir ~/ftp
echo "thinkingmonks" | sudo tee -a /etc/vsftpd.user_list
cat /etc/vsftpd.user_list
```
## Enable the service 
```shell
sudo systemctl restart vsftpd
sudo ufw allow 20:21/tcp
sudo ufw allow 30000:31000/tcp
sudo ufw allow OpenSSH
```

## create ssh keys
```shell
sudo openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -keyout /etc/ssl/private/vsftpd.pem -out /etc/ssl/private/vsftpd.pem
```
## Login into ftp to download file
```shell
ftp 192.168.0.113
thinkingmonks
lcd .
get <filename>
mget <filename1> <filename2>
```
## Login into ftp

# 2. Add SSH key
## Generate SSH Key
```shell
ssh-keygen -t rsa -b 4096 -C "thethinkingmonks@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

## Add SSH key 
Copy the below key and paste in github account
```shell
cat ~/.ssh/id_ras.pub
```

## Add username and email in git config
```shell
git config --global user.name "Thinking Monks"
git config --global user.email "thethinkingmonks"
git config --global core.editor "vim"
git config --global merge.tool kdiff3
```

# Ngrok
## Installation of Ngrok
```shell
curl -s https://ngrok-agent.s3.amazonaws.com/ngrok.asc | sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null &&
              echo "deb https://ngrok-agent.s3.amazonaws.com buster main" | sudo tee /etc/apt/sources.list.d/ngrok.list &&
              sudo apt update && sudo apt install ngrok
```

## Running Ngrok
```shell
ngrok http 80
```
