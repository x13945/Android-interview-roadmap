# 事件分发

## 简介

Android的事件分发，会由Window把硬件的中断，发送给ViewRootImpl。然后基于责任链App层的DecorView，然后在ViewTree 中分发。

## 原理

ViewGroup会缓存处理了Down事件的View，在后续的Move和Up事件中，便于分发。但是在早期版本中，缓存的是对象本身，而新版本中，缓存的是一个MotionTarget链表，最近处理Down的View会被放到链表头部。



## 技巧

- 	1. 设置padding，让view变大
		
      2. 设置TouchDelegate，扩大自己的可点击范围 [Android TouchDelegate详解及优化 - 简书](https://www.jianshu.com/p/cb5181418c7a)

## 参考

- [android多种滑动冲突的解决方案 - 移动开发 - 亿速云](https://www.yisu.com/zixun/216908.html)
- [Android 输入事件一撸到底之源头活水（1） - 简书](https://www.jianshu.com/p/16f3f4c333cc)
- [Android 输入事件一撸到底之DecorView拦路虎（2） - 简书](https://www.jianshu.com/p/c3843bf6545b)
- [Android 输入事件一撸到底之View接盘侠（3） - 简书](https://www.jianshu.com/p/bc133ed02b1e)