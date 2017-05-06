---
title: Two Method of Cache Read/Write in Computer Achitecture
date: 2017-05-04 23:21:18
tags: 标签　CA
---
当写入Cache操作时，有两种不同的模式，相对应的当Cache miss 发生的时候，也有两种对应的优化解决方法，下面我们就搭配直观的流程图，深入介绍一下Cache中的细节问题。
<!--more-->
## Write cache 的两种模式

- write through：CPU向cache写入数据时，同时向memory也写一份，使cache和memory的数据保持一致。优点是简单，缺点是每次都要访问memory，速度比较慢。
- write back：CPU更新cache时，只是把更新的cache的Dirty bit设置为１，表示已经写过，并不同步更新memory。只是在cache区要被新进入的数据取代时，才更新memory。这样做的原因是考虑到很多时候cache存入的是中间结果，没有必要同步更新memory。优点是CPU执行的效率提高，缺点是实现起来技术比较复杂。

## Write-cache miss 写缺失的两种情况

- Write allocate方式将写入位置读入缓存，然后采用write-hit（缓存命中写入）操作。写缺失操作与读缺失操作类似。
- No-write allocate方式并不将写入位置读入缓存，而是直接将数据写入存储。这种方式下，只有读操作会被缓存。

#### 通常Write-back采用Write allocate方式，而Write-through采用No-write allocate方式

---
# Write-through 流程图(读/写)
!["Write-through 流程图(读/写)"](/img/cache01.jpg)
# Write-back 流程图(读/写)
!["Write-back 流程图(读/写)"](/img/cache02.jpg)
