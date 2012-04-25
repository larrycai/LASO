---
layout: post
title: UART 控制器 - 串口寄存器配置
---

## 串口的寄存器 SFR:
	15 Regs	Register  Address
	控制类	6个
		ULCON0  0xE290_0000
		UCON0  0xE290_0004
		UFCON0  0xE290_0008
		UMCON0  0xE290_000C
		UBRDIV0  0xE290_0028
		UDIVSLOT0  0xE290_002C

	状态类	4个
		UTRSTAT0  0xE290_0010
		UERSTAT0  0xE290_0014
		UFSTAT0  0xE290_0018
		UMSTAT0  0xE290_001C

	数据类	2个
		UTXH0  0xE290_0020
		URXH0  0xE290_0024

	中断类	3个
		UINTP0  0xE290_0030
		UINTSP0  0xE290_0034
		UINTM0  0xE290_0038
		
## 查看 uboot 对串口的设置
	[FriendlyLEG-TINY210]# md 0xe2900000
	e2900000: 00000003 00000245 00000000 00000000    ....E...........
	e2900010: 00000000 00000000 00010000 00000010    ................
	e2900020: 00000000 0000000d 00000023 00000808    ........#.......
	e2900030: 00000005 00000005 00000000 00000000    ................
	e2900040: 00000000 00000000 00000000 00000000    ................
	e2900050: 00000000 00000000 00000000 00000000    ................
	e2900060: 00000000 00000000 00000000 00000000    ................
	e2900070: 00000000 00000000 00000000 00000000    ................
	e2900080: 00000000 00000000 00000000 00000000    ................
	e2900090: 00000000 00000000 00000000 00000000    ................

	ULCON0  	0xE290_0000 	00000003
	UCON0  		0xE290_0004 	00000245
	UFCON0  	0xE290_0008 	0
	UMCON0  	0xE290_000C 	0
	UBRDIV0  	0xE290_0028 	00000023
	UDIVSLOT0  	0xE290_002C 	00000808

	其中 FIFO control & Modem control 可以不用设置
	Timing setting
		ULCON0	0x3
			data bit: 8bit
			stop bit: 1bit
			parity: none
		UCON0	0x245
			enable Transmit & Receive MODE: 01 01	(INT&Polling)
			interrupt: disable
			dma: disable

	CLOCK setting
		UCON0	00:  PCLK (66M)
			--> 115200 bps (bit/second)
			--> 波特率并不是串口控制器的工作频率，串口控制器在接收采样时，是波特率的16倍

		66Mhz = 66000000hz

		分频因子 = 66000000 / (115200*16) - 1
		(分频因子 + 1) = PCLK/(bps*16)

		UBRDIV0:  0x23 = (66000000)/(115200*16)-1= 35
		UDIVSLOT0:
	

<br> <br> 
<div> <a href="chp5-4.html">上一节</a> &nbsp;&nbsp; | &nbsp;&nbsp; <a href="chp5-6.html">下一节</a> </div> <br> <br>