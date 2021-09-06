# Squeeze-and-Excitation Network

---

**URL:** https://arxiv.org/abs/1709.01507

**Code:** https://github.com/hujie-frank/SENet
**Jnl/Conf:** CVPR 2018

**Rate:** ★★★★

---

## 论文简介

文章提出SENet，并希望引入SE block来建立不同通道之间的依赖关系来增强网络的表示能力，
通过一个自适应校准机制，利用全局信息来选择性的强调有益信息而抑制相对无用的信息。

## 方法
![1](../images/ymli/GPS-net.png)
1 通过一个卷积操作（Ftr）实现 X->U 的转换，卷积核定义为V=[v_1, $v_2$, $v_3$,...$v_C$], C表示
通道数， 最后输出U=['$u_1$, $u_2$, $u_3$,...$u_C$'], 第C个通道输出$u_C$ 计算公式如下：
![](http://latex.codecogs.com/gif.latex?\\sum_{s=1}^{C'} v_{c}^{s} * X^{s})

## 创新点总结

1.提出了用于message passing的DMP模块，通过节点的上下文信息来增强节点特征

2.提出使用NPS损失建模不同节点之间优先级的差异

3.一种新的处理长尾分布的方法ARM
