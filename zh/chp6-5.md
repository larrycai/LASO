---
layout: post
title: 源码开放学ARM - SDRAM 控制器 - SDRAM 寄存器配置
---

## SDRAM 寄存器配置
	[FriendlyLEG-TINY210]# md 0xF0000000
	f0000000: 0ff02330 00202400 20e00323 00e00323    0#...$ .#.. #...
	f0000010: 00110400 ff000000 79101003 00000086    ...........y....
	f0000020: 00000000 00000000 ffff00ff 00000000    ................
	f0000030: 00000618 2b34438a 24240000 0bdc0343    .....C4+..$$C...
	f0000040: 00001db7 00000000 60000000 00000000    ...........`....
	f0000050: 000005b2 00000000 00000000 00000000    ................
	f0000060: 00000000 00000000 00000000 00000000    ................
	f0000070: 00000000 00000000 00000000 00000000    ................
	f0000080: 00000000 00000000 00000000 00000000    ................
	f0000090: 00000000 00000000 00000000 00000000    ................
	f00000a0: 00000000 00000000 00000000 00000000    ................
	f00000b0: 00000000 00000000 00000000 00000000    ................				
				
	DDR 寄存器配置参数
		data width: 32bit
		row address bit: 14bit
		col address bit: 10bit
		memory type: DDR2
		number of banks: 8banks (DDR chip)
		Average Periodic Refresh Interval: 0x618
			7.8us * 200Mhz = 1560 = 0x618
			7.8us : 刷新周期
		Timing 时间参数
			...
	



[上一节](chp6-4.html)  |  [目录索引](../index.html)  |  [下一节](chp6-6.html)
