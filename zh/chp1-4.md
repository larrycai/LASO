---
layout: post
title: 基本开发流程 
---

## 1.4 基本开发流程

###1.4.1 开发工具是如何使用的？
	armcc main.c -> .axf
	armasm start.s -> .o
	armlink -ro-base 0x?? -entry xxx -> .axf
	fromelf -bin -> .bin
	fromelf -c -> .txt (反汇编)
	

<br>
<br>
	
<div>
<a href="chp1-3.html">上一节</a> &nbsp;&nbsp; | &nbsp;&nbsp; <a href="chp2-1.html">下一节</a> 	
</div>

<br>
<br>