# LeakCanary

## 简介

LeakCanary是square公司开发的一个内存泄漏检查工具。

## 原理

### 弱引用队列

当声明一个弱引用的时候，可以把一个队列附加上去。如果GC回收了这个弱引用对象，则会把他放到弱引用队列中。借此，我们可以观察那些对象没有被及时回收。

### 生命周期监听

1. Activity 借助Aplication的LifecycleListener，添加回掉
2. Fragment 和Activity类似
3. RootViewWatcher 反射WindowManagerGlobal，监听view的生命周期
4. ServiceWatcher 反射AMS中Service的创建，动态代理所有方法，过滤死亡方法：serviceDoneExecuting

在生命周期结束的时候，触发gc，然后检查弱引用队列，就可以知道哪些对象没有被及时回收。然后通过Debug类的api，dumpHeap。之后用shark工具分析引用链，用通知提示用户。

## 参考

- [LeakCanary 内存泄漏原理完全解析 - 简书](https://www.jianshu.com/p/59106802b62c)