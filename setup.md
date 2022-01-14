# 1. FTP Setup

## Install FTP
```shell
sudo apt update
sudo apt install -y vsftpd
```

## Configure VSFTPD
```shell
sudo vim /etc/vsftpd.vim
```

## Change the config of vsftpd
```txt
listen=NO
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=Yes
pasv_enable=Yes
pasv_min_port=10000
pasv_max_port=10100
allow_writeable_chroot=YES
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO
```

## Allow ports in firewall
```shell
sudo ufw allow 20/tcp
sudo ufw allow 21/tcp
```
# 2. Add SSH key
```shell
ssh-keygen -t rsa -b 4096 -C "thethinkingmonks@gmail.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```
