# Android-interview-roadmap

未来准备`Android`面试，准备了这个仓库，做完复习笔记。

### 预期

### 1. Java基础

- 多线程
- IO/NIO
- 泛型
  - [Java泛型的协变、逆变和不变 - 简书](https://www.jianshu.com/p/90948ff4a940)
- 设计模式

### 2. Android

- 四大组件源码解析
- View 绘制流程解析
    -   [day06](./day06/day06.md)
- 点击事件分发解析 [day06](./day06/day06.md)
- 组件化
- 插件话
    - ClassLoader
        - BootstrapClassLoader
        - 
- 热修复
- 性能优化
- 瘦身
- 架构
  - mvp
  - mvc
  - mvvm
- Jetpack
- Handler
- NDK
    - [Android JNI 篇 - JNI回调的三种方法（精华篇） - 简书](https://www.jianshu.com/p/e576c7e1c403)
- IPC
    - Linux IPC方式
        - 管道
        - 消息队列
        - 共享内存
        - Socket
    - Binder
        - 平衡稳定性、安全性和性能
        - mmap 内存映射
    - ServiceManager进程和Zygote通信的时候为什么不用bindler，而是socket
        - binder依赖多线程操作，而fork进程的时候如果有多线程会出现死锁
    - AIDL
        - IBinder
        - IInterface
        - Binder
        - Stub
        - [写给 Android 应用工程师的 Binder 原理剖析 - 知乎](https://zhuanlan.zhihu.com/p/35519585)

### 3. Kotlin

- 协程
    - 不同的dispatcher有什么区别，例如IO，Compute等

#### 4. React-Native

- 性能优化
- 原理
- 引擎 jsi
  - jsc
  - v8
  - hermes



## 进度

- Day01 50%
- Day02 25%
- Day03 摸鱼
- Day04 出去耍
- Day05 100%
- Day06 100%
- Day06 120%

