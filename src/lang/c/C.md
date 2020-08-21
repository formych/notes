# C

## 传值

所有的传值本质都是变量值的传递
C中改变一个变量(包括指针)的值，就传他的地址即可（使用多级指针）
java和c++不同，不能修改实参的引用，只能修改实参的内容

## 预处理指令（正是编译之前的处理）

C提供的预处理功能：

1. 宏定义
2. 文件包含
3. 条件编译

以"#"开头，后面不加分号
预处理是C语言特有的，有利于程序的移植性，增加程序灵活性
有助于目标程序精简，减少运行时间

### 宏定义

宏展开：就是用字符串代替标识符

- 不带参数的宏定义
  格式
  `#define 标识符 字符串`
  作用范围
  该指令行到源文件结束，可以用#undef指令结束宏定义
  宏定义不分配存储空间，不带参数的宏定义只做简单的字符串替换
  "宏名"这种字符串不做置换

- 带参数的宏定义
格式
`#define 标识符(参数) 字符串`
`#define S(r) PI * (r) * (r)`
置换原则
  用实参代替形参，在宏定义时，字符串中的形式参数外加一个括号
  带参宏定义与函数的区别
    a.函数调用先求参数的值，再代入; 而宏定义只是进行置换
    b.函数调用是程序运行时处理的； 而宏定义是在预处理阶段
    c.函数调用中的参数有类型; 而宏不存在类型问题

### 文件包含

```text
含义
在源文件中将另一个源文件的全部内容包含进来，插入到当前位置
格式
`#include "文件名"`
`#include <文件名>`
尖括号和双撇号区别
尖括号是到存放C函数库里的头文件的目录下寻找，为标准方式
双撇号是到当前用户目录下寻找，若找不到则按标准方式
```

#### 头文件可包含

- 函数原型
- 宏定义
- 结构体类型定义
- 全局变量

#### 顺序

- 先小后大
- 可嵌套使用

### 条件编译

格式
```C
#ifdef 标识符
process1
#else
process2
#endif
```
```C
#ifndef 标识符
process1
#else
process2
#endif
```
```C
#if  表达式
process1
#else
process2
#endif
```