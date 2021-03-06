---
layout: post
title: 非关系型数据库和关系型数据库区别，优势比较
categories: [database]
description: some word here
keywords: 关系型数据库, 非关系型数据库
---

非关系型数据库的优势：
1. 性能
NOSQL是基于键值对的，可以想象成表中的主键和值的对应关系，而且不需要经过SQL层的解析，所以性能非常高。
2. 可扩展性
同样也是因为基于键值对，数据之间没有耦合性，所以非常容易水平扩展。

关系型数据库的优势：
1. 复杂查询
可以用SQL语句方便的在一个表以及多个表之间做非常复杂的数据查询。
2. 事务支持
使得对于安全性能很高的数据访问要求得以实现。

对于这两类数据库，对方的优势就是自己的弱势，反之亦然。

但是近年来这两种数据库都在向着另外一个方向进化。例如：
NOSQL数据库慢慢开始具备SQL数据库的一些复杂查询功能的雏形，比如Couchbase的index以及MONGO的复杂查询。对于事务的支持也可以用一些系统级的原子操作来实现例如乐观锁之类的方法来曲线救国。
SQL数据库也开始慢慢进化，比如HandlerSocker技术的实现，可以在MYSQL上实现对于SQL层的穿透，用NOSQL的方式访问数据库，性能可以上可以达到甚至超越NOSQL数据库。可扩展性上例如Percona Server，可以实现无中心化的集群。

虽然这两极都因为各自的弱势而开始进化出另一极的一些特性，但是这些特性的增加也会消弱其本来具备的优势，比如Couchbase上的index的增加会逐步降低数据库的读写性能。所以怎样构建系统的短期和长期存储策略，用好他们各自的强项是架构师需要好好考虑的重要问题。 

