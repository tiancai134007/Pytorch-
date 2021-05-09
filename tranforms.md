# transforms常用的图像预处理方法
* 数据中心化
* 数据标准化
* 缩放
* 裁剪
* 旋转
* 翻转
* 填充
* 噪声添加
* 灰度变换
* 线性变换
* 仿射变换
* 亮度、饱和度及对比度变换

# normalize
功能：逐channel的对图像进行标准化
output = （input- mean）/ std
* mean: 各通道的均值
* std：各通道的标准差
* inplace：是否原地操作
