### Hook函数机制：不改变主体，实现额外功能，像一个挂件，挂钩，hook
#### Tensor.register_hook
功能：注册一个反向传播hook函数
Hook函数仅一个输入参数，为张量的梯度

####  主要代码：
    b = torch.ass(w,x)
    a_gard = list()
    def grad_hook(grad):
      a_gard.append(grad)
    handle = a.register_hook(gead_hook)
 
#### Module.register_forward_hook
功能：注册module的前向传播hook函数
* module：当前网络层
* input：当前网络层输入数据
* output：当前网络层输出数据

####  主要代码：
    b = torch.ass(w,x)
    a_gard = list()
    def grad_hook(grad):
      a_gard.append(grad)
    handle = a.register_hook(gead_hook)
    
#### Module.register_forward_pre_hook
功能：注册module前向传播前的hook函数
参数：
* module：当前网络层
* input：当前网络层输入数据

#### Module.register_backward_hook
功能：注册module反向传播前的hook函数
参数：
* module：当前网络层
* grad_input：当前网络层输入梯度数据
* gard_output：当前网络层输出梯度数据

### Grad—CAM（类激活图）
