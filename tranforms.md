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

# transforms.CenterCrop
功能：从图像中心裁剪图片
* size：所需裁剪图片尺寸

# transforms.RandomCrop
功能：从图像中随机裁剪出尺寸为size的图片
* size：所需裁剪图片尺寸
* padding：设置填充大小   <br>
当为a时，上下左右均填充a个像素   <br>
当为（a,b）时，上下填充b个像素，左右填充a个像素   
当为（a,b,c,d）时,左,上,右,下分别填充a,b,c,d    
* pad_if_need:若图像小于设定size，则填充
* padding_mode: 填充模式，有4种模式
1、constant：像素值由fill设定
2、edge：像素值由图像边缘像素决定
3、reflect：镜像填充，最后一个像素不镜像，例如:[1,2,3,4] -> [3,2,1,2,3,4,3,2]
4、symmetric: 镜像填充，最后一个像素镜像，例如：[1,2,3,4] -> [2,1,1,2,3,4,4,3]
* fill:为constant时，设置填充的像素值 

# RandomResizedCrop
功能：随机大小、长度比裁剪图片
* size：所需裁剪图片尺寸
* scale：随机裁剪面积比例，默认（0.08,1）
* ratio：随机长宽比，默认（3/4,4/3）
* interpolation:插值方法
PIL.Image.NEAREST
PIL.Image.BILINEAR
PIL.Image.BICUBIC