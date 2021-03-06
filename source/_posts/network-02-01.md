---
title: 计算机网络自顶向下方法读书笔记（第二章之一）
date: 2019-05-10
tags: 
    - network
catalog: true
---

客户--服务器体系结构，有一个总是打开的主机成为服务器。具有固定的，周知的 IP 地址。

### 进程通信

不同主机间的进程通信。

网络进程通信，很明显至少是两个进程，他们通过网络互相发送报文。若想通过网络发送报文，报文则必须经过发送方的应用层 -> 运输层 -> 网络层 -> 链路层 -> 物理层，再到接收方物理层 -> 链路层 -> 网络层 -> 运输层 -> 应用层，方而完成报文的发送和接收。就好比你从一栋大楼的最高层去往隔壁大楼的最高层一样，肯定要先下到底面，然后在从底面上去隔壁楼。

问题来了，应用层是如何和传输层发送数据交换的呢，套接字。这是一个软件接口，是同一台主机内应用层与传输层之间的接口，也叫「应用程序编程接口」。现在知道怎么发送了，那接收方的地址怎么确定呢，一个是主机地址，一个是应用程序地址，答案就是 **IP 地址 + 端口号**。这样接收方接受到数据时就可以根据端口号进行数据分发了。

选择传输协议时需注意以下几点：

1. 可靠数据传输，就是数据能否一定到达目的地
2. 吞吐量
3. 定时（笔者不太晓得这个定时啥用处）
4. 安全性

运输层跑的协议主要是 TCP 协议，该协议是面向连接的，可靠的数据传输协议。安全性可以通过 SSL 来保证。注意，SSL 不是与 TCP/UDP 在相同层次上的第三种运输协议，而是一种对 TCP 的加强。

UDP 是无连接的，不可靠数据传输服务，同时有可能是乱序的。

**今天的因特网通常可以为时间敏感应用提供满意的服务，但它不能提供任何定时和带宽保证。**

### 应用层协议

应用层使用最广泛的便是 HTTP 协议，也叫超文本传输协议。该协议是无状态的，但是可以通过标识码即 sessionID 来表示会话信息，这得益于返回的 Set-cookie 机制。

FTP 协议使用两个并行的 TCP 连接来传输文件，一个用于控制连接，一个用于数据连接。FTP 服务器必须在整个会话期间保留用户的状态。

SMTP 电子邮件协议。

SMTP 不使用中间邮件服务器，A 邮件客户端 --> A 邮件服务器 --> B 邮件服务器 --> B 邮件客户端。

「A 邮件服务器 --> B 邮件服务器」的过程通过 SMTP 协议推过去，因为是 A 发起的连接。这也是 SMTP 和 HTTP 的主要差别，HTTP 主要是由获取文件方发起连接请求，属于**拉协议**，SMTP 主要是由发送文件方发起连接，属于**推协议**。

第二个区别就是 SMTP 要求每一个报文使用 7 比特的 ASCII 码格式。