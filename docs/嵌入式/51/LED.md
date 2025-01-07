# LED

## LED介绍

发光二极管，Light Emitting Diode

> 开发板上的电阻数字表示，102 = 1K，“102”解释为“10”后再加“2”个“0”，即变成“1000”

单片机中，CPU控制寄存器，一个寄存器分为8个部分，每个部分通过一个驱动器控制一个IO口。

CPU给寄存器传递，1代表高电平，0代表低电平。可以用一个8位二进制数赋值给寄存器，从而控制8个IO口的电平。



## 点亮一个LED

```c
#include <REGK52.H>

void main(){
    while(1){
        P2 = 0xFE; // 1111 1110
    }
}
// P2端口的状态会不断地被重置为0xFE。
```

```c
#include <REGK52.H>

void main(){
    P2 = 0xFE; // 1111 1110
    while(1){
    }
}
// P2端口的状态只在程序开始时被设置为0xFE一次，之后除非有其他代码介入，否则不会改变。
```

> // #include <REGK52.H>
> AT89X52.H
> 相关寄存器的信息都存储其中

## LED闪烁

```c
#include <REGK52.H>
#include <INTRINS.H>

void Delay500ms(void)	//@12.000MHz 
{
	unsigned char data i, j, k;

	_nop_();
	i = 4;
	j = 205;
	k = 187;
	do
	{
		do
		{
			while (--k);
		} while (--j);
	} while (--i);
}

void main(){
    while(1){
        P2 = 0xFE;
        Delay500ms();
        P2 = 0xFF;
        Delay500ms();
    }
}
```

> 实现延时的工具：
>
> STC-ISP中的“软件延时计算器”，当前开发板的晶振是12MHz，由于是STC89C系列的单片机，所以指令集改成“STC-V1”，最后生成一个`Delay()`函数 

## LED流水灯

```c
#include <REGX52.H>
#include <INTRINS.H>

void Delay500ms(void)	//@12.000MHz 
{
	unsigned char data i, j, k;

	_nop_();
	i = 4;
	j = 205;
	k = 187;
	do
	{
		do
		{
			while (--k);
		} while (--j);
	} while (--i);
}

void main(){
    while(1){
        P2 = 0xFE;
        Delay500ms();
        P2 = 0xFD;
        Delay500ms();
        P2 = 0xFB;
        Delay500ms();
        P2 = 0xF7;
        Delay500ms();
        P2 = 0xEF;
        Delay500ms();
        P2 = 0xDF;
        Delay500ms();
        P2 = 0xBF;
        Delay500ms();
        P2 = 0x7F;
        Delay500ms();
    }
}
```

```c
// 改进
#include <REGX52.H>
#include <INTRINS.H>

void Delayms(unsigned int xms)	//@12.000MHz
{
	unsigned char data i, j;
	while(xms--){
		i = 2;
		j = 239;
		do
		{
			while (--j);
		} while (--i);
	}
}

void main(){
    while(1){
        P2 = 0xFE;
        Delayms(500);
        P2 = 0xFD;
        Delayms(500);
        P2 = 0xFB;
        Delayms(500);
        P2 = 0xF7;
        Delayms(500);
        P2 = 0xEF;
        Delayms(500);
        P2 = 0xDF;
        Delayms(500);
        P2 = 0xBF;
        Delayms(500);
        P2 = 0x7F;
        Delayms(500);
    }
}
```

