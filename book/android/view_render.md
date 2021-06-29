# View渲染

## 简介

View的渲染过程，离不了三大方法

- onMeasure
- onLayout
- onDraw

## 原理解析

### onMeasure

- MeasureSpec 高两位类型，低32位大小

- 布局类型

    - parent EXACTLY

        - | Child 类型   | 结果    | 尺寸        |
            | ------------ | ------- | ----------- |
            | 指明尺寸     | EXACTLY | child尺寸   |
            | MATCH_PARENT | EXACTLY | parent size |
            | WRAP_CONTENT | AT_MOST | parent size |

    - parent AT_MOST

        - | Child 类型   | 结果    | 尺寸        |
            | ------------ | ------- | ----------- |
            | 指明尺寸     | EXACTLY | child尺寸   |
            | MATCH_PARENT | AT_MOST | parent size |
            | WRAP_CONTENT | AT_MOST | parent size |

    - parent UNSPECIFIED

        - | Child 类型   | 结果        | 尺寸        |
            | ------------ | ----------- | ----------- |
            | 指明尺寸     | EXACTLY     | child尺寸   |
            | MATCH_PARENT | UNSPECIFIED | parent size |
            | WRAP_CONTENT | UNSPECIFIED | parent size |




## 参看

-  [Android 自定义View之Measure过程 - 简书](https://www.jianshu.com/p/23519665ff32)
- [Android Activity创建到View的显示过程 - 简书](https://www.jianshu.com/p/7e260b7890a3)
- [Android 输入事件一撸到底之源头活水（1） - 简书](https://www.jianshu.com/p/16f3f4c333cc)
- [Android 输入事件一撸到底之DecorView拦路虎（2） - 简书](https://www.jianshu.com/p/c3843bf6545b)
- [Android 输入事件一撸到底之View接盘侠（3） - 简书](https://www.jianshu.com/p/bc133ed02b1e)