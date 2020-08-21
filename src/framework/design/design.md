# 设计

## 核心

高内聚, 低耦合
抽象层

## 日志的报错地方

1. 最底层报错
2. 上层报错

## 包的封装

1. 内部调用外面 (外面是基础)
2. 外面调用内部 (里面是基础)

## 函数功能实现

1. 一层层调用下去，top to down  自顶向下
2. 外面汇总控制， down to top   自下而上
3. 胶合层