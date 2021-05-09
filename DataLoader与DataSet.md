## DataLoader
功能：构建可迭代的数据装载器
* dataset：Dataset类，决定数据从哪里读取以及如何读取
* batchsize：批大小
* num_works: 是否多进程读取数据
* shuffle：每个epoch是否乱序
* drop_last:当样本数不能被batchsize整除时，是否舍弃最后一批数据

## Epoch、Iteration与Batchsize的关系与区别
* Epoch：所有训练样本都已输入到模型中，称为一个Epoch
* Iteration：一批样本输入到模型中，称之为一个Iteration
* Batchsize：批大小，决定一个Epoch有多少个Iteration   <br>
样本总数：80，Batchsize：8  <br>
1 Epoch = 10 Iteration

## Dataset
功能：Dataset是抽象类，所有自定义的Dataset需要继承它，并且复写__getitem__()
getitem：接收一个索引，返回一个样本
