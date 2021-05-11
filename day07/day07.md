## 目标

- Android 6个番茄
- 算法 4个番茄

## 进度

- Android 12个番茄

    - View 绘制流程解析

        - [Android Activity创建到View的显示过程 - 简书](https://www.jianshu.com/p/7e260b7890a3)

    - 点击事件分发解析

        - 底层分发给ViewRootImpl，然后通过责任链分发到App层的DecorView，然后在ViewTree 中分发
            - [Android 输入事件一撸到底之源头活水（1） - 简书](https://www.jianshu.com/p/16f3f4c333cc)
            - [Android 输入事件一撸到底之DecorView拦路虎（2） - 简书](https://www.jianshu.com/p/c3843bf6545b)
            - [Android 输入事件一撸到底之View接盘侠（3） - 简书](https://www.jianshu.com/p/bc133ed02b1e)
            - 关于View的点击处理，如果想扩大点击返回，有两种方式
            - 1. 设置padding，让view变大
                2. 设置TouchDelegate，扩大自己的可点击范围 [Android TouchDelegate详解及优化 - 简书](https://www.jianshu.com/p/cb5181418c7a)

    - 组件化

    - 插件话

        - ClassLoader
            - Java
                - BootstrapClassLoader 加载 JVM 运行时的核心类
                - ExtensionClassLoader 加载 JVM 的扩展类
                - AppClassLoader 加载 classpath 里的 jar 包和目录
            - Android [Android类加载器ClassLoader - Gityuan博客 | 袁辉辉的技术博客](http://gityuan.com/2017/03/19/android-classloader/)
                - PathClassLoader
                - DexClassLoader
    
    - 热修复 [全面解析 Android 热修复原理 - 知乎](https://zhuanlan.zhihu.com/p/75465215)
    
        - 热修复不同于插件化，不需要考虑各种组件的生命周期，唯一需要考虑的就是如何能将问题的方法／类／资源／so 替换为补丁中的新方法／类／资源／so。
            其中最重要的是方法和类的替换，所以有不少热修复框架只做了方法和类的替换，而没有对资源和 so 进行处理。
    
        - 资源
            
            - InstantRun 通过反射addAssetPath，把新的资源添加到AssetManager中
            
        - so文件

            - 方法替换
            - 类似dex，反射注入so路径
        
        - Java
          
          - 流派
        
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
        
        - [安卓App热补丁动态修复技术介绍](https://mp.weixin.qq.com/s?__biz=MzI1MTA1MzM2Nw==&mid=400118620&idx=1&sn=b4fdd5055731290eef12ad0d17f39d4a)
          
            - 不同dex下的class互相引用的时候，会报一个校验错误
                - 原因是dex转odex的时候，如果互相引用的类都在一个dex中，会打上一个is pre verify的标识位。而热修复dex和原来引用它的部分可能会因为不在一个dex中而导致失败。
                
                - QQZone的解决办法 给所有类通过字节码修改工具，都引用一个打在单独dex 中的类
                
                    