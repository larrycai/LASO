---
layout: post
title: 源码开放学ARM - 异常处理 - 异常处理流程
---

## 异常处理流程
### ARM 的软中断异常发生后，硬件做何响应？
	硬件要做6件事情，以发生SWI异常为例：
		1. 保存 (PC-4) -> LR_svc	(PC 是当前执行指令地址+8)
		2. 保存 CPSR -> SPSR_svc
		3. 修改 CPSR -> SVC mode
		4. 修改 CPSR I-bit -> disable IRQ
		5. 映射相应(USR ->) SVC 模式的寄存器
		6. 修改 PC -> 0x8
		
### cpu 内核跳转到 0x8 之后，软件需要做哪些工作？

PC 跳转到 0x8 之后，第一个问题是如何返回？ 包括两个返回：	
	
	1. 地址的返回 	mov pc, lr
	2. 模式的返回	movs pc, lr
	
	mov pc, lr	[0xe1a0f00e]   
	movs pc, lr	[0xe1b0f00e]   

直接返回没有实际意义，因此第二个问题是如何跳转到 swi_handler ？

	b   跳转	b    swi_handler	
		0xEA000000 | offset	offset计算公式 ( swi_handler - (0x8+8) ) / 4
		offset：代表从 PC 到 目标地址 之间相差的指令数
		
	ldr 跳转	ldr  pc, [pc, offset]
		0xE59FF000 | offset	offset计算公式 ( data_addr - (0x8+8) ) 
		offset：代表从 PC 到 数据存储地址 之间相差的字节数
		data_addr: 代表 存储目标地址的内存单元的地址，这个地址被看成为一个数据，用ldr从内存中读出来。

跳转到 handler 之后， handler 需要做哪些工作？

	swi_handler 要做以下工作：
		1. 保存现场： r0-r12, r14 压栈
			STMFD r13!, {r0-r12, r14}
		2. 进入异常处理: 
			BL	C_swi_handler		; 用C实现
		3. 恢复现场： r0-r12, pc 出栈
			A) LDMFD r13!, {r0-r12, pc}^
			B) LDMFD r13!, {r0-r12, r14}
			   movs pc, lr	
			将原来保存的 spsr 恢复给 CPSR




[上一节](chp8-2.html)  |  [目录索引](../index.html)  |  [下一节](chp8-4.html)
