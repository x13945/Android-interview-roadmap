# ARouter

## 简介

ARouter是阿里开源的一个组件化路由框架。官方仓库地址在这里：[alibaba/ARouter: 💪 A framework for assisting in the renovation of Android componentization (帮助 Android App 进行组件化改造的路由框架)](https://github.com/alibaba/ARouter)

## 原理

1. 在编译时，通过javapoet生成特定的路由，拦截器，序列化组件。这些组件的名字开头都是特定的包名
2. 运行时，初次使用会扫描所有dex中的class，把符合1中类名规则的类收集起来
3. 调整。通过2种收集的路由表，进行跳转

### 加载优化

从上面流程可以看出，初次启动扫描路由表的过程十分耗时。于是官方提供了aouter-compile在编译时生成路由表

## 参考

- [阿里ARouter全面全面全面解析(使用介绍+源码分析+设计思路)_CallmeZhe的博客-CSDN博客](https://blog.csdn.net/CallmeZhe/article/details/112851137?utm_medium=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromMachineLearnPai2~default-1.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2~default~BlogCommendFromMachineLearnPai2~default-1.control)
- [square/javapoet: A Java API for generating .java source files.](https://github.com/square/javapoet)