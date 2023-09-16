使用[[卷积神经网络CNN|卷积神经网络]]进行训练，4层卷积层，第二四卷积层添加池化层，最后3个连接层
# 1. 代码的文件结构
![[MINIST手写识别文件结构.png]]
# 2. 运行代码
~~~python
import torch  
from torch import nn  
import torchvision  
# 提供了对图片数据处理相关的api和数据  
from torch.utils.data import DataLoader  
from torch.autograd import Variable  
import time  
  
data_tf = torchvision.transforms.Compose([torchvision.transforms.ToTensor(),torchvision.transforms.Normalize([0.5],[0.5])])  
# ToTensor()将图像转换为张量  
# Normalize()正则化方法，将数据缩放到相同的范围内  
  
train_set = torchvision.datasets.MNIST('./data', train=True, transform=data_tf, download=True)  
test_set = torchvision.datasets.MNIST('./data', train=False, transform=data_tf, download=True)  
# 创建MNIST数据集的实例 train_set,train等于Ture表示训练集False表示测试集  
train_data = DataLoader(train_set, batch_size=64, shuffle=True)  
test_data = DataLoader(test_set, batch_size=128, shuffle=False)  
# 创建训练集 train_data 和测试集 test_data# batch_size设置一次加载的数据量大小，shuffle是否打乱数据集  
  
class CNN(nn.Module):  
def __init__(self):  
super(CNN,self).__init__()  
# 用4个卷积层  
self.layer1 = nn.Sequential(  
nn.Conv2d(1,16,kernel_size=3), #输出大小 16, 26 ,26 特征图数量16，尺寸26 卷积核大小3*3  
nn.BatchNorm2d(16),  
nn.ReLU(inplace=True))  
  
self.layer2 = nn.Sequential(  
nn.Conv2d(16,32,kernel_size=3),#输出大小 32, 24, 24 特征图数量32，尺寸24  
nn.BatchNorm2d(32),  
nn.ReLU(inplace=True),  
nn.MaxPool2d(kernel_size=2,stride=2)) #最大池化层减少特征图的尺寸 32, 12,12 尺寸(24-2) /2 +1=12  
  
self.layer3 = nn.Sequential(  
nn.Conv2d(32,64,kernel_size=3), # 64,10,10  
nn.BatchNorm2d(64),  
nn.ReLU(inplace=True))  
  
self.layer4 = nn.Sequential(  
nn.Conv2d(64,128,kernel_size=3), # 128,8,8  
nn.BatchNorm2d(128),  
nn.ReLU(inplace=True),  
nn.MaxPool2d(kernel_size=2,stride=2)) # 128, 4,4 卷积核的大小为2  
  
self.fc = nn.Sequential(  
nn.Linear(128 * 4 * 4,1024),  
nn.ReLU(inplace=True),  
nn.Linear(1024,128),  
nn.ReLU(inplace=True),  
nn.Linear(128,10)) #3个全连接层最终将输入的张量映射到10个类别的概率 这层也是输出层  
  
def forward(self,x):  
x = self.layer1(x)  
x = self.layer2(x)  
x = self.layer3(x)  
x = self.layer4(x)  
x = x.view(x.size(0),-1)  
x = self.fc(x)  
  
return x  
  
#网络参数数量  
def get_parameter_number(net):  
total_num = sum(p.numel() for p in net.parameters())  
trainable_num = sum(p.numel() for p in net.parameters() if p.requires_grad)  
return {'Total': total_num, 'Trainable': trainable_num}  
#选择网络  
net = CNN()  
print(net)  
use_gpu = torch.cuda.is_available()  
print(get_parameter_number(net))#设置损失函数  
criterion = nn.CrossEntropyLoss()#设置网络优化方式  
learingrate = 0.01  
optimizer = torch.optim.SGD(net.parameters(), lr=learingrate) #学习率0.1 0.01  
  
if(use_gpu):  
net = net.cuda()  
criterion = criterion.cuda()  
losses = []  
acces = []  
eval_losses = []  
eval_acces = []  
trainloss = []  
start = time.time()  
#开始训练  
for e in range(20):  
train_loss = 0  
train_acc = 0  
net.train()  
for im, label in train_data:  
if (use_gpu):  
im, label = im.cuda(),label.cuda()  
im = Variable(im)  
label = Variable(label)# 前向传播  
out = net(im)  
loss = criterion(out, label)# 反向传播  
optimizer.zero_grad()  
loss.backward()  
optimizer.step()# 记录误差  
train_loss += loss.item()# 计算分类的准确率  
_, pred = out.max(1)  
num_correct = (pred == label).sum().item()  
acc = num_correct / im.shape[0]  
train_acc += acc  
losses.append(train_loss / len(train_data))  
acces.append(train_acc / len(train_data))# 在测试集上检验效果  
eval_loss = 0  
eval_acc = 0  
net.eval() # 将模型改为预测模式  
for im, label in test_data:  
if (use_gpu):  
im, label = im.cuda(),label.cuda()  
im = Variable(im)  
label = Variable(label)  
out = net(im)  
loss = criterion(out, label)# 记录误差  
eval_loss += loss.item()# 记录准确率  
_, pred = out.max(1)  
num_correct = (pred == label).sum().item()  
acc = num_correct / im.shape[0]  
eval_acc += acc  
eval_losses.append(eval_loss / len(test_data))  
eval_acces.append(eval_acc / len(test_data))  
print('***** One epoch has finished ******')  
print('epoch: {}, Train Loss: {:.6f}, Train Acc: {:.6f}, Eval Loss: {:.6f}, Eval Acc: {:.6f}'  
.format(e, train_loss / len(train_data), train_acc / len(train_data),  
eval_loss / len(test_data), eval_acc / len(test_data)))  
trainloss.append(train_loss / len(train_data))  
end = time.time()  
print('The code run{:.2f}s'.format(end - start))  
  
filename = 'epochs.txt'  
with open(filename, 'a') as name:  
name.write('CNN,')  
for i in range(len(trainloss)-1):  
name.write(str(trainloss[i])+',')  
name.write(str(trainloss[-1]) + '\n')  
name.close()
~~~
# 3. 展示代码
~~~python
import torchvision  
from torch.utils.data import DataLoader  
import cv2  
  
data_tf = torchvision.transforms.Compose([torchvision.transforms.ToTensor()])  
  
#准备训练数据  
train_set = torchvision.datasets.MNIST('./data', train=True, transform=data_tf)  
batchSize = 64  
train_data = DataLoader(train_set, batch_size=batchSize, shuffle=True)  
images,labels = next(iter(train_data))  
img = torchvision.utils.make_grid(images)  
# 在装载完成后选取其中一个批次的数据进行预览  
img = img.numpy().transpose(1,2,0)  
print(labels)  
cv2.imshow('images',img)  
key_pressed=cv2.waitKey(0)
~~~