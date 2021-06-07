# SharedPreferences

## 简介

SharedPreferences 是Android提供的一个轻量级key-value存储框架。

## 原理

SP的落盘文件是xml，初次加载会把xml加载到内存中，之后的修改如果是用apply方法，则会只修改内存数据；commit方法则会落盘处理。

### 数据修改

通过edit方法会生成一个Editor对象，之后的修改会放到Editor对象的map中，在apply的时候，才会通过同步锁来更新给sp对象。

### 权限控制

获取sp的时候，会有mode字段，其左右是借助selinux的文件权限功能，赋予文件访问权限。

### 跨进城

SP的mode中有个字段：Context.MODE_MULTI_PROCESS。这个不能实现跨进城，只是在在获取sp的时候，会立即从磁盘读一遍。实际上没有任何跨进城能力。

## 参考

- [SharePreference原理及跨进程数据共享的问题 - 简书](https://www.jianshu.com/p/4984f66f9a4b)