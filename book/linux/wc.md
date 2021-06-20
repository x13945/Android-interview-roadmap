# WC

## 简介

`WC`是Linux上的一个用来统计数量的工具。

```shell
Usage: wc [OPTION]... [FILE]...
    -c, --bytes, --chars print the byte counts
    -l, --lines print the newline counts
    -L, --max-line-length print the length of the longest line
    -w, --words print the word counts
        --help display this help and exit
        --version output version information and exit
```

## 示例

1. 统计当前目录下，py文件数量

    ```shell
    find . -name "*.py" |wc -l
    ```

2. 统计当前目录下，所有py文件行数

    ```shell
    find . -name "*.py" |xargs cat|wc -l
    ```

3. 统计当前目录下，所有py文件行数，并过滤空行

    ```shell
    find . -name "*.py" |xargs cat|grep -v ^$|wc -l
    ```

    