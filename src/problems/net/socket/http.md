# http1.1

## 现象

业务高峰期使用http调用，发现大量的超时

## 分析

排查下游，发现服务没有任何报错，异常信息

排查业务，发现一直是超时

一开始认为套接字不够用了，排查后发现并没有

想到http1.1基于tcp，但是使用pipeline模型，存在队头阻塞的问题，
导致请求还没发出去就已经超时

## 方案

使用http2或者tcp进行调用
