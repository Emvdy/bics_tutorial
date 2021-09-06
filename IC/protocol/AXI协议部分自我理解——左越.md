# AXI笔记

[TOC]

## outstanding

outstanding是一种“同时”读写的特性。

对于**主设备**，可以支持对不同从设备进行同时读写，最大支持N个，N大小由主设备->从设备接受地址数据FIFO深度->从设备发放数据FIFO深度->主设备接受数据FIFO深度决定；

对于**从设备**，可以支持被连续写地址和读地址，这就要求从设备需要FIFO或者寄存器缓存地址等信息的功能。

## 信号理解

**地址传输：**

`AxLEN`代表burst的拍数，支持`1-16`位，即`[3:0]+1`；

`AxSIZE`代表burst的每拍数据最大宽度（字节数），即$2^{[3:0]} Bytes$

**数据传输：**

`WSTRB`代表每拍数据的片选信号，当`WSTRB[n]`为高时，即`WDATA[8n+7:8n]`选通。N位数据对应$log_{2}^{N}$位选通位。

## 交易顺序ID（我的理解）

AXI协议支持乱序交易。

每个通道都要标注`ID`，包含`AxID，xID，BID`，每个设备都有特定的”`ID`代码段“，每个`ID`代表某设备一次事件传输。

不同`ID`之间**可以乱序**传输，相同`ID`**必须顺序**传输。

## 依赖关系中箭头符号

​	双箭头：double-headed arrows point to signals that must be asserted only after assertion of the signal at the start of the arrow.

​	单箭头：single-headed arrows point to signals that can be asserted before or after the signal at the start of the arrow

