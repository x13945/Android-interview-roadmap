# IO

## NIO

NIO通常在服务端会多一些，可以实现单个线程服务多个socket连接

- Buffer 数据容器
- Channel 对于文件的抽象
    - 双向，即可读也可写
    - 实现
        - FileChannel
        - DatagramChannel
        - ServerSocketChannel
            - 只有非阻塞状态才能配置
        - SocketChannel
- Selector 用于检测注册到Selector上的Channel状态
    - 只有ServerSocketChannel和SocketChannel类里才能通过其注册方法注册到Selector上面
- Charset 提供Unicode 字符串定义

## 参考

- [第11讲 | Java提供了哪些IO方式？ NIO如何实现多路复用？](https://time.geekbang.org/column/article/8369)
- [网络编程NIO：BIO和NIO - 小高飞 - 博客园](https://www.cnblogs.com/gaofei200/p/13933952.html)