---
description: 系统源缓存服务
---

# Apt-Cacher NG

## 简介

![](../../.gitbook/assets/cache-service-started.png)

## EXPOSE

| 端口 | 用途 |
| :--- | :--- |
| 3142 | 管理页面 |



## 前置准备

```bash
mkdir -p ${NFS}/acng/data
mkdir ${NFS}/acng/logs
```

## 启动命令

{% tabs %}
{% tab title="Docker" %}
```bash
--cap-drop=all \
--name apt-cacher-ng \
-e TZ=Asia/Shanghai \
-p 3142:3142 \
-v ${NFS}/acng/data:/var/cache/apt-cacher-ng \
-v /mnt/share2/nfs/acng/logs:/var/log/apt-cacher-ng \
--label traefik.enable=false \
konstruktoid/apt-cacher-ng
```
{% endtab %}

{% tab title="Swarm" %}
```bash
docker service create --replicas 1 \
--name acng \
--network staging \
-e TZ=Asia/Shanghai \
-p 3142:3142 \
--mount type=bind,src=${NFS}/acng/data,dst=/var/cache/apt-cacher-ng \
--mount type=bind,src=${NFS}/acng/logs,dst=/var/log/apt-cacher-ng \
--label traefik.enable=false \
konstruktoid/apt-cacher-ng
```
{% endtab %}
{% endtabs %}



## 参考

官网: [https://www.unix-ag.uni-kl.de/~bloch/acng/](https://www.unix-ag.uni-kl.de/~bloch/acng/)

