# AQS(AbstractQuenedSynchronizer)

## 简介

AQS是Java中ReentrantLock的低层实现

## 原理

1. 一个volatile的整数，同时提供setState和getState方法
2. 一个FIFO的等待线程队列，多线程等待和竞争
3. 给予CAS，实现acquire和releae

### 应用

#### ReentrantLock

1. 内部通过AQS实现了Sync，以AQS的state来反应锁的状况。
    1. 通过构造方法，指定公平性

2. lock
    1. 执行sync的acquire(1)
        1. 设置成功，则标记当前锁的持有者是自己，return，否则会添加到等待队列的尾端
    2. 执行sync的release(1)

所谓公平和非公平，就是公平锁会直接把自己加到队列中，而非公平锁会先有限抢锁资源。



## 参考

- [第24讲 | 有哪些方法可以在运行时动态生成一个Java类？](https://time.geekbang.org/column/article/10076)