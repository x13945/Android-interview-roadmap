# TCP/UDP

## TCP建立和取消连接

### 三次握手

1. 客户端发送 SYN=1，Seq=X
2. 服务队发送 SYN=1，ACK=X+1，Seq=Y
3. 客户端发送：ACK=Y+1，Seq=Z

之后双方用Z做完数据包的序列开始通信

### 四次挥手

1. 主动方发送：Fin=1， Ack=Z，Seq=X
2. 被动方发送：ACK=X+1， Seq=Z
3. 被动方发送：Fin=1，Ack=X，Seq=Y
4. 主动方发送：ACK=Y，Seq=X

之所以要四次，因为消息是异步发送的，所有要让双方都准备好断开这件事



## 参考

- [TCP三次握手四次挥手详解 - 知乎](https://zhuanlan.zhihu.com/p/40013850)

