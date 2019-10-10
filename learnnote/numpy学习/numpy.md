###np.random.choice(a,size=NONE,replace=False,p=NONE)
表示从a中随机选取size个数,replacement 代表的意思是抽样之后还放不放回去，如果是False的话，那么通一次挑选出来的数都不一样，如果是True的话， 有可能会出现重复的，因为前面的抽的放回去了。p表示每个元素被抽取的概率，如果没有指定，a中所有元素被选取的概率是相等的。

###np.vstack()和np.hstack()
np.vstack():在竖直方向上堆叠
np.hstack():在水平方向上平铺
```
arr1=np.array([1,2,3])
arr2=np.array([4,5,6])
print np.vstack((arr1,arr2))
print np.hstack((arr1,arr2))
```
```
[[1 2 3]
 [4 5 6]]
[1 2 3 4 5 6]
```

###numpy.flatnonzero():
返回扁平化的矩阵的非零元素的位置（index）
```
1 >>> x = np.arange(-2, 3)
2 >>> x
3 array([-2, -1,  0,  1,  2])
4 >>> np.flatnonzero(x)
5 array([0, 1, 3, 4])
import numpy as np
d = np.array([1,2,3,4,4,3,5,3,6])
haa = np.flatnonzero(d == 3)
print (haa)

[2 5 7]
```

###np.random.seed(num)
参数num是0会使随机数可预测。即当参数相同时使得每次生成的随机数相同；当参数不同或者无参数时，作用与numpy.random.rand()函数相同，**即利用随机数种子，每次生成的随机数相同**
```
>>> numpy.random.seed(0) ; numpy.random.rand(4)
array([ 0.55,  0.72,  0.6 ,  0.54])
>>> numpy.random.seed(0) ; numpy.random.rand(4)
array([ 0.55,  0.72,  0.6 ,  0.54])
```
种子重置(每次)，每次都会出现相同的数字组。 如果未重置随机种子，则每次调用都会显示不同的数字：
```
>>> numpy.random.rand(4)
array([ 0.42,  0.65,  0.44,  0.89])
>>> numpy.random.rand(4)
array([ 0.96,  0.38,  0.79,  0.53])

```

###Numpy.random中shuffle与permutation的区别
两者都是对原来数组进行重排列，区别是shuffle是在原数组上直接操作，无返回值，而permutation则生成一个重新打乱的数组，并不改变原数组


###np.power(x1,x2)
求x1的x2次幂，x2可以是数字可以是数组，数组的话就是x2中的值是x1对应元素的幂次

###numpy中的ravel()、flatten()、squeeze()的用法与区别
numpy中的ravel()、flatten()、squeeze()都有将多维数组转换为一维数组的功能，区别： 
ravel()：如果没有必要，不会产生源数据的副本 
flatten()：返回源数据的副本 
squeeze()：只能对维数为1的维度降维
另外，reshape(-1)也可以“拉平”多维数组
![](https://raw.githubusercontent.com/nanfengchuiyeluo6/images/master/squeeze%EF%BC%88%EF%BC%89.png)

###np.dot()
1. 如果处理的是一维数组，则得到的是两数组的內积
2. 如果是二维数组（矩阵）之间的运算，则得到的是矩阵积（mastrix product）。
![](https://raw.githubusercontent.com/nanfengchuiyeluo6/images/master/%E7%9F%A9%E9%98%B5%E7%A7%AF.png)

###np.concatenate((a1, a2, ...), axis=0)
a1, a2, ... : 需要拼接的矩阵
axis : 沿着某个轴拼接，默认为列方向

###np.bincount(x, weights=None, minlength=0)
例子：
```
x = np.array([0,1,1,3,2,1,7])
np.bincount(x)
输出结果是：array([1,3,1,1,0,0,0,1])
```
第一个是看0在x中出现几次，1次；
1出现几次，3次；
2出现几次，1次；
3出现几次，1次；
4出现几次，0次；
5出现几次，0次；
6出现几次，0次；
7出现几次，1次

###numpy.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None, axis=0)[source]
返回一个固定间隔的数字空间，如linespace（1，15，15）意思是在1到15之间产生15个数，间隔为1
