# 位操作

go和c的位操作符

+ 与                   &
+ 或                   |
+ 异或                 ^
+ 右移                 >>
+ 左移                 <<
+ 按位取反              ~

区别：

+ go里面没有~, 用^代替

示例

```go
i&1 == 0          // 判断奇偶

i|0                   // 位或

^a + 1                  // 变换符号 go版本
~a + 1                  // 变换符号 c版本

a ^= b                  // 交换两个变量的值
b ^= a
a ^= b
```

交换2个数的算法

```sh
1. 用第三个变量

2. 用
c = a + b;
a = c - a;
b = c - b;

3. 位异或

a ^ a = 0
a ^ 0 = a

a = b <=> a = b^(a^a) <=> a^(a^b)
b = a <=> b = a^(b^b)^(a^a) <=> a^(a^b)^(a^b)

所以类推之 a^b
a ^= b
b ^= a
a ^= b

4. 语言原生支持(go)
a, b = b, a
```
