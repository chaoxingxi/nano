# 讲在前面

>*吃不上猪肉，那就看猪跑!*

## 阻塞项

1. SDKM刷机失败，需尝试Ubuntu 18.04的SDKM
尝试过方案
Ubuntu 20.04 实体HOST和虚拟机都尝试了，也尝试了 https://forums.developer.nvidia.com/t/sdk-manager-fails-to-flash-orin-nx-8gb-nvme-on-orin-nano-developer-kit/256681/5
>*sudo -s*
>*echo -1 > /sys/module/usbcore/parameters/autosuspend*
都不行，似乎只能
https://forums.developer.nvidia.com/t/unable-to-flash-my-jetson-orin-nano-som-from-ubuntu-20-04-pc/253923

还是不行，只能先用TF卡，直接刷images


## 项目概述

基于Jetson Orin Nano的车载感知模块仿真项目。

一、 基于ROS2，先跑通视频流到最终推理的链路。

1. 相机驱动，罗技USB相机驱动，转发成ros topic

2. 推理加后处理节点（包括推理+跟踪，可先不做跟踪，将推理结果透传出来）

3. 可视化另做

二、nano台架部署BEVFusion

1. 部署BEVFusion demo

2. 用开源数据集生成rosbag用于仿真

3. 播包方式跑通推理

4. 完善后处理

5. nano作为台架，无真实传感器，跑通前融合台架仿真

三、 感知模块

1. 前融合（视为单传感器）

2. 单传感器感知模块

3. 多传感器融合模块

## 项目依赖

1. 跨平台构建Docker镜像 X86 arm

    [跑通在x86上编译的二进制程序，拷贝到orin上直接可运行](https://cloud.tencent.com/developer/article/1543689)


2. 使用service启动程序 待定

3. 是否需要多仓管理repo 待定

4. rosbag数据包db3生成

    因为没有实车，只能将数据集再制作成rosbag数据包
    找一个开源的多传感器融合的数据集
    需要来自驱动的原始数据，视频是否需要解码待定

## 项目主体

构建一套车载多传感器感知的方案

BEV前融合+后融合的方案

## 工具

1. rviz、webrviz可视化
