# FAQ

1. HTTP如何确定数据传输结束？
    短连接
        1.0 服务端关闭
    Content-Length
        传输的body大小
        如果使用压缩gzip，则为压缩后的长度，该值和实际数字不一致，会产生超时和截断
            长度大于实际传输的数据，造成超时
            长度小于实际传输的数据，造成截断
                1.1 keepalive的情况下, 截断会造成下次请求来的时候，服务端读取上次剩余的字节，数据解析混乱
    Transfer-Encoding
        chunked
            数据以分块的方式传输，每个分块的开头添加当前分块的长度，16进制表示，后跟\r\n，
            然后是数据块，后跟\r\n，... 最后跟终止块，长度为0

            数据块: 长度 + \r\n + 数据 + \r\n
            终止块: 长度0 + \r\n
            \r\n

            [chunk size][\r\n][chunk data][\r\n]
            ...
            [chunk size][\r\n][chunk data][\r\n]
            [chunk size = 0][\r\n][\r\n]

2. HTTP2如何确定数据传输结束？
    stream序号和确认号
    http2的语义还是基于http1.1的，同上

3. 一个服务存在多个tcp连接，在主机上的socket的端口号是怎么样的？
    端口复用，多个tcp共用一个端口号，使用ss -tpan查看, 多个socket指向同一个socket

4. socket.accept()产生新的socket的解释？
    由于tcp面向连接的，欢迎套接字监听建立连接请求，返回新的套接字建立tcp连接

5. TCP在1s时间内能传输最大传输量？
    tcp是一个传输层协议，本身不限制数据大小，只负责把数据交到下一层
    由于以太网的MTU决定一次传输的大小，一般是1500，减去每一层的头部，剩下就是数据量
    一个TCP连接类一条高速公路，能穿多少取决于高速公路的基础设施(宽度和速度)

6. UDP， IP数据包的大小？
   由于以太网的MTU决定一次传输的大小，一般是1500，减去每一层的头部，剩下就是数据量
   大于MTU的数据会进行数据包分片
   建议将UDP数据控制在1472字节以下
   Internet编程时，建议将UDP数据控制在576字节以下

7. 基于TCP传输数据,如何读取?
    自定义二进制数据的拆包封包协议
    流式数据的解析

8. 粘包
    原因
        1. negal优化算法:会将数据量小的，且时间间隔较短的数据一次性发给对方
        2. 接收方不及时接收缓冲区的包，造成多个包接收

    解决
        1.禁用negal优化算法
        2.定义数据大小字段，加入到数据前面，
        3.protobuf解决方案

    参考
    [1](https://www.cnblogs.com/juepei/p/4421569.html)
    [2](https://www.cnblogs.com/sui776265233/p/9289858.html)

9. 惊群效应

[参考](https://manjusaka.itscoder.com/posts/2019/03/28/somthing-about-thundering-herd/)
