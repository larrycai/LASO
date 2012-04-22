---
layout: post
title: 特殊功能寄存器
---

## 特殊功能寄存器

### 关于内核，控制器，总线和外设之间的关系
	内核：Cortex-A8 (CORE)
		寄存器 Regs (R0-R15, CPSR)
		指令集 Ins (add/sub, ldr/str)
		总线 (访存指令)
	地址概念：
		cpu：32bit	ldr r0, [r1] 	(r1:addr)
			1)SRAM:
			2)SFR:
			--------------------------
			3)DDR:
			4)Device internal memory:
	总线概念：
		片内总线
			地址线-32bit	由 地址寄存器的字节数 决定
		片外总线
			地址线-29bit	由 设计cpu时，外接的单个存储器件的最大容量 决定
		内存控制器
			通过把 32bit 的最大访存范围，分割为若干个 bank 来进行统一访问
	外设控制器概念：
		外设 = 可见(接插件/关联芯片/连接线) + 不可见(外设控制器)
		外设控制器 = 寄存器接口 <---- 黑匣子(类似函数库.o) ---> 外设工作的时序图
	总结关系：
		都是涉及到裸板驱动 (无操作系统/无MMU参与)
		本质上除了运算之外，都是变成为对地址的读写
		C语言的指针，在本阶段，占一个很重要的角色。
	

<br> <br> 
<div> <a href="chp2-2.html">上一节</a> &nbsp;&nbsp; | &nbsp;&nbsp; <a href="chp2-4.html">下一节</a> </div> <br> <br>