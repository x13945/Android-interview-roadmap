## 目标

- Android 4个番茄
- 算法 4个番茄

## 进度

### Android 6个番茄

#### Handler-Looper

作为Android架构中的消息体系。驱动了Android上层的几乎所有多线程场景。

- Handler

    向消息队列中发送消息，以及处理消息队列中取出的消息。可以发送一般消息和延时消息，最终都会调用到同一处`sendMessageAtTime->enqueueMessage`。然后调用到`MessageQueue`的`enqueueMessage`。

    `Message`被发送时，其`target`会被设置为当前`Handler`，因此才可以被`Looper`分配给特定`Handler`。

    `Handler`在构造函数中，回去关联对应的`Looper`，然后从`Looper`中取出`MessageQueue`。这里会先检查当前线程的`Looper`是否完备

- MessageQueue

    消息队列。是一个基于时间为优先级的有序队列，基于触发时间升序排列。消息会在放入队列的时候排序，假如触发时间相等，则会以放到队列中的时间作为作为优先级。

    - 放入消息 `enqueueMessage`

    - `Looper`取消息 `next`

        如果队列头的消息还没到触发时间，则会通过Poll休眠当前线程，让出CPU资源。
        
    - 线程安全 是由`synchronized`来锁的代码块

- Looper

    负责从`MessageQueue`中取消息，然后交给`Handler`处理。

    由于其构造方法时私有的，因此只能被静态方法`prepare`来初始化。初始化的过程，会构建一个私有的`Looper`对象，放到当前线程的`ThreadLocal`对象中，且只能初始化一次。

- Message

    用于携带信息。有一个大小是50的消息池，用于复用。消息池就是个单向链表。

    - 属性

        -             what 永远标记消息 整型
        -             arg1 arg2 整型
        -             obj Object类型
    - 复用
        - 通过Obtain 在消息池的头部复用消息
        - 用完的消息会塞到头那里

##### 同步屏障

消息大致分三种：

- 同步消息
- 异步消息
- 同步屏障消息

日常使用的都是同步消息，屏障消息就是在消息队列中插入一个屏障，在屏障之后的所有普通消息都会被挡着。

同步屏障是通过`MessageQueue`的`postSyncBarrier`方法插入到消息队列中。屏障消息的特点就是其`target`是`null`。插入普通消息会唤醒消息队列，但是插入屏障不会。

原理是，如果有同步消息，next方法取消息的时候，只会取到异步消息，同步消息会被屏蔽掉。

##### IdleHandler

###### 1. 作用

在消息队列中，没有消息可以处理的时候，就会触发。例如`ActivityThread`的`main`方法中，会在第一次`idle`的时候，调用一次`GC`

###### 2. 使用

往消息队列中插入IdleHandler

###### 3. 原理

在`next`中取不到消息的时候，会依次只想`IdleHandler`，然后基于其重写的`queueIdle`，来判断是否移除掉。

### 算法 4个番茄

- 队列
    - 数组队列 大小敏感
    - 链表队列 大小不敏感，无限长度
    - 循环队列