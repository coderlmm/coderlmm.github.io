---
title: 计算机网络自顶向下方法读书笔记（第一章）
date: 2019-05-03
tags: 
    - network
catalog: true
---

2019.05.13 号周一开始了第三期的读书活动「计算机网络自顶向下方法」，由于自己拖延加上后来流感感染高烧感冒导致现在才开始动笔写作业，甚是惭愧。

本章简单，多是概念性的知识。

网络中的是设备通过通信链路和分组交换机链接到一起，其中各个设备要想完成信息交换，也就是数据的传输，必须有一个统一的协议才行。就好比人们平时沟通交流所用的语言一样，语言不通，沟通的可能性基本为零。

因特网中设计的协议非常多，比如硬件实现的协议控制了在两块网卡间的比特流，拥塞控制协议控制了发送方和接收方之间的传输速率，但其中最重要的两个协议还属 TCP 和 IP 协议。

两台计算机之间若想进行数据交换，则必须相连，现实生活中的设备千千万，如果每两两相连的话则不太可能，于是出现分组交换技术。这真是一项伟大的发明。

### 协议层次

五层因特网协议栈：应用层，运输层，网络层，链路层，物理层。

七层 OSI 参考模型：应用层，表示层，会话层，运输层，网络层，链路层，物理层。

分层带来的最大的好处就是可以分而治之，各层之间不相互依赖其具体实现，只要每层做好自己分内的事就可以了。

### 网络攻击

+ 病毒可以入住主机
+ DoS 攻击
+ 网络中传输的数据包有可能被截获
+ IP 哄骗