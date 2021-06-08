# 锁

## 概念

- 公平锁

    - 多个线程按照申请锁的顺序来获取锁
- 非公平锁

    - 多个线程获取锁的顺序并不是按照申请锁的顺序
- 可重入锁 

    - ReentrantLock 
        - AQS中维护了一个private volatile int state来计数重入次数，避免了频繁的持有释放操作
    - synchronized
    - 可重复可递归调用的锁，在外层使用锁之后，在内层仍然可以使用
- 不可重入锁

    - 不可重入锁，与可重入锁相反，不可递归调用，递归调用就发生死锁
-         AtomicReference
- 独享锁
    - 线程独有
- 非独享所
    - 线程间共享
    - ReentrantReadWriteLock
- 互斥锁
    - 只有一个线程能持有
- 读写锁
    - 多个线程共享锁
- 乐观锁
    - 假设读多写少，读不加锁，写的时候加锁
- 读写锁
    - 读写都加锁
- 分段锁
    - ConcurrentHashMap

## 参考

- [常见的Java锁总结：公平锁，可重入锁，独享锁，互斥锁，乐观锁，分段锁，偏向锁，自旋锁等等 - 简书](https://www.jianshu.com/p/6456af2a7c5d)
