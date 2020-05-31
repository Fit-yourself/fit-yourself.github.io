+++

date = 2020-03-22T18:56:49
description="这个破东西吓我的3个月没学单片机。"
tags = ["C"]
categories = ["折腾Time"]
title = "对定时器的认识"

+++

了解：

- 机器周期
- 时间周期是机器周期的N倍
- 频率 : 11.0592 Hz

定时器位于单片机上，非外部。

不管三七二十一： 

1. 设置TMOD 模式  其为 1bit
2. 设置TH0 TL0 初值 寻址的bit
3. TR0 置1  TCON 的一个bit
4. 判断 TF0 位置  TCON 的一个bit

| 7    | 6    | 5    | 4    | 3    | 2    | 1    | 0    |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| TF1  | TR1  | TF0  | TR0  | IE1  | IT1  | IE0  | IT0  |

复位值均为0；

unsigned char code LED[] = {0xC0,0xF9,0xA4,0xB0,0x99,0x92,0x82,0xF8,0x80,0x90,0x88,0x83,0xC6,0xA1,0x86,0x8E};