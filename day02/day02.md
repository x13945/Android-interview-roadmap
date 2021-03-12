## 目标

- 算法 4个番茄
- kotlin 4个番茄
- Android 4个番茄
- Java 4个番茄

## 进度

### 1. Java 6个番茄

- 泛型

  最初时为了创建容器类，可以兼容更多的类型，`Java SE5`中引入。不像C++，Java的泛型是在编译期做的检测，会被擦除类型信息。因此无法在运行期获得具体类型。

  - 泛型类
  - 泛型方法 *优先使用*

  - 型变 类型转换后的关系 [PECS (Producer Extends Consumer Super)?](https://stackoverflow.com/questions/2723397/what-is-pecs-producer-extends-consumer-super)
    - 逆变 super
      - 限定下界。`? super T`只能使用T或者T的子类
    - 协变 extends
      - 限定上限。`? extends T`只能使用T或者T的父类
    - 不变

