---
layout: post
title: 源码开放学ARM - NandFlash 控制器 - NandFlash 时序图
---

## Nand Flash Timing 时序
	READ ID Timing (p31)
		CLE 命令周期 写1次 90h		
		ALE 地址周期 写1次 00h
		DAT 数据周期 读5次 id = 0x EC DA 10 95 44 

	READ page Timing (p23)
		CLE 命令周期 写1次 00h
		ALE 地址周期 写5次 
		CLE 命令周期 写1次 30h
		忙等待周期 R/nB 高有效
		数据周期 读2048次data + 64次ECC




[上一节](chp7-2.html)  |  [目录索引](../index.html)  |  [下一节](chp7-4.html)
