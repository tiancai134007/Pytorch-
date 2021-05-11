# SummaryWriter
功能：提供创建event file的高级接口
主要属性：
* log_dir：event file输出文件夹
* comment：不指定log_dir时，文件夹后缀
* filename_suffix：event file文件名后缀 

# add_scalar()
功能：记录标量
* tag：图像的标签名，图的唯一标识
* scalar_value：要记录的标量
* global_step:x轴

# add_scalars()
main_tag：该图的标签
tag_scalar_dict：key是变量的tag，value是变量的值

# add_histogarm()
功能：统计直方图与多分位数折线图
* tag：图像的标签名，图的唯一标识
* values：要统计的参数
* global_step：y轴
* bins：取直方图的bins

# add_image()
功能：记录图像
* tag：图像的标签名，图的唯一标识
* img_tensor:图像数据，注意尺度
* global_step:x 轴
* dataformats：数据形式，CHW，HWC，HW

# torchvision.utils.make_grid（与add_image结合使用）
功能：制作网格图像
* tensor：图像数据，B*C*H*W形式
* nrow：行数（列数自动计算）
* padding：图像间距（像素单位）
* normalize：是否将图像值标准化
* range：标准化范围
* scale_each：是否单张图维度标准化
* pad_value：padding的像素值
