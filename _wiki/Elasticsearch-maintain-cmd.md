---
layout: wiki
title: Elasticsearch维护命令
categories: Elasticsearch
description: 日常维护指令记录
keywords: Elasticsearch
---

### 服务启动
```
sudo su sre
cd /var/wd/elasticsearch
./startup.sh
```
特别注意：不能用前端方式启动，使用前端方式启动的进程将在ssh进程中断时关闭。

### 服务关闭
```
sudo su sre
cd /var/wd/elasticsearch
./shutdown.sh
```
 

### 健康检查
```
curl 'localhost:9200/_cat/health?v'
curl 'localhost:9200/_cat/nodes?v'
curl 'localhost:9200/_cat/shards?v'
curl 'localhost:9200/_cat/indices?v'
```
注：IP和端口根据实际情况修改
 

### 内存调整
修改startup.sh
```
#!/bin/bash
./bin/elasticsearch -d -Xms3g -Xmx7g -p ./bin/pid
```
修改ms和mx为最小和最大内存使用量

### 故障恢复
当集群出现故障需要重启时，关闭所有服务器，先启动集群中主节点，主节点配置在discovery.zen.ping.unicast.hosts中。
