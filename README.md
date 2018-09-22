# ngrok 使用

> ## 采用了[来自 hteen 的 ngrok docker 镜像](https://github.com/hteen/docker-ngrok)

## 文件备份

ngrok 文件夹下即为本次使用的 hteen/ngrok 镜像构建脚本，ngrok 版本 1.7

# 构建

```powershell
docker run --rm -it -e DOMAIN='ngrok.jijiwuming.cn' \
-v /home/ubuntu/ngrok:/myfiles hteen/ngrok /bin/sh /build.sh
```

# 启动服务端

```powershell
docker run -idt --name ngrok-server \
-v /home/ubuntu/ngrok:/myfiles \
-p 80:80 \
-p 4442:443 \
-p 4443:4443 \
-e DOMAIN='ngrok.jijiwuming.cn' hteen/ngrok /bin/sh /server.sh
```

# 启动客户端

```powershell
./ngrok -config ./ngrok.cfg -subdomain test 192.168.1.100:80
```

## 注意

- 对 ngrok 和 test.ngrok 都要配置对应的域名 A 记录
