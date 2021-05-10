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
![image](https://github.com/tiancai134007/Pytorch-/blob/main/image/methods.png)
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
<br>1、constant：像素值由fill设定
<br>2、edge：像素值由图像边缘像素决定
<br>3、reflect：镜像填充，最后一个像素不镜像，例如:[1,2,3,4] -> [3,2,1,2,3,4,3,2]
<br>4、symmetric: 镜像填充，最后一个像素镜像，例如：[1,2,3,4] -> [2,1,1,2,3,4,4,3]
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

# FiveCrop与TenCrop
功能：在图像的上下左右以及中心裁剪出尺寸为size的5张图片，TenCrop对这5张图片进行水平或者垂直镜像获取10张图片
* size：所需裁剪图片尺寸
* vertical_flip：是否垂直翻转

# 翻转 RandomHorizontalFlip与RandomVerticalFlip
功能：依概率水平或者垂直翻转图片
* p：翻转概率

# 旋转 RandomRotation
功能：随机旋转图片
* degrees：旋转角度
<br>当为a时，在（-a,a）之间选择旋转角度
<br>当为（a,b）时，在（a,b）之间选择旋转角度
* resample：重采样方法
* expand：是否扩大图片，以保持原图信息（旋转后部分角的信息可能丢失 ）
* center：旋转点设置，默认中心旋转

# Pad
功能：对图片边缘进行填充
* padding：设置填充大小
当为a时，上下左右均填充a个像素
当为（a,b）时，上下填充b个像素，左右填充a个像素
当为（a,b,c,d）时，左，上，右，下分别填充a,b,c,d
* padding_mode:填充模式，有4种模式，constant、edge、reflect和symmetric
* fill：constant时，设置填充的像素值，（R,G,B）or (Gray)

# ColorJitter
功能：调整亮度、对比度、饱和度和色相
* brightness：亮度调整因子
<br>当为a时，从[max(0,1-a),1+a]中随机选择
<br>当为（a,b）时，从[a,b]中随机选择
* contrast: 对比度参数，同brightness
* saturation：饱和度参数，同brightness
* hue：色相参数，当为a时，从[-a,a]中选择参数，注：0<= a <= 0.5
<br>当为（a，b）时，从[a,b]中选择参数，注：-0.5 <= a <= b <= 0.5

# Grayscale(当RandomGrayscale的概率为1时的特例)与RandomGrayscale
功能：依概率将图片转换为灰度图
* num_output_channels: 输出通道数，只能设1或3
* p：概率值，图像被转换为灰度图的概率

# RandomAffine
功能：对图像进行仿射变换，仿射变换是二维的线性变换，由五种基本院子变换构成，分别是旋转、平移、缩放、错切和翻转
* degrees：旋转角度设置
* translate：平移区间设置，如（a,b）,a设置宽（width）,b设置高（height）
图像在宽维度平移的区间为 -img_width * a < dx < img_width * a
* scale: 缩放比例（以面积为单位）
* fill_color: 填充颜色设置 
* shear: 错切角度设置，有水平错切和垂直错切
<br>若为a,则仅在x轴错切，错切角度在（-a,a）之间
<br>若为（a,b）,则a设置x轴角度，b设置y的角度
<br>若为（a,b,c,d)，则a,b设置x轴角度，c，d设置y轴角度
* resample: 重采样方式，有NEAREST、BILINEAR、BICUBIC

# RandomErasing
功能：对图像进行随机遮挡
* p：概率值，执行该操作的概率
* scale：遮挡区域的面积
* ratio：遮挡区域长宽比
* value：设置遮挡区域的像素值，（R,G,B）or （Gray）

# Lambda
功能：用户自定义lambda方法
* lambd：lambda匿名函数

# transforms.RandomChoice
功能：从一系列transforms方法中随机挑选一个

# transforms.RandomApply
功能：依据概率执行一组transforms操作

# transforms.RandomOrder
功能：对一组transforms操作打乱顺序

# 自定义transforms要素:
1.仅接收一个参数，返回一个参数
<br>2.注意上下游的输出与输入
##### 结构
    class YourTransforms(object):
      def __init__(self,...):
        ...
      def __call__(self,img):
        ...
        return img

# 数据增强的原则
原则：让训练集与测试集更接近




