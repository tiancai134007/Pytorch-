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
