# Aliyun DNS Authenticator plugin for Certbot

A certbot dns plugin to obtain certificates using aliyun.


## Obtain Aliyun RAM AccessKey
[https://ram.console.aliyun.com/](https://ram.console.aliyun.com/)

And ensure your RAM account has `AliyunDNSFullAccess` permission.


## Install
安装
以Archlinux及Aliyun-dns为例，首先安装certbot

```
sudo pacman -Sy certbot
```
然后手动安装cerbot-dns-aliyun(其他DNS供应商请到certbot官网查看对应dns插件)

```bash
git clone https://github.com/tengattack/certbot-dns-aliyun
cd certbot-dns-aliyun
sudo python setup.py install
```
## Credentials File
设置Aliyun Api凭证

```ini
certbot_dns_aliyun:dns_aliyun_access_key = 12345678
certbot_dns_aliyun:dns_aliyun_access_key_secret = 1234567890abcdef1234567890abcdef
```

```bash
chmod 600 /path/to/credentials.ini
```


## Obtain Certificates
获取证书

```bash
certbot certonly -a certbot-dns-aliyun:dns-aliyun \
    --certbot-dns-aliyun:dns-aliyun-credentials /path/to/credentials.ini \
    -d example.com \
    -d "*.example.com"
```
