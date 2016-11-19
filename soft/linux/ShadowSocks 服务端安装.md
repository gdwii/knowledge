### 安装

```shell
# yum install python-setuptools && easy_install pip
# pip install shadowsocks
```

### 配置

```shell
[root@localhost /]# touch /etc/shadowsocks.json
[root@localhost /]# vi /etc/shadowsocks.json
{
    "server":"138.128.208.158",
    "server_port":443,
    "local_address": "127.0.0.1",
    "local_port":1080,
    "password":"MyPass",
    "timeout":600,
    "method":"rc4-md5"
}
```

备注：加密方式官方默认使用aes-256-cfb，推荐使用rc4-md5，因为 RC4比AES速度快好几倍。
各字段说明：
- server:服务器IP 
- server_port:服务器端口
- local_port:本地端端口
- password:用来加密的密码
- timeout:超时时间（秒）
- method:加密方法，可选择 “bf-cfb”, “aes-256-cfb”, “des-cfb”, “rc4″等

### 运行
```shell
[root@localhost /]# ssserver -c /etc/shadowsocks.json -d start
```
### 停止
```shell
ssserver -c /etc/shadowsocks.json -d stop
```
