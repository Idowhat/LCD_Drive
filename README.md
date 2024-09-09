# LCD_Drive

记录一次修改lcd接口，来兼容正点原子开发板的pcb设计过程。

## 背景

在使用领航者开发板的时候，它对应的4.3寸的显示屏800x480分辨率的显示屏是专用于领航者zynq7020的。
于是我计划自己画一块PCB，从网上买一块4.3寸的显示屏，然后兼容正点原子的开发板。

## 液晶背光供电电路
  
LED背光要求的电压典型值是15V，而整体只有3.3V和5V，所以选择使用STI9287来进行升压。为控制电流使用了一个等效为10欧姆的电阻。EN控制外接到了开发板上，我这里使用了电阻限流，当然也可以对EN端口输入PWM波控制亮度。

<p align = "center">    
<img  src="https://github.com/Idowhat/img_video/blob/main/img_LCD/BL_Parameter.jpg?raw=true"  />
<img  src="https://github.com/Idowhat/img_video/blob/main/img_LCD/BL_Power.jpg?raw=true"   />
<img  src="https://github.com/Idowhat/img_video/blob/main/img_LCD/I_led.jpg?raw=true"   />
</p>


## 总结
总体电路原理图如下
<p align = "center">
<img src="https://github.com/Idowhat/img_video/blob/main/img_LCD/Schematic.jpg?raw=true" />
</p>

电源处都加入了电容滤波，电容触摸通信使用的是IIC，SCL引脚和SDA引脚处都加入了上拉电阻。

特别感谢嘉立创的每月免费打板，这一举措，让自己动手创做一些实用电路成为了可能。再次感谢。所以我这次将整个电路完全开源。
## 附录
我所购买的液晶屏的接口定义如下

<p align = "center">
<img src="https://github.com/Idowhat/img_video/blob/main/img_LCD/Pin_definition.jpg?raw=true"  />
</p>
