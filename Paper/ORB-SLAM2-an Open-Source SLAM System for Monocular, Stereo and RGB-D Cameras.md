# ORB-SLAM2-an Open-Source SLAM System for Monocular, Stereo and RGB-D Cameras

## Introduction

单目、双目、深度系统（depth只在初始化过程中使用吗？）

后端基于BA与单目和双目观察允许精确的轨迹估计与度量尺度。我们的系统包括一个轻量级的定位模式，利用视觉里程表跟踪未映射区域，并匹配映射点，允许零漂移定位。

## Methods

![2](https://github.com/GRF-Sunomikp31/ORB_SLAM2_detailed_comments/blob/master/Paper/IMG/2.png)

Local BA：只优化当前帧；



## Experments

为了解释多线程系统的不确定性，我们运行每个序列5次，并显示估计轨迹精度的中值结果。

**Kitti Dataset**：相对误差低于1%；与单目结果相比，我们提出的双目版本能够处理单眼系统失败的序列；双目版本的结果基本上都比LSD-SLAM好；

**EuRoC Dataset**：ORB-SLAM2实现了几厘米的定位精度；

**TUM RGB-D Dataset**：精度高；

时间结果：共可见性图的密度越大，局部地图包含的关键帧和点越多，因此局部地图跟踪和局部BA的开销也越大；

## Conclusion

未来工作：

- 不重叠的多摄像机，鱼眼或全向摄像机支持，大规模密集融合，协作mapping或增强运动模糊的鲁棒性

## 问题

1、重点关注ORB-SLAM2和我ORB-SLAM1的区别以及depth如何使用？

使用双目或RGB-D摄像机的一个主要好处是：通过从仅仅一帧获得深度信息，不需要像在单目情况下一样从运动初始化中获得特定的结构。在系统启动时，我们用**第一帧创建一个关键帧，将其姿态设置为原点**，并从所有的立体关键点创建一个初始地图，

2、绿色点的深度小于立体基线的40倍，而蓝色点的深度更远。

3、关于SLAM系统中，远点和近点使用的问题；
