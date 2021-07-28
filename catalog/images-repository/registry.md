---
description: Docker仓库
---

# Registry

## 简介



## EXPOSE

| 端口 | 用途 |
| :--- | :--- |
| 5000 | 通讯端口 |



## 前置准备

```bash
#创建数据保存目录
mkdir ${NFS}/registry
chmod -R 775 $NFS/registry
```

## 启动命令

{% tabs %}
{% tab title="Docker" %}
```bash
docker run -d \
--name registry \
--restart unless-stopped \
-e TZ=Asia/Shanghai \
--restart always \
-e TZ=Asia/Shanghai \
-p 5000:5000 \
-v ${NFS}/registry:/var/lib/registry \
registry
```
{% endtab %}

{% tab title="Swarm" %}

{% endtab %}
{% endtabs %}



## 参考

