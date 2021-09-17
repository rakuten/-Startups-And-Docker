---
description: 性能压力测试
---

# Locust

## 简介

Harbor 是 VMware 开源的 Registry，也是一款大众熟知的产品，但运行它需要启动约8个容器实例，让人实在提不起兴趣去跑，等哪天有空再搞吧

内容完善中....

## EXPOSE

| 端口 | 用途 |
| :--- | :--- |
| 5557 |  |
| 8089 |  |



## 前置准备

```bash

```

## 启动命令

{% tabs %}
{% tab title="Docker" %}
```bash
docker run \
-p 8089:8089 \
-v $PWD:/mnt/locust \
locustio/locust -f /mnt/locust/locustfile.py
```
{% endtab %}

{% tab title="Swarm" %}

{% endtab %}

{% tab title="Compose" %}
```yaml
version: '3'

services:
  master:
    image: locustio/locust
    ports:
     - "8089:8089"
    volumes:
      - ./:/mnt/locust
    command: -f /mnt/locust/locustfile.py --master -H http://master:8089
  
  worker:
    image: locustio/locust
    volumes:
      - ./:/mnt/locust
    command: -f /mnt/locust/locustfile.py --worker --master-host master
```
{% endtab %}
{% endtabs %}



## 参考

官网: [https://locust.io/](https://locust.io/)

插件:  
[https://github.com/SvenskaSpel/locust-plugins](https://github.com/SvenskaSpel/locust-plugins)  
[https://github.com/SvenskaSpel/locust-swarm](https://github.com/SvenskaSpel/locust-swarm)

