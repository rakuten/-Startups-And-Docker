---
description: 开源网盘，支持阿里云、七牛云等OSS
---

# Cloudreve

## 简介

出色的国产开源免费网盘程序，除了可以将网盘文件储存在服务器本机硬盘之外，它还能快速同时对接国内外多家云存储平台，将文件储存到腾讯云 COS、阿里云 OSS、七牛、又拍云、亚马逊 AWS S3、OneDrive 

## EXPOSE

| 端口 | 用途 |
| :--- | :--- |
| 5212 | 管理页面 |



## 前置准备

```bash
mkdir -p ${NFS}/cloudreve/uploads
mkdir -p ${NFS}/cloudreve/config
mkdir -p ${NFS}/cloudreve/db
mkdir -p ${NFS}/cloudreve/avatar
```

## 启动命令

{% tabs %}
{% tab title="Docker" %}
```bash
docker run -d \
--name cloudreve \
-e PUID=1000 \ # optional
-e PGID=1000 \ # optional
-e TZ="Asia/Shanghai" \ # optional
-p 5212:5212 \
--restart=unless-stopped \
-v ${NFS}/cloudreve/uploads:/cloudreve/uploads \
-v ${NFS}/cloudreve/config:/cloudreve/config \
-v ${NFS}/cloudreve/db:/cloudreve/db \
-v ${NFS}/cloudreve/avatar:/cloudreve/avatar \
xavierniu/cloudreve
```
{% endtab %}

{% tab title="Swarm" %}
```bash
docker service create --replicas 1 \
--name cloudreve \
--network staging \
-e PUID=1000 \ # 可选
-e PGID=1000 \ # 可选
-e TZ=Asia/Shanghai \
--mount type=bind,src=${NFS}/cloudreve/uploads,dst=/cloudreve/uploads \
--mount type=bind,src=${NFS}/cloudreve/config,dst=/cloudreve/config \
--mount type=bind,src=${NFS}/cloudreve/db,dst=/cloudreve/db \
--mount type=bind,src=${NFS}/cloudreve/avatar,dst=/cloudreve/avatar \
xavierniu/cloudreve

#traefik参数
--label traefik.enable=true \
--label traefik.docker.network=staging \
--label traefik.http.services.pan.loadbalancer.server.port=5212 \
--label traefik.http.routers.pan.rule="Host(\`pan.${DOMAIN}\`)" \
--label traefik.http.routers.pan.entrypoints=http \
--label traefik.http.routers.pan-sec.tls=true \
--label traefik.http.routers.pan-sec.tls.certresolver=dnsResolver \
--label traefik.http.routers.pan-sec.rule="Host(\`pan.${DOMAIN}\`)" \
--label traefik.http.routers.pan-sec.entrypoints=https \
```
{% endtab %}
{% endtabs %}

* 查看初始密码

```bash
docker logs -f cloudreve
```

## 参考

