## 目标

- Android 4个番茄
- 算法 4个番茄

## 进度

### Android 6个番茄

#### View 绘制

- onMeasure [Android 自定义View之Measure过程 - 简书](https://www.jianshu.com/p/23519665ff32)

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
        
                
    
- onLayout 

### 算法 2个番茄

- 排序算法

    | 算法 | 是否是原地排序 | 是否稳定 | 最好时间复杂度 | 最坏  | 平均  |
    | ---- | -------------- | -------- | -------------- | ----- | ----- |
    | 冒泡 | 是             | 是       | O(n)           | O(n²) | O(n²) |
    | 插入 | 是             | 是       | O(n)           | O(n²) | O(n²) |
    | 选择 | 是             | 否       | O(n²)          | O(n²) | O(n²) |

    