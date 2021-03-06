关于上采样方法总结（插值和深度学习）

一、简介

      上采样的技术是图像进行超分辨率的必要步骤，最近看到了CVPR2019有一些关于上采样的文章，所以想着把上采样的方法做一个简单的总结。
看了一些文章后，发现上采样大致被总结成了三个类别：
1、基于线性插值的上采样
2、基于深度学习的上采样（转置卷积）
3、Unpooling的方法
其实第三种只是做各种简单的补零或者扩充操作，下文将不对其进行涉及。

为了方便大家阅读，做了个小的目录，接下来的文章介绍主要分为以下内容：
线性插值
1、最近邻算法    
2、双线性插值算法    
3、双三次插值算法（bicubic    

深入学习
1、转置卷积    
2、PixelShuffle（亚像素卷积，CVPR2016）    
3、DUpsampling（亚像素卷积，CVPR2019）    
4、Meta-Upscale（任意尺度缩放，CVPR2019）    
5、CAPAFE（内容关注与核重组，思路新颖，ICCV2019）    
二、线性插值

      线性插值用的比较多的主要有三种：最近邻插值算法、双线性插值、双三次插值（BiCubic），当然还有各种其改进型。在如今SR中这些方法仍然广泛应用。这些方法各有优劣和劣势，主要在于处理效果和计算量的差别。
      计算效果：最近邻插值算法 < 双线性插值 < 双三次插值
      计算速度：最近邻插值算法 > 双线性插值 > 双三次插值
       在接下来我会将测试这些算法的效果和运行速度。

1、最近邻插值算法

      最近邻插值算法是最简单的一种插值算法，当图片放大时，缺少的像素通过直接使用与之最近原有颜色生成，也就是说照搬旁边的像素这样做结果产生了明显可见的锯齿。在待求像素的四邻像素中，将距离待求像素最近的邻灰度赋给待求像素。




轻量级通用上采样算子

    Large receptive field
    Content-aware
    Lightweight


### reference
[Decoders Matter for Semantic Segmentation:
Data-Dependent Decoding Enables Flexible Feature Aggregation](http://arxiv.org/pdf/1903.02120v2.pdf)    
[Location-aware Upsampling for Semantic Segmentation](https://arxiv.org/abs/1911.05250)    
[CARAFE: Content-Aware ReAssembly of FEatures](https://arxiv.org/abs/1905.02188)    
[CSDN](https://blog.csdn.net/qq_34919792/article/details/102697817)