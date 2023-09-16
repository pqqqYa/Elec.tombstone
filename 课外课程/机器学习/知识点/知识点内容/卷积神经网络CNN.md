全称Convolutional Neural Network
输入层→卷积层→池化层→全连接层→输出层
# 卷积层
利用卷积核，通过二维离散卷积操作，全链接变成局部链接
卷积运算的结果就是特征图`Feature Map`
![[Fearuemap演示.png]]
深度卷积网络就是堆很多层进行计算，逐级下去学到图片的特征
卷积过后要加入激活函数，这里加入的是线性整流单元`Rectified Linear Unit`简称`ReLU函数ReLU（x）`，特征图上的负数都变成0
![[ReLU函数表达式.png]]
简单理解为
$$ReLu(x)=\begin{cases}& x\ \text{ if }\  x> 0 \\& 0\ \text{ if } x\le 0\end{cases}$$
# 池化层Pooling
减低数据维度，减少数据参数，避免过拟合
把局部多个神经元的输出组合成下层单个神经元来减少数据维度“小矩阵里面找最大值或者平均值”，进一步放大主要特征，忽略少数像素点的偏差
* Max Pooling最大池化
* Average Pooling平均池化
基本都是`2*2`的矩阵
![[池化层演示.png]]
# 全连接层
把相邻2层的神经元全部交叉相连