---
description: NPM仓库
---

# Artifactory

## 简介

默认用户，密码  
admin password

## EXPOSE

| 端口 | 用途 |
| :--- | :--- |
| 8081 |  |
| 8082 |  |

## 前置准备

```bash
#创建数据保存目录
sudo mkdir $NFS/artifactory
sudo chown -R 775 $NFS/artifactory
```

## 启动命令

{% tabs %}
{% tab title="Docker" %}
```bash
docker run -d \
--restart unless-stopped \
--network=backend \
--name artifactory  \
-p 8081:8081 -p 8082:8082 \
-v $NFS/artifactory:/var/opt/jfrog/artifactory \
docker.bintray.io/jfrog/artifactory-oss:latest


```
{% endtab %}

{% tab title="Swarm" %}

{% endtab %}
{% endtabs %}



## 参考

