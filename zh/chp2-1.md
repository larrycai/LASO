---
layout: post
title: 内部结构框图 
---

## 内部结构框图 ##

### 目录结构
	一、Overview
		1. overview
			block diagram
		2. memory map
			System Memory Map
			SFRs (Special Function Register)
				0xE0000000 - 0xFB6FFFFF (max-512M)
				真实的存储容量：寄存器的个数 * 4bytes
				以串口为例： 15个 * 4组 = 60个 * 50 = 3K * 4 = 12K
		3. ball map
			pin assignment
			signal description
				UART-RxD0/TxD0 CTS0/RTS0
	二、System
		1. GPIO
		2. Clock
		3. Power
		4. boot sequence
	三、Bus
		1. AXI/AHB
	四、Interrupt
		1. Vectored Interrupt Controller
	五、Memory
		1. DRAM => DDR memeory
		2. SROM => SRAM + ROM(Nor Flash)
		3. OneNand
		4. Nand
		5. Compact Flash
	六、DMA
		1. DMA Controller
	七、Timer
		1. PWM Timer
		2. System Timer
		3. Watchdog Timer
		4. RTC
	八、Connectivity
		1. UART
		2. IIC-bus
		3. SPI (serial peripheral interface)
		4. USB Host
		5. USB OTG
		6. SD/MMC
	九、Multimedia
		1. LCD
		2. CAM
		3. G3D
		4. CODEC
		5. TVOUT
		6. VIDEO
		7. MIXER
		8. IMAGE ROTATOR
		9. JPEG
		10. G2D
	十、AUDIO
		1. IIS
		2. AC97
		3. PCM
		4. ADC (TS)
		5. KeyPad
	十一、Security	

### S5PV210 Block Diagram
	PRODUCT OVERVIEW
	Block Diagram
		CPU (运算) (控制)
		BUS
		Controllers (特殊功能寄存器)
	Pin Assignment Diagram
	SIGNAL DESCRIPTIONS
	SPECIAL REGISTERS (SFRs)
	SYSTEM MANAGER
		System Memory Map (系统内存映射)
			0x4000000 = 0x40M = 64M
		System Manager Registers (10+)
	SFR
		Name + Address + R/W + desc. + Reset Value
		Bit-Field
	Timing 时序图
	Controller
		OVERVIEW
		Diagram
		SPECIAL REGISTERS
		Timing

### 芯片的一般结构		
	CORE - Cortex-A8
	MMU
	CACHE
	Regs (通用寄存器)
	ALU (运算器)
	BUS
		片内 - 地址线32bit
		片外 - 地址线取决于BANK的大小
	iRAM (SRAM)
	iROM
	Peripheral Controllers
		Memory cont.
		GPIO cont.
		UART cont.
		USB cont.
		IIC cont.
		SD cont.
		SPI cont.
		DMA cont.
		Interrupt cont.
		G3D, G2D
		HDMI
		CAMERA
		TVOUT
		IMAGE ROTATOR
		JPEG

### 数据手册应该怎样阅读？
	Overview
		CHIP Block Diagram, MemoryMap,
		Pin Assignment, Signal Description
		SFRs (how many, address range)
		Controllers (how many)
	System
		Clock (BUS), Power
		Boot Sequence (启动/引导流程)
		GPIO
	Device
		UART
		NandFlash
		Memory (DDR)
		DMA
		Interrupt
		PWM Timer
			-> mini OS porting
		LCD + TS
		AUDIO
		DM9000
		SD
		Security

<br> <br> 
<div> <a href="chp1-4.html">上一节</a> &nbsp;&nbsp; | &nbsp;&nbsp; <a href="chp2-2.html">下一节</a> </div> <br> <br>