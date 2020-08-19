# OmniCopter Project
## 项目简介
本项目为对ETHZ全向无人机项目的复现
> D. Brescianini and R. D'Andrea, "Design, modeling and control of an omni-directional aerial vehicle," 2016 IEEE International Conference on Robotics and Automation (ICRA), Stockholm, 2016, pp. 3261-3266.

本项目采用Arduino Mega2560单片机和JY901惯导模块实现姿态与位置控制。

![输入图片说明](https://images.gitee.com/uploads/images/2020/0321/172527_0fb2de19_5675321.png "屏幕截图.png")

飞行视频见[https://www.yuque.com/xtdrone/other_research/omnicopter](https://www.yuque.com/xtdrone/other_research/omnicopter)

## 项目索引
>### 应用层(APP)
 * OmniCopter.ino 项目应用主文件，利用API构件飞控应用

>### 事务处理层(TPS)
 * OmniCopter.h负责正确初始化和处理各种组件，完成飞控功能模块的处理事务，提供API接口给应用
 * Log.h 作为调试辅助类，输出各种调试参数，可以统一全部关闭输出，设置输出频率等。
 * FailSafe.h 安全机制，提供一个阻塞函数，检测是否失控以及遥控通道7是否解锁
 
>### 数据处理层(DPS)
 * Input.h 遥控器接收机信号输入，保存输入的控制指令  
 * Output.h 电调驱动，解析八个螺旋桨指令并输出PWM波  
 * Sensor.h 初始化并驱动JY901模块读取姿态数据，转换数据格式 
  * JY901.h JY901惯导平台驱动   
 * Controller.h 飞控核心算法部分，包括AttitudeController，BodyRateController，PositionController和ControlAllocator

>### 配置以及数学扩展库
* Config.h   保存飞控各种状态参数  
* MathExtend.h  拓展数学结构体，包括四元数相关运算，姿态角和姿态角速度等
