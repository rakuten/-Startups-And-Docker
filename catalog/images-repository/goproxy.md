---
description: Go 源缓存服务
---

# GOPROXY

## 简介



## EXPOSE

| 端口 | 用途 |
| :--- | :--- |
| 8081 | 通讯端口 |



## 前置准备

```bash

```

## 启动命令

{% tabs %}
{% tab title="Docker" %}
```bash
docker run -d \
--network=backend \
--restart unless-stopped \
-e TZ=Asia/Shanghai \
--name traefik \
-p 8081:8081 \
-v /${NFS}/goproxy:/go \
goproxy/goproxy
```
{% endtab %}

{% tab title="Swarm" %}

{% endtab %}
{% endtabs %}



1. 设置 `export GOPROXY=http://localhost #允许goproxy`
2. 设置 `export GOPROXY=direct #禁止goproxy`

## 参考

官网: [https://goproxy.io/zh/](https://goproxy.io/zh/)  
DockerHub: [https://github.com/goproxyio/goproxy](https://github.com/goproxyio/goproxy)

