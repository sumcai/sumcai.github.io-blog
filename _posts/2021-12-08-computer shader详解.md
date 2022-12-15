---
title: computer shader详解
layout: post
categories: 
  - Vulkan技术
tags: 
  - computer shader
date: 2021-12-08 07:39:25
permalink: /vulkan/compshader/
---

# computer shader详解

## 使用方式

- 代码侧调度计算管线任务

  `vkCmdDIspatch(commandBuffer, groupSize.x, groupSize.y, groupSize.z)`

  `groupSize`代表工作组数量(xyz三个方向上)

- shader侧配置设置

  `layout(local_size_x=6, local_size_y=4) in;`

  设置本地工作组大小，`local_size_z`未设置取默认值1



## WorkGroup参数说明

![1638971538231](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/863e1f0932c954536068441fbcf0534f.png)

以上图为例

- 全局工作组， groupSize.x =3 , groupSize.y=4, groupSize.z=8

- `gl_NumWorkGroups` ：(3，4，8)，全局工作组大小。

- `gl_WorkGroupSize` ：(6，4，1)，本地工作组大小。

- `gl_WorkGroupID` ：（2，2，4），本地工作组在全局工作组中的位置。

- `gl_LocalInvocationID` ：（5，3，0），计算单元在本地工作组的位置。

- `gl_GlobalInvocationID` ：（17，11，4），计算单元在全局工作自的位置，gl_WorkGroupID * gl_WorkGroupSize + gl_LocalInvocationID

- `gl_LocalInvocationIndex` ：23，计算单元在本地工作组的索引，gl_LocalInvocationID.z * gl_WorkGroupSize.x * gl_WorkGroupSize.y + gl_LocalInvocationID.y * gl_WorkGroupSize.x +gl_LocalInvocationID.x;

  


## Subgroup参数说明

![1638972921886](https://objectstorage.ap-osaka-1.oraclecloud.com/n/ax0kqy8quzyr/b/bucket-blog/o/2022/04/c349681166b76d3a822788989b02ac22.png)

如果一个本地工作组分成如上图所示的subgroup，则有如下参数

-  `gl_NumSubgroups`  ：8，本地工作组内的子组数
-  `gl_SubgroupID`  ：[0，7]，本地工作组内子组的ID，范围[0，gl_NumSubgroups)
-  `gl_SubgroupSize`  ：32，子组的容量大小
-  `gl_SubgroupInvocationID`  ：[0，31]，子组内计算单元的ID，范围[0，gl_SubgroupSize)

  