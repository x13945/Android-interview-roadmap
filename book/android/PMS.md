# PackageManagerService

## 简介

**PackageManagerService**（简称 PMS），是 Android 系统核心服务之一，处理包管理相关的工作，常见的比如安装、卸载应用等

## 原理

#### 安装包校验

安装包中一般有如下三个文件：

- MANIFEST.MF －－ 记录各文件的hash值。
- CERT.SF －－ 证书签名文件。
- CERT.RSA －－ 证书

第一步会先校验证书文件是否和已安装Apk相同。如果想相同则会校验CERT.SF和MANIFEST.MF。而如果第三方开发者修改了class文件，则清单文件就会对不上。如果修改了清单文件，则CERT.SF就会对不上。如果修改了CERT.SF，则要原来的证书才能加吗通过。



## 参考

- [Android apk文件结构及其安装,校验流程_般若程序蝉(prajna.top)的专栏-CSDN博客](https://blog.csdn.net/kartorz/article/details/89337530)