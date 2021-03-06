# 热修复

## 简介

热修复不同于插件化，不需要考虑各种组件的生命周期，唯一需要考虑的就是如何能将问题的方法／类／资源／so 替换为补丁中的新方法／类／资源／so。
其中最重要的是方法和类的替换，所以有不少热修复框架只做了方法和类的替换，而没有对资源和 so 进行处理。

## 原理

热修复通常要替换的有三种资源：

1. Android中的资源文件

    InstantRun 通过反射addAssetPath，把新的资源添加到AssetManager中

2. so文件

    - 方法替换
    - 类似dex，反射注入so路径

3. Java 文件

    流派

    - native hook。在c++层修改方法类类对应的引用，进而达到热修复的目的

        - **优点**：
            补丁可以实时生效
            **缺点**：
            1. 兼容性差，由于 Android 系统每个版本的实现都有差别，所以需要做很多的兼容。（这也就是为什么上面提供的 demo 代码只能运行在 Android N 上，因为没有对其他版本做兼容）
            2. 开发需要掌握 jni 相关知识

    - dex 插桩

        - QQZone
        - 由于PathClassLoader从dex中加载class的时候，会从dex队列的前面开始找起。因此只要把hotfix dex通过反射放到数组头就行

    - dex 替换

        - tinker

    - InstantRun

        - 原理：在每个类中，新增changeQuickRedirect静态变量，在执行每个方法之前都判断这个变量是否存在，如果存在则替换。而patch也是通过放到dex猎豹的最前面来解决的

        - **优点**：

            1. 使用 java 实现，开发方便
            2. 兼容性好
            3. 补丁实时生效

            **缺点**：

            1. 代码是侵入比较高，需要在原有代码中新增逻辑，而且需要对方法进行插桩，将这里逻辑自动化处理
            2. 增大包体积

## 技巧

1. 不同dex下的class互相引用的时候，解决校验错误
    1. 原因是dex转odex的时候，如果互相引用的类都在一个dex中，会打上一个is pre verify的标识位。而热修复dex和原来引用它的部分可能会因为不在一个dex中而导致失败。
    2. QQZone的解决办法 给所有类通过字节码修改工具，都引用一个打在单独dex 中的类

## 参考

-  [全面解析 Android 热修复原理 - 知乎](https://zhuanlan.zhihu.com/p/75465215)
- [安卓App热补丁动态修复技术介绍](https://mp.weixin.qq.com/s?__biz=MzI1MTA1MzM2Nw==&mid=400118620&idx=1&sn=b4fdd5055731290eef12ad0d17f39d4a)