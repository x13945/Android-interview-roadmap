# PackageManagerService

## 简介

**PackageManagerService**（简称 PMS），是 Android 系统核心服务之一，处理包管理相关的工作，常见的比如安装、卸载应用等

## APK加载

系统启动后，system_server进城会启动，然后会启动PMS，之后PMS会加载所有的Apk，从AndroidManifest中获得包信息，包括权限信息

## 敏感权限鉴权

### Android6以下

1. 根据PMS解析的申请权限数据，对应用添加gid

2. 启动应用进程时，指定所有对应的gid

    例如：android.permission.WRITE_EXTERNAL_STORAGE

    1. 应用在AndroidManifest.xml中申请android.permission.WRITE_EXTERNAL_STORAGE

    2. 安装后，PMS解析该应用，并为该应用添加sdcard_rw的组ID。

    3. 启动该应用进程时，使用上面解析的gid。

### Android6 及以上

## 原理

#### 安装包校验

安装包中一般有如下三个文件：

- MANIFEST.MF －－ 记录各文件的hash值。
- CERT.SF －－ 证书签名文件。
- CERT.RSA －－ 证书

第一步会先校验证书文件是否和已安装Apk相同。如果想相同则会校验CERT.SF和MANIFEST.MF。而如果第三方开发者修改了class文件，则清单文件就会对不上。如果修改了清单文件，则CERT.SF就会对不上。如果修改了CERT.SF，则要原来的证书才能加吗通过。



## 参考

- [Android apk文件结构及其安装,校验流程_般若程序蝉(prajna.top)的专栏-CSDN博客](https://blog.csdn.net/kartorz/article/details/89337530)
- [Android之PMS流程分析_calm1516的专栏-CSDN博客](https://blog.csdn.net/calm1516/article/details/114170934)