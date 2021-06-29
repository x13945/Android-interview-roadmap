# 事件分发

## 简介

Android的事件分发，会由Window把硬件的中断，发送给ViewRootImpl。然后基于责任链依次在ViewTree中查找特定的View来处理

## 原理

ViewGroup会缓存处理了Down事件的View，在后续的Move和Up事件中，便于分发。但是在早期版本中，缓存的是对象本身，而新版本中，缓存的是一个MotionTarget链表，最近处理Down的View会被放到链表头部。

## 参考

- [android多种滑动冲突的解决方案 - 移动开发 - 亿速云](https://www.yisu.com/zixun/216908.html)