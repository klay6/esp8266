# 认识继电器(Relay),使用微动开关控制高压电路，智能灯泡第一步
### 一、材料准备
我们需要提前准备的材料:  
1、光耦继电器模块(光耦隔离,支持高低电频驱动) * 1  
2、微动开关 * 1       
3、esp8266开发板 * 1块    
4、micropython开发环境(包含IDE，以及程序上传相关耗材)  

### 二、继电器介绍   
简单的认识继电器，  
![](连接.jpg)
电器参数了解  
5VDC  驱动继电器电池圈工作的电压(直流电源)  
10A 250VAC   当电压是250V时,能流过继电器电流最大为10A  
15A 125VAC   和上面一样道理，当电压是125v时，能流过继电器的最大电流为15A  
注意(警告):  
  当流过继电器的电流超过规定值时候，会照成元器件过热顺怀以及可能引起火灾等问题
  

### 三、连线方式  

开发板和继电器连接 
 
继电器| 开发板|GPIO
--|--|--
DC+ |3.3v|
DC-	|GND|	
IN	|D3	|12

开发板和微动开关连接 
 
微动开关| 开发板|GPIO  
--|--|--
A端 |GND|
B端	|D7|13

  
注意问题  
   直接循环检测微动开关，按下按键会有很多次的响应.例如下面的例子  
   ```python
   while True:
		if button.value() == 1:
   		print("put down")
   ```
   我们需要判断在一个时钟周期内的前后两个值是否不相等，来判断是否按下按钮或者松开按钮  
   
   演示程序不是完美的，是一个死循环，在正在的环境大家要学会变通。
   