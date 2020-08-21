# redis

## redis cluster

Redis Cluster是一种服务器Sharding技术，3.0版本开始正式提供。
Redis Cluster中，Sharding采用slot(槽)的概念，一共分成16384个槽，这有点儿类pre sharding思路。对于每个进入Redis的键值对，根据key进行散列，分配到这16384个slot中的某一个中。使用的hash算法也比较简单，就是CRC16后16384取模。

## Redis Sharding集群

Redis Sharding可以说是Redis Cluster出来之前，业界普遍使用的多Redis实例集群方法。其主要思想是采用哈希算法将Redis数据的key进行散列，通过hash函数，特定的key会映射到特定的Redis节点上。这样，客户端就知道该向哪个Redis节点操作数据。

## twemproxy

twemproxy又叫nutcracker，起源于twitter系统中redis/memcached集群开发实践，运行效果良好，后代码奉献给开源社区.

## codis

豌豆荚
