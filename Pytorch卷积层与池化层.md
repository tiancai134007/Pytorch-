#### 卷积的维度：
一般情况下，卷积核在几个维度上滑动，就是几维卷积
## nn.Conv2d
功能：对多个二维信号进行二维卷积
主要参数：
* in_channels:输入通道数
* out_channels:输出通道数，等价于卷积核个数
* kernel_size:卷积核尺寸
* strile：步长
* padding：填充个数
* dilation：空洞卷积大小
* groups：分组卷积设置
* bias：偏置

#### 尺寸计算公式

#### 转置卷积
转置卷积又称为反卷积和部分跨越卷积，用于对图像进行上采样。参数与正常卷积相同
不均匀重叠可能导致棋盘效应
#### 尺寸计算公式


## nn.MaxPool2d
功能：对二维信号（图像）进行最大值池化
主要参数:
* kernel_size:池化核尺寸
* strile：步长
* padding：填充个数
* dilation：池化核间隔大小
* ceil_mode:尺寸向上取整
* return_indices:记录池化像素索引（应用于最大值反池化）
##### 反池化示意图
![image](https://github.com/tiancai134007/Pytorch-/blob/main/image/反池化.png)

## nn.AvgPool2d
功能：对二维信号（图像）进行平均值池化
主要参数：
* kernel_size:池化核尺寸
* strile：步长
* padding：填充个数
* ceil_mode:尺寸向上取整
* count_include_pad:填充值用于计算
* divisor_override：除法因子

## nn.MaxUnpool2d
功能：对二维信号（图像）进行最大值池化上采样
主要参数：
* kernel_size:池化核尺寸
* strile：步长
* padding：填充个数

## nn.Linear
功能：对一维信号（向量）进行线性组合
主要参数：
* in_features:输入结点数
* out_features:输出结点数
* bias:是否需要偏置
