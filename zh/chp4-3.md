---
layout: post
title: 时钟管理 - 锁相环和分频器
---

## 锁相环和分频器

### 锁相环 PLL
	PLL: Fin -> Fout 倍频		XPLL_CON
	MUX: 0/1 选择器 SRC选择源	CLK_SRC
	DIV: /2-16 分频器 DIV		CLK_DIV

	REGISTER DESCRIPTION
	OM[0]: cpu pin OM[0]=0, XXTI=24M
	Fin_PLL: 24Mhz
	APLL: APLL_CON: e0100100: 0xa07d0301 => 1000Mhz


### 分频器 Divider
	Mux_APLL: CLK_SRC0, 0xe0100200: 10001111 [0]=> 1
	Mux_MSYS: CLK_SRC0, 0xe0100200: 10001111 [16]=> 0
	DIV_APLL: CLK_DIV0, 0xE0100300: 14131440 [2:0]=> 0 = /1
	DIV_APLL: CLK_DIV0, 0xE0100300: 14131440 [10:8]=> 100 = /5


### 举例: UART 串口时钟 PCLK_PSYS 的生成过程
	Mux_PSYS: CLK_SRC0, 0xe0100200: 10001111 [24]=>0  Fout_mpll

	MPLL: MPLL_CON: 0xa29b0c01 => 667Mhz (p358)
		Equation to calculate the output frequency:
		FOUT = MDIV X FIN / (PDIV X 2^SDIV)
		Fout = (0x29b)*24M/(12 * 2^1) = 667Mhz
	Mux_MPLL: CLK_SRC0, 0xe0100200: 10001111 [4]=> 1  Fout_mpll

	DIV_HCLKP: CLK_DIV0, 0xE0100300: 14131440 [27:24]=> 0100 = /5
	DIV_PCLKP: CLK_DIV0, 0xE0100300: 14131440 [30:28]=> 001 = /2

	

<br> <br> 
<div> <a href="chp4-2.html">上一节</a> &nbsp;&nbsp; | &nbsp;&nbsp; <a href="chp5-1.html">下一节</a> </div> <br> <br>