# init代码块

在Kotlin类的声明中，可以用init来声明一个代码块。如下：

```kotlin
class App : Application() {
    override fun onCreate() {
        super.onCreate()
        DimenUtils.setContext(this)
        XLog.d("App init")
    }

    init {
        XLog.d("init")
    }
}
```

其中的语句会在编译时插入到构造方法的末尾