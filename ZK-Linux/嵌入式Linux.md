韦东山的教程需要有基础的人去看不会懵逼，他写的那种面向对象写裸机和驱动框架，需要多看几遍才能在脑海中印象，关键需要跟着写代码。或者可以看正点原子的嵌入式Linux教程，非常适合0基础的人去学习。

下面我总结下学习嵌入式Linux需要这几方面的基础：

## Linux基础命令

基本命令掌握如目录操作，文件操作操作，文件查找搜索，磁盘管理等，最关键要会gcc命令使用

## 掌握C语言

这部分学到指针那里，因为C语言的精髓是指针，不会指针等于不会C语言

## shell

重点掌握语法：

\- sed, tr, awk三剑客的用法

\- if,for,switch,while条件判断循环使用用法

\- 正则表达式

\- 特殊符号的用法

## Makefile

重点掌握

1、看[韦东山](https://www.zhihu.com/search?q=韦东山&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2721048089})第三期的[数码相框](https://www.zhihu.com/search?q=数码相框&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2721048089})中通用Makefile文件，看懂就好。不要求会写

2、自动生产[makefile](https://www.zhihu.com/search?q=makefile&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2973858783})的工具autotools



## 数据结构

这里的知识比较难啃，不经常很容易忘记。这里建议学会链表和队列，源码可以看看Linux内核里的list,c，queue.c和list.h，[queue.h](https://www.zhihu.com/search?q=queue.h&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2703411489})

## 文件IO

需要掌握的知识点

1、掌握Linux文件IO的一套系统调用API：open、read、write、[lseek](https://www.zhihu.com/search?q=lseek&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2973858783})，close等。

2、熟练写出文件拷贝等功能模块。

3、理解I/O、缓冲的概念。

在Linux下，一切皆文件，我们操作操作许许多多的外设（字符设备、套接字、文件等等）就像操作文件一样。要想知道如何操作文件和外设，我们就必须熟练掌握文件IO，这是我们学习Linux下面编程最基本的知识点。

## 系统编程

1、[进程与线程](https://www.zhihu.com/search?q=进程与线程&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2703411489})的概念

2、掌握常用的函数[fork函数](https://www.zhihu.com/search?q=fork函数&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2703411489})等api；

3、进程创建、回收；

4、常用的进程相关命令：ps、top，vmstat；

5、[进程间通信](https://www.zhihu.com/search?q=进程间通信&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2973858783})：信号量、消息队列、共享内存、管道、信号；

6、[守护进程](https://www.zhihu.com/search?q=守护进程&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2703411489})；

7、线程创建、同步互斥，互斥锁；

8、库的概念，什么是[动态库](https://www.zhihu.com/search?q=动态库&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2703411489})和静态库，如何自己制作动态库和静态库。

## [网络编程](https://www.zhihu.com/search?q=网络编程&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2703411489})

1、TCP/IP协议分层以及每一层的功能；不要看OSI，只要知道即可；

2、socket api的使用，

3、tcp、udp；C/S架构如何创建；

4、[tcpdump](https://www.zhihu.com/search?q=tcpdump&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2703411489})进行抓包，wireshark去看包

## 安全密钥学

1、信息安全技术：[加解密算法](https://www.zhihu.com/search?q=加解密算法&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2973858783})，信息炸药算法，数字签名，数字证书、

2、网络安全技术：TLS SSL,HTTPS

## UBOOT

掌握知识点

\- uboot的env设置

\- uboot启动流程

## 构建最小Linux系统

熟悉Linux启动流程，了解如何用Busybox，Buildroot构建最小的文件系统。就知道如何在如何在ARM板子跑应用程序。

## 内核裁剪

make menuconfig去配置裁剪内核驱动

## 字符驱动

\- 字符设备驱动概念inode、cdev、file_operations、file之间关系，理解里面的字符框架的OOP思想

\- platform总线和设备树的关系；

\- 同步互斥机制，[自旋锁](https://www.zhihu.com/search?q=自旋锁&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2973858783})、信号量、原子操作；

\- 按键的中断，等待队列，[poll](https://www.zhihu.com/search?q=poll&search_source=Entity&hybrid_search_source=Entity&hybrid_search_extra={"sourceType"%3A"answer"%2C"sourceId"%3A2973858783})的实现；

其他的用到了再去深刻学习

---

评论：突然发现不是很难？我对大部分都有印象？再补充点。看懂硬件原理图，各种通信协议，iic,spi,qspi,uart,iis,can。最好再看懂verlog代码，学习下dsp平台。最最重要的，是要学信号处理的算法。

