---
description: 波场
---

# Tron

## 简介

官方提供的docker镜像不仅偏大而且很旧，所以我们自己动手丰衣足食

## EXPOSE

| 端口 | 用途 |
| :--- | :--- |
| 8090 | full node HTTP API |
| 8091 | solidity node HTTP API |
| 18888 | P2P端口 |



## 前置准备

```bash
#创建数据保存目录
mkdir ${NFS}/tron
chmod 775 $NFS/tron

#获取SuStake(Tron侧链)官方提供的Dockerfile
wget https://github.com/SunStake/docker-java-tron/archive/refs/heads/master.zip
unzip master.zip
cd docker-java-tron-master
docker build --build-arg JAVA_TRON_VERSION="GreatVoyage-v4.2.2.1" -t java-tron:4.2.2.1 .
```

## 启动命令

{% tabs %}
{% tab title="Docker" %}
```bash
docker run -d \
--name = tron \
-e NETWORK=dev \
-e WITNESS_MODE=true \
-p 8090:8090 \
-v $NFS/tron:/data \
java-tron:4.2.2.1
```
{% endtab %}

{% tab title="Swarm" %}

{% endtab %}
{% endtabs %}



## 参考

Tron官网: [https://tron.network/index?lng=zh](https://tron.network/index?lng=zh)  
TRC20说明: [https://cn.developers.tron.network/docs/trc20%E5%90%88%E7%BA%A6%E4%BA%A4%E4%BA%92%E4%BB%A5usdt%E4%B8%BA%E4%BE%8B](https://cn.developers.tron.network/docs/trc20%E5%90%88%E7%BA%A6%E4%BA%A4%E4%BA%92%E4%BB%A5usdt%E4%B8%BA%E4%BE%8B)  
Docker环境变量: [https://github.com/SunStake/docker-java-tron](https://github.com/SunStake/docker-java-tron)

