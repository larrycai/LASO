---
layout: post
title: GPIO 控制器内部结构
---

## GPIO 控制器内部结构

General Purpose Input/Output (p92-p352)

	（看完 GPIO 章节，要解决哪些问题？）
	1) 237 multi-functional input/output port pins
		34 general port groups
	2) GPIO <---> peripheral controller (signal mux)
	3) GPIO Block Diagram
		APB bus (addr + data) *(int *)0xE0000000 = 0x1234;
		Register File (GPIO SFRs)
		Mux Control (functional)
		Interrupt Control (Interrupt cont.)
	4) Pin Mux Description
		pin name -> GPIO name
		default function
	

<br> <br> 
<div> <a href="chp2-4.html">上一节</a> &nbsp;&nbsp; | &nbsp;&nbsp; <a href="chp3-2.html">下一节</a> </div> <br> <br>