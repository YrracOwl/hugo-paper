---
title: 关于成型滤波器在matlab中的相关实现
slug: rcos_in_matlab
categories:
  - 技术
draft: false
date: 2023-01-30T03:50:36.537Z
authors: YrracOwl
image: nft-car-girl-3iue4ieidjw-unsplash.jpg
tags:
  - 升余弦滤波器
  - matlab
---
<!--StartFragment-->

# 什么是成型滤波器

成型滤波器也即升余弦滤波器，它主要用在数字信号处理领域中，作用是将表现为方波的无限带宽数字信号脉冲(*根据傅立叶变换可知矩形方波的带宽无限宽，因为矩形方波可以由无限个频率存在整数倍倍数关系的sine叠加而成*)进行带限，从而使信号的带宽匹配信道的带宽。

通常在发送端使用根升余弦滤波器进行滤波，在接收端也使用根升余弦滤波器进行滤波，在发送端->信道->接收端这一条通路上，便存在一个升余弦滤波器，因此实现了针对信号的带限。

# matlab中的实现

## 升余弦滤波器

在matlab中使用`rcosdesign(beta,span,sps,shape)`来实现升余弦滤波器，接下来就此函数中的参数进行说明。

* beta：滚降系数，通常取值为在0到1之间
* span：由于实际的升余弦滤波器的拖尾无限长，就像水面的波纹一样，在无限远处幅度为0，所以截取一定的长度，span表示模拟的拖尾能够影响的未经采样原始的数据点数
* sps：每个原始的数据点数的采样点数
* shape：可选参数，默认为根升余弦滤波器，当其为normal时就是升余弦滤波器

如下举个例子：

```matlab
h = rcosdesign(0.25,6,4);
fvtool(h,'Analysis','impulse') % 此行是显示滤波器h的脉冲响应
```

得到的结果如下所示：

![](https://raw.githubusercontent.com/YrracOwl/tiddlywiki/main/tiddlers/%E6%88%90%E5%9E%8B%E6%BB%A4%E6%B3%A2%E5%99%A8-demo1.png)

## 上采样与下采样

上采样表示为内插，即插值；下采样就是通常意义上描述的采样，间隔一定的周期进行采样。

在matlab中使用函数`upfirdn(data,fir,p,q)`来实现，就其中的参数进行说明如下。

* data：原始数据
* fir：滤波器
* p：上采样
* q：下采样，不使用下采样可以不写，或者写为1

> 也可以这么理解，upfirdn(xn,hn,length) 作用为把xn中的每个值乘以序列hn，然后移位相加，length表示了移位的长度。其中xn、hn的点数分别为N1、N2，输出点数为 N2+(N1-1)×length。

给出示例如下所示。

```matlab
h = rcosdesign(0.25, 4, 40);
data = 2*randi([0 1], 30, 1) - 1;
figure;
stairs(data)
ylim([-2 2]);grid on;
x = upfirdn(data, h, 40); % 注意：因为滤波器中的sps是4，因此这里的上采样p也为4
figure;
stem(x)
ylim([-0.4 0.4]);grid on;
```

> 其中:
>
> \* figure为新建一个图像
>
> \* stairs是将数据data进行台阶化显示，以与滤波后的做对比
>
> \* ylim是将数据在图像上的显示的范围进行手动指定
>
> \* stem就是绘制离散点的图像，若要绘制连续图像，可以使用plot

其结果显示为：

![](https://raw.githubusercontent.com/YrracOwl/tiddlywiki/main/tiddlers/%E6%88%90%E5%9E%8B%E6%BB%A4%E6%B3%A2%E5%99%A8-demo3.png)

data的值为左图，滤波之后的图为右图，可以观察到**矩形方波被带限了**。

# 未完待续

<!--EndFragment-->

<!--StartFragment-->

# Reference

[参考1](https://blog.csdn.net/lanluyug/article/details/80401943) [参考2](https://blog.csdn.net/weixin_44884357/article/details/89488374)

<!--EndFragment-->