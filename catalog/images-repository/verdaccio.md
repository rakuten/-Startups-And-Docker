---
description: NPM仓库
---

# Verdaccio

## 简介



## EXPOSE

| 端口 | 用途 |
| :--- | :--- |
| 4873 | 管理页面 |



## 前置准备

```bash
#创建数据保存目录
mkdir $NFS/verdaccio
chmod 775 $NFS/verdaccio
```

## 启动命令

{% tabs %}
{% tab title="Docker" %}
```bash
docker run -d \
--restart unless-stopped \
--network=backend \
--name verdaccio \
-p 4873:4873 \
-v $NFS/verdaccio:/verdaccio/storage \
verdaccio/verdaccio
```
{% endtab %}

{% tab title="Swarm" %}

{% endtab %}
{% endtabs %}



## 参考

