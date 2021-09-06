# GPS-Net Graph Property Sensing Network for Scene Graph Generation

---

**URL:** https://arxiv.org/abs/2003.12962

**Code:** https://github.com/taksau/GPS-Net

**Jnl/Conf:** CVPR 2020 

**Rate:** ★★★☆☆

---

## 论文简介

提出了Graph Property Sensing Network，使用特定于节点的上下文信息来增强节点特征，并通过三线性模型对边的方向信息进行编码。
通过引入节点优先级敏感的损失函数，来区分训练中不同节点对整体场景图的影响。
同时通过软化特征分布，根据每个物体对的视觉特征对其进行调整来缓解长尾分布问题。

## 创新点总结

1.提出了用于message passing的DMP模块，通过节点的上下文信息来增强节点特征

2.提出使用NPS损失建模不同节点之间优先级的差异

3.一种新的处理长尾分布的方法ARM

## 方法
![1](../images/ymli/GPS-net.png)
模型主要分三个部分：
1.DMP模块用于建模边方向相关的上下文信息
2.NPS-Loss:基于节点的优先级对不同节点对整体的贡献进行差异化的处理
3.ARM 基于统计的先验知处理长尾分布带来的bias 

## 思路借鉴

SGG任务中边的方向对结果的影响在之前的工作中常被忽略，这篇文章提出的边方向相关的上下文信息编码方法很有趣。
节点的优先级这一考虑也是很直观的，但我还没看明白这个优先级怎么做出来的，似乎是手动建立的矩阵，如果能够在网络中自然的学习出这种优先级或许会更好
