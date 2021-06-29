# 插件话

## 简介

Android的插件话，通常是指四大组件的动态插拔使用。由于Android中限定，只有在`AndroidManifest.xml`文件中定义过的四大组件才能正常启动。因而就有两种流派

- 代理派

    现在`AndroidManifext`中定义一个壳或者占位组件，然后通过动态代理在运行时代理调用插件中的生命周期。例如腾讯开源的shadow

- hook派

    这种通常是hook四大组件的创建过程，动态替换四大组件实际启动的累

## 原理

- ClassLoader
    - Java
        - BootstrapClassLoader 加载 JVM 运行时的核心类
        - ExtensionClassLoader 加载 JVM 的扩展类
        - AppClassLoader 加载 classpath 里的 jar 包和目录
    - Android [Android类加载器ClassLoader - Gityuan博客 | 袁辉辉的技术博客](http://gityuan.com/2017/03/19/android-classloader/)
        - PathClassLoader
        - DexClassLoader

## 参考

- [【Android 修炼手册】常用技术篇 -- Android 插件化解析