---
description: 开源网盘，支持阿里云、七牛云等OSS
---

# Cloudreve

## 简介

Harbor 是 VMware 开源的 Registry，也是一款大众熟知的产品，但运行它需要启动约8个容器实例，让人实在提不起兴趣去跑，等哪天有空再搞吧

内容完善中....

## EXPOSE

| 端口 | 用途 |
| :--- | :--- |
| 53 | DNS |
| 8080 | 管理页面 |



## 前置准备

```bash
mkdir -p ${NFS}/cloudreve/uploads
mkdir ${NFS}/cloudreve/config
mkdir ${NFS}/cloudreve/db
mkdir ${NFS}/cloudreve/avatar
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

{% endtab %}
{% endtabs %}

* 查看初始密码

```bash
docker logs -f cloudreve
```

## 参考

