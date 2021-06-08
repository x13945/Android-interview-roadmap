# CAS(compare and swap)

## 简介

CAS 是 Java 并发中所谓 lock-free 机制的基础。

他通常在应用层用死循环的形式等待锁，而不是进入内核态。因而有更高的性能。

## 原理

- AtomicInteger
    - getAndIncrement
        - sun.misc.Unsafe.getUnsafe().getAndAddInt
            - 低层就是cas循环等待
    - 避免过多的自旋