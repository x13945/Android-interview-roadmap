# MAT-Memory Analyzer Tool

## 简介

MAT是常用的Java堆内存分析工具，有独立运行版本，也有Eclipse的插件。

## 重要概念

我们可以用Eclipse或者其他工具，到处Java的堆文件，一般是Hprof格式。如果是Android，需要用sdk中自带的hprof-conv转换一下才能被MAT使用

- Shallow heap 对象本身的堆占用
- Retained heap 对象加上其引用对象的堆占用
- incoming references 当前对象被其他对象引用
- outGoing references 当前对象引用的对象

## 参考

- [内存分析工具MAT的使用入门 - 云+社区 - 腾讯云](https://cloud.tencent.com/developer/article/1676945#:~:text=内存分析工具MAT (Memory Analyzer Tool)是一款 JVM 的内存分析工具，在实际的工作中可以帮助我们解决生成上内存占用过高等问题。 我之前用,MAT 是在 eclipse上使用，前者是后者的一个插件。 后来换到 IDEA 才知道原来 MAT 也有独立的可运行版本。)

