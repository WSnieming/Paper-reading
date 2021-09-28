# Squeeze-and-Excitation Networks

---

**URL:** https://arxiv.org/abs/1709.01507

**Code:** https://github.com/hujie-frank/SENet

**Jnl/Conf:** CVPR 2018

**Rate:** ★★★★

---

## 论文简介

文章提出SENet，并希望引入SE block来建立不同通道之间的依赖关系来增强网络的表示能力，
通过一个自适应校准机制，利用全局信息来选择性的强调有益信息而抑制相对无用的信息。最终
以较小的计算量增加为代价得到了较大的网络性能提升。

## 方法
![1](../images/mnie/20210906.1.png)

1 通过一个卷积操作（Ftr）实现 X->U 的转换，卷积核定义为<img src="https://latex.codecogs.com/svg.image?V&space;=&space;[v_{1},&space;v_{2},&space;v_{3},...,v_{c}]" title="V = [v_{1}, v_{2}, v_{3},...,v_{c}]" />, C表示通道数， 最后输出<img src="https://latex.codecogs.com/svg.image?U&space;=&space;[u_{1},&space;u_{2},&space;u_{3},...,u_{c}]" title="U = [u_{1}, u_{2}, u_{3},...,u_{c}]" />, 第C个通道输出计算公式如下：

<img src="https://latex.codecogs.com/svg.image?u_{c}&space;=&space;v_{c}&space;&space;*&space;X&space;=&space;\sum_{s=1}^{C'}&space;v_{c}^{s}&space;*&space;X^{s}" title="u_{c} = v_{c} * X = \sum_{s=1}^{C'} v_{c}^{s} * X^{s}" />

2 全局池化操作。由于每个filter只能利用局部信息，U中的每个单元也就无法利用此区域外
的上下文信息，为了能使其具有全局感受野，用全局平均池化将全局空间信息压缩为一个实数，
其中<img src="https://latex.codecogs.com/svg.image?z_{c}\in\mathbb{R}^{C}" title="z_{c}\in\mathbb{R}^{C}" />，对于z的第c个元素，计算公式如下：

<img src="https://latex.codecogs.com/svg.image?z_{c}&space;=&space;F_{sq}(u_{c})&space;=&space;\frac{1}{H&space;*&space;W}\sum_{i=1}^{H}\sum_{j=1}^{W}u_{c}\left&space;(&space;i,&space;j&space;\right&space;)" title="z_{c} = F_{sq}(u_{c}) = \frac{1}{H * W}\sum_{i=1}^{H}\sum_{j=1}^{W}u_{c}\left ( i, j \right )" />


3 自适应重新校准。 使用一个两层的非线性全连接网络，公式如下：

<img src="https://latex.codecogs.com/svg.image?s&space;=&space;F_{ex}(z,&space;W)&space;=&space;\sigma&space;(g(z,&space;W))&space;=&space;\sigma&space;(W_{2}\delta&space;(W_{1}z))" title="s = F_{ex}(z, W) = \sigma (g(z, W)) = \sigma (W_{2}\delta (W_{1}z))" />

![1](../images/mnie/20210906.2.png)

4 将学习到的z（即每个通道的权重）与对应通道做乘法（相当于对U进行了放缩）。

<img src="https://latex.codecogs.com/svg.image?\widetilde{x_c}&space;=&space;F_{Scale}(u_c,&space;s_c)&space;=&space;s_c&space;u_c" title="\widetilde{x_c} = F_{Scale}(u_c, s_c) = s_c u_c" />

## 创新点总结和思路借鉴

提出了SE block，利用全局信息显示建立通道间的依赖关系, 创新性的将注意力机制应用于CV领域，通过实验中验证，将SE块嵌入到目前已有的模型中，网络性能得到明显提升。
对于自适应重新校准各个特征通道权重中使用的两层全连接神经网络，也可以尝试使用其它结构的网络来实现。
