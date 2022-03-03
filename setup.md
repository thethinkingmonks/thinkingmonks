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

# 3. Setup Torrent CLI
## 3.1 Installation

```shell
sudo add-apt-repository ppa:transmissionbt/ppa
sudo apt-get update
sudo apt-get install transmission-cli transmission-common transmission-daemon
```

## 3.2 Configure

```shell
sudo service transmission-daemon stop
sudo vim /var/lib/transmission-daemon/info/settings.json
```

### Change below parameters
```json
{
"rpc-password": "{62b16db87b89a91dd49a5110a7cafc06d20eb4f2wtK6kqPj",
"rpc-username": "transmission",
"rpc-whitelist": "127.0.0.1,192.168.*.*",
"umask": 2,
}
```

### Restart the service
```shell
sudo service transmission-daemon start
```

### Place the torrent file in below dir
```shell
/var/lib/transmission-daemon/downloads/
sudo usermod -a -G debian-transmission thinkingmonks
```

### Starting and Stoping deamons
```shell
sudo service transmission-daemon start
sudo service transmission-daemon stop
sudo service transmission-daemon reload
```

### Bash Alias
```bash
alias t-start='sudo service transmission-daemon start'
alias t-stop='sudo service transmission-daemon stop'
alias t-reload='sudo service transmission-daemon reload'
alias t-list='transmission-remote -n 'transmission:transmission' -l'
alias t-basicstats='transmission-remote -n 'transmission:transmission' -st'
alias t-fullstats='transmission-remote -n 'transmission:transmission' -si'
```

### To add a torrent to the daemon, use this command:
```shell
transmission-remote -n 'transmission:transmission' -a /var/lib/transmission-daemon/downloads/files.torrent
```


